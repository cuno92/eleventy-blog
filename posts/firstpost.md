---
title: Distributed Transactions
description: MIT 6.824 Lecture 12 - Distributed Transactions
date: 2020-10-31
tags:
  - mit-6.824
  - distributed-systems
layout: layouts/post.njk
---
[![MIT 6.824: Lecture 12 - Distributed Transactions](http://img.youtube.com/vi/aDp99WDIM_4/0.jpg)](http://www.youtube.com/watch?v=aDp99WDIM_4 "MIT 6.824: Lecture 12 - Distributed Transactions")

[6.824 2020 Lecture 12: Distributed Transactions](https://pdos.csail.mit.edu/6.824/notes/l-2pc.txt)

Distributed databases typically divide their tables into partitions spread across different servers which get accessed by many clients. In these databases, client transactions often span the different servers as the transactions may need to read from various partitions. A distributed transaction is a database transaction which spans multiple servers.

A transaction with the correct behaviour must exhibit the following, also known as the ACID properties:

* Atomicity: Either all writes in the transaction succeed or none, even in the presence of failures.

* Consistency: The transaction must obey application-specific invariants.

* Isolation: There must be no interference from concurrently executing transactions. The ideal isolation level is serializable isolation. This guarantees that the result of the execution of concurrent transactions will be the same as if the database executed the transactions one after the order. I've written about serializability more extensively here and here, and I'll recommend reading them if you're interested in learning more about it.

* Durability: Committed writes must be permanent.