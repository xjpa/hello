---
layout: post
title: 'Peek into Web Development'
description:
category: articles
tags: [backend-engineering]
comments: true
---

Let's get this <a href="/articles/2023/05/07/backend-odyssey">backend odyssey</a> started.

<!-- more -->

We start with the internet.

# The Internet

From a software development perspective, the internet is comprised of these layers

1. Application: at the top, the app layer, of which a web application like google or facebook is built out of various services.

2. Middleware: web services that allow us to build applcations that do stuff between machines, cloud services like GCP and AWS, and more

3. Session: protocols such as HTTP, P2P/peer to peer, SSH, FTP, and more are in this layer like the LSP/lightweight streaming protocol, which sits atop/relies on the UDP. What's a protocol? Let's just say it's a specification for messages that would allow entities (computers) to communicate and exchange stuff (over the web)

4. Transport: more abstractions over IP layer, examples of protocols in this layer include TCP and UDP

5. IP: this layer contains protocols that sends packets/bits of data from one endpoint to another, or packet forwarding. Examples of protocols include the IPv4/IPv6 internet procols

6. Link: the lowest layer in the internet protocol suite/TCP. Contains protocols for things like WIFI and Ethernet.

Typically, web and even backend development work is focused on those above the transport layer.

# OSI Model

Another worth a look similar to the above is the OSI model, which is the one typically shown on computer networking textbooks. The following is a screenshot of the OSI model taken from wikipedia:

<img src="/photos/2022/osi.png">

The presence of such layers allow us to have abstractions towards the lower layers, while having interfaces to each other. Because of this, we can replace technologies in one layer (like in data link layer, it could be changing from Wi-Fi to 3G internet connection) and depending on how the application is built, the application would still continue to run, thanks to modularising things and having interfaces.

# What happens when one types something like facebook.com into the browser?

As we've seen, the web is built upon layers. And this segues us nicely to a popular interview question

> what happens when you type something into the browser?

A very in-depth answer to that can be found on this [github repo](https://github.com/alex/what-happens-when) (archived link [here](https://archive.is/FA5Ml)). I mentioned that interview question, as the answer to that question provides a good, practical review of the different layers of the internet. Therefore that github repo is a must read.

Nonetheless, here's a very, very simplified view of it for the budding web developer:

1. You type facebook.com on your browser and hit enter. Here, you’re essentially trying to contact the facebook server.

2. By contacting this, you make something called a "GET request"

3. What you get in response are webpage files, like a facebook page

4. You use a program to view those webpage files, a web browser like Google Chrome

Now usually, you're going to need 3 things for a webpage

1. HTML: the building blocks of the websites

2. CSS: essentially these makes HTML look pretty. They allow you to change the text, the background, and manipulating assets like photos and diagrams around such as rotating them and moving them across the screen

3. JS: helps with other things around the page, does a lot, too many to mention. Generally, it is used to add interactivity to the web page. It also allows us to load things without calling the application's server, thus it allows less server traffic and an increase in app performance.

Those 3, namely HTML, CSS, and JS, are typically called the holy trinity of web development. And you can build a ton of great applications with just those 3.

# Systems and Design

To know what work web and backend engineers do, let's look into a very high level view of the design of some large applications. And in the process, get to see some common patterns.

Sidenote: the diagrams below are made with this cool online diagram making tool called excalidraw, pretty cool that it lets me export to SVG file which when compared to an image file, SVG is 88% smaller! Looks more high quality too! Anyhow, just making that sidenote for my future reference on what to use.

## Google

<img src="/photos/2022/google-like-system.svg">

On our cloud cluster there are usually 3 components or in cloud terms we say compute nodes. First one is a web server for the search interface which the user (our client) will use to type type things out with, it's the one we interact with when we go to google.com. We send our queries to it and get back results. As we interact with the web server, it fetches data from another server (or servers) which are the index servers, which looks up for keywords from our queries. We have the 3rd compute nodes which are crawlers, which run asynchronously to update the index on real time based on data (from pages) they fetch from the world wide web.

## Facebook

<img src="/photos/2022/fb-like-system.svg">

Here we have a server to serve pages to the user. Then we have a recommendation engine running asynchronously that ranks posts that are relevant to the user. We also have a database server which contains user data. These components are decoupled from one another, to bring relevant content to the user right at the current moment.

# Engineering Problems

Those are only just a couple architectures of famous software, and these vary greatly for other systems like say designing a system like Amazon. No such perfect system design exists. Often through the designing of such systems, we attempt to do our best to just compromise what is best for our current needs. We have to do some tradeoffs to optimize for our problems. Let's look into common engineering problems.

## Consistency/Consensus

Why: when we distribute work and replicate data, we need to find a way to keep the state of our system "in-sync" for everyone so all clients see the same data at the same time

Solution: <a href="https://en.wikipedia.org/wiki/Concurrency_control">concurrency control</a>, <a href="https://en.wikipedia.org/wiki/Lock_(computer_science)">locking data</a>, <a href="https://en.wikipedia.org/wiki/Clock_synchronization">keep clocks in sync</a> to maintain consistency

Problem: our solutions can introduce significant higher performance overhead, such as locking data can result in <a href="https://en.wikipedia.org/wiki/Resource_contention">contention</a> which could introduce delay and limit the throughput, or keeping clocks in sync can add latency

## Availability

Why: need to have the system to always be available and reliable (by reliable, we mean the system performs correctly)

Solution: redundancy for availability

Problem: Redundancy increases security risk, generally slows things down/increases latency, and adds more complexity

## Interoperability

Why: to coordinate components built in different ways, either in different location, or a different programming language or framework, or in a different computing environment or hardware (like for a recent example Apple's new M1 architecture when it was introduced wasnt compatible with a lot of software)

Solution: standardization is done differently, but typically we work towards language, semantics, code, and data formats and there are different ways for performing interoperability with them. Like say using a virtual environment and FFIs for language interoperability, or for code interoperability it could be RPCs (remote procedure calls)

Problem: depending on the implementation, it could introduce additional complexity, or a point of failure, performance issue, or security issue. Finally, interoperability is a moving target as new technologies and standards are being developed

## Security/Privacy

Why: everyone will eventually get attacked

Solution: typically it is mostly about access control. But there is a new level of privacy where you intently show some level of data in a way that it'll act up as noise and wont allow other actors to re-identify data that would allow them to hack, this brings us an approach called <a href="https://en.wikipedia.org/wiki/Differential_privacy">Differential Privacy</a>, explained perfectly in the wikipedia link as

> The idea behind differential privacy is that if the effect of making an arbitrary single substitution in the database is small enough, the query result cannot be used to infer much about any single individual, and therefore provides privacy.

Problem: different human behaviours

## Discovery (resource, location)

Why: because building large systems like say one over the internet, one has to handle different nodes, services, and data. Thus at some point, locating the correct resource and data

Solution: standardization, naming paths and declaring what we're interested <a href="https://link.springer.com/chapter/10.1007/978-3-540-27866-5_144">like this approach</a>, directory protocols (LDAP)

Problem: what if we dont know what to use to match something?

## Scalability

Why: need to scale accordingly to the demand/workload

Solution: distribute the work, usually across other compute nodes or add more nodes

Problem: the more we distribute the work, the more we have to worry about how to coordinate across all these workers. We also have to worry about how to balance the load (see <a href="https://en.wikipedia.org/wiki/Load_balancing_(computing)">load balancing</a>) for all these workers to avoid any bottleneck, so that everyone gets consistent data.
