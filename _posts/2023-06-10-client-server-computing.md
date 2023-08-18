---
layout: post
title: 'Client-Server Computing'
description:
category: articles
tags: [backend-engineering]
comments: true
---

Continuing the previous post for the <a href="/articles/2023/05/07/backend-odyssey">backend engineering series</a>, the previous one was about some basic ideas about designing systems. The next thing to learn, would be the interaction between machines in these systems, so we go with client and server models

<!-- more -->

So basically what we've learned so far is that the web is more like a network of documents and assets linked to one another in a distributed system in the internet.

<center><img src="/photos/2023/client-server-computing-0.jpg"></center>

So two things to ask about this is, how do we publish new content, and how do we fetch them?

There are lots of approaches, but here are the 2 most popular: P2P, and Client-Server

# Peer-to-Peer

Every computer is a peer, in that they both serve and fetch content for the user.

Basically its protocols works like the following (diagrams made through <a href="https://excalidraw.com/">excalidraw</a>- it's awesome!)

<img src="/photos/2023/client-server-computing-1.svg">

If a computer wants to host a new content, it just adds it to its local system. If it wants to request something, like let's say Computer A wants to request a document, it checks its local storage if it has it, then asks its "neighbours" (other computing machines) if they have one. And then these if neighbours dont have it, they check their other neighbours. These messages of request would propagrate across the network until it reaches a computer that has it, in this case in the diagram it's Computer D. At that point, Computer D sends it back directly (if it's a well designed system) to Computer A.

# Client and Server

Unlike the general approach of P2P, client-server is more of a specialized approach

<img src="/photos/2023/client-server-computing-2.svg">

By specialized we mean that clients just talk (mostly through browsers) to the servers, while servers are focused on hosting and publishing content that the clients request. Thus server machines are typically much more powerful machines than clients as they have to respond to multiple clients. In comparison to P2P, where it's more of a general approach where everybody coordinates.

# The Server

Let's look more into what the servers are.

From the word, it's a machine that (provides specializes services) serves. These machines are mostly located in data centers, organized in the cloud, providing clients services (such as content, emails, databases) that they may need usually through a <a href="https://en.wikipedia.org/wiki/Request%E2%80%93response">request/response method</a>. As mentioned earlier, these are much more powerful machines with higher storage and memory, as well as better connection, to deal with multiple requests from users.

Servers typically have a known IP address on the internet. As servers typically provide multiple services, these services in the server have multiple TCP ports. In time, they were given conventions, based on the Internet Assigned Numbers Authority (IANA), standard web services (HTTP) typically live in port :80, SSH servers would be :22, secured transfers (HTTPS) would be :443, etc.

Every server application has its own TCP port to distinguish between multiple services it's running. Like when what if one client requests some document from the server and another client requests to run some command for it on a Virtual Machine (VM) service that the server provides?

Designing server applciations also come with similar challenges that we've mentioned in the first blog post in this series, <a href="/articles/2022/08/10/peek-into-web-development">Peek into Web Development</a>. An example would be consistency, how would we coordinate between multiple servers providing redundant services? Concurrency is another challenge, obviously given that servers would tend to get concurrent requests more. Managing state too, like should we allocate for every client session or keep state at minimum?

Speaking of state, on the next part of this series, we'll look into HTTP in depth and how it handles state, as well as a bit of a taste of Java programming. This then sets us nicely into the next subseries of this backend engineering odyssey, which is diving into concurrency, which could be about 3-4 blog posts long. It's important to look into concurrency in the server side, before we look into discussing modern web development and web frameworks that exist today.
