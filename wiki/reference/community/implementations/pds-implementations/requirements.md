---
title: What is required to make a PDS implementation?
description: 
published: true
date: 2025-03-31T20:00:47.473Z
tags: pds
editor: markdown
dateCreated: 2025-03-31T20:00:11.627Z
---

# What is required to make a PDS implementation?

See [existing PDS implementations](/wiki/reference/community/implementations/pds-implementations).

This [Github thread from July 2024](https://github.com/bluesky-social/atproto/discussions/2644) had a long answer by Bryan Newbold that is included below:

---

It can be tricky to implement repos! They can be a bit slippery to think about, and it is pretty easy to take some simplifying assumptions and then learn later that your implementation needed some additional feature or complexity.

The very strong analogy is to git repos. git is famously complex as well! And harder when you try to actually implement anything hard with it.

I've laid out three different ways of answering your question and thinking about repos. In analogy to git these would roughly break down like:

* software API: what commands does the git CLI support? those are analogous to the com.atproto.sync.* and com.atproto.repo.* lexicons. what functions and API does a git implementation expose internally, or as a library? eg `libgit2`. these need to enable the public interface, but will usually be implementation-specific. there are likely common patterns and abstractions, but there isn't a formal checklist or anything.

* repo data encoding: this would be like poking around in a .git directory, and figuring out how to format a raw git commit object, or the syntax of git directory objects. and some related encoding, like CAR files; git itself doesn't directly require "diffs" or "patches" in theory, but de-facto every git implementation is going to have some code to output a "universal diff" patch format which other tools can work with. it is very easy to get tangled up in details, acronyms, and unexpected quirky spec details or decisions here.

* data structures: these are the fun cerebral abstractions and concepts. "what makes git special" / "what makes atproto special". you need to understand these to do an implementation and get the details right, but realistically you will probably spend more time on the above details and API design decisions than with the computer-science concepts.

## Repos as a Software API: what functionality do you need to support?

One way to think about atproto repos is as a black-box data container. What software API methods are needed for interacting with this data container?

The basics:

* import and export repos from CAR files. these are a binary storage format, basically with the data blocks concatenated together; details are in the IPLD CAR file specifications. this is helpful in testing, and required to service repo import/export endpoints

* add, update, and delete records from a repo, as a batch, given existing binary records and paths. this is to service the record mutation endpoints.

* ability to "list" the records in a repo, with start/end and limit flexibility, to service the list endpoint

* store repo data somewhere, like a sqlite or postgresql database. there are a bunch of ways to do this; often implementations invent or reuse some generic interface for fetching/storing/etc block data, so they can support multiple storage backends. you should probably always implement an always-in-memory version

* validate an MST tree. there isn't an endpoint for this, and in theory you could just be very careful with all of the import/export and mutation code, but in practice, for development and debugging, you should have a method which does deep re-verification of an MST tree

Not directly related, but needed:

* ability to translate between JSON atproto data (records) and CBOR atproto data (records). usually you want to do this in an app/lexicon-agnostic way

* you need to have the functionality to create a new commit object and sign it with a cryptographic private key, so you need to implement the atproto crypto system (key encoding, signature validation, specific curves, high-S/low-S signatures, etc)

* Lexicon validation, needed for a PDS implementation

More advanced:

* remember some commit history about a repo, so you can generate a "diff" of what changed since some previous commit revision (rev). these are usually serialized as "CAR slices", and are used to output on the PDS event stream, or to service the "get changes since" API endpoint. needed to do a PDS

* parse out blob references from arbitrary records, and maintain a mapping between records and blobs

* keep track of the current commit for each account somewhere

Implementation design decisions:

* potentially the ability to do a series of small updates to an MST in memory, then "commit" the changes. this is like a working directory in git. in theory you could get away with only having a batch-update API which always returns a commit

* ability to work with complete MSTs (you have all the records and intermediate nodes) vs partial MSTs

* when loading an MST from data store, do you pull out all the blocks/nodes at the beginning? or one block at a time? or something more complex?

* when you mutate an MST, do you only load and generate the "new" tree nodes? or re-generate the whole tree and diff which nodes are new and write those to storage? or re-write all nodes to storage?

* need the ability to read from any repo, but usually can only mutate/update if you have the secret part of signing key on hand

Keep in mind that there are repos in the network today with millions of records and gigabytes of data.

## Repo data formats and encoding: nuts and bolts

There is a whole grab-bag of data formats, serializations, and other incidental design details to work through. These are individually mostly simple and boring, but there are a whole bunch of acronyms which may or may not be familiar or come across as idiosyncratic. A lot of these are described in the "Data Model" specs.

I'm not really sure how to help here: there are just a bunch of little details to bulldoze through. A partial list:

* CIDs: basically just content. If you think of something like SHA-1 hashes in git, they are implicitly: the SHA-1 algorithm; a specific output number of bytes (could have been truncated!); binary bytes are encoded in lower-case hex; might refer to final file bytes, or to another "git object" (like a commit or directory node); git has a convention of pre-pending the file size and hashing the file size bytes and then the actual file bytes together. that is a bunch of implicit knowledge you are just expected to know when working with git; you can't guess it just looking at a hash. CIDs are a more general format that tries to support evolution of these details by encoding metadata about the hash in the hash itself, so you can parse the CID and learn that it is SHA-256, represented using base32 vs hex vs base64, etc. atproto uses CIDs in a very restricted way: basically all CIDs are generated with the same hash today, the format flexibility is so we can evolve in the future

* CBOR: CBOR is basically a binary encoding for JSON (though it has some features JSON doesn't, and it isn't always a perfect one-to-one). atproto uses a specific subset/variant of CBOR, and a specific subset/variant of JSON, such that we can deterministically convert records between JSON and CBOR. the terminology for the CBOR variant is "DAG-CBOR" and comes from IPLD, but it is really just some simple rules like "don't use floats" and "always sort the keys in a dict".

* IPLD: this is a commonly confusing technology/abstraction. if you look it up you will get word soup about abstractions. basically it is just JSON/CBOR objects with links between objects. instead of those links being URLs (like they would be in most HTTP JSON APIs on the web), the references between objects are hashes (specifically CIDs). this turns a group of linked objects in to a merkel-tree or merkle-dag.

## MST as an abstract data structure

This is the specific data structure used to turn a collection of records (with paths) in to a tree structure. It is similar to something like a Red-Black Tree: you get the general idea from the abstraction, but the overall concept is parameterized (what hash algorithm to use for hashing? what "prefix length" for counting tree depth?) which need to be specified (and are for atproto), and then a bunch of encoding and data format issues discussed in the section above.

This one is complex and i've already spent a bunch of time writing this doc, so going to cut things a bit short. I hope that the atproto "Repository" spec roughly documents the details. Realistically, it would be most helpful to have some diagrams and worked examples (specific records and paths resulting in specific hashes) to demonstrate all this, but it is a huge amount of work to generate that kind of documentation and we haven't gotten around to it yet.