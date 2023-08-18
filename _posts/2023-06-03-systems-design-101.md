---
layout: post
title: 'Systems Design 101 and Interfaces'
description:
category: articles
tags: [learning, programming, backend-engineering]
comments: true
---

Systems Software are a bunch of interoperating components that manage computing resources. Some examples of systems software includde database management systems and operating systems. Designing for them requires generality and reusability, and this in turn requires testing them on various inputs for various different situations. This makes them harder to design than programs/applications/general software, which are typically built to do a specific task.

<!-- more -->

With that in mind, let's see about how to design such systems

<center>
<img src="/photos/2022/picasso-style-robot-design-computer-system.png">
</center>

# Engineering Problems

I recommend going another reading of the previous blog post, [Peek into Web Development](/articles/2023/05/09/peek-into-web), the last part as it discusses some common problems like scalability and solutions.

# Hints for Computer Systems Design

Let's look into a paper by <a href="https://en.wikipedia.org/wiki/Butler_Lampson">Butler Lampson</a> called [Hints for Computer System Design](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/acrobat-17.pdf)

A good summary can be seen in the figure here from the paper

<img src="/photos/2022/lampson.png">

It is sort of outdated, at least with one part in the diagram for implementation where it says to "plan to throw one away." While it is generally true that even today's software engineering our original implementation and design will be re-architected and refactored over time, if we read the details of Lampson's "plan to throw one away" in the paper, it says:

> **<u>Plan to throw one away</u>**; you will anyhow. If there is anything new about the function of a system, the first implementation will have to be redone completely to achieve a satisfactory (that is, acceptably small, fast, and maintainable) result. It costs a lot less if you plan to have a prototype. Unfortunately, sometimes two prototypes are needed, especially if there is a lot of innovation. If you are lucky you can copy a lot from a previous system; thus Tenex was based on the SDS 940. This can even work even if the previous system was too grandiose; Unix took many ideas from Multics.

It's a good advice but it came from an era when there were only a few software engineering tools around, so people tend to build a prototype, take notes of the lessons learned, then re-implement it from scratch. Nowadays, refactoring is easier than ever and we have tools that make it easy to scale prototypes out.

Nevertheless, the rest of the paper is a very good read in learning how to design applications. Like just from the figure above:

- 3 columns (Functionality, Speed, Fault Tolerance): the kind of engineering for functionality, speed, and fault tolerance should be separate

- Completeness - Separate normal and worse case: otherwise, you get spaghetti code, so separate the behaviours

- Interface - Do one thing well: good advice to "dont generalize" things interfaces as this makes it easier for us to optimize it and "make it fast."

- Implementation - Use a good idea again: basically modularize things

- Implementation - Speed: compute in background and process in batches if you can for speed. Lampson explains this further in the paper

> **<u>Compute in background when possible</u>**. In an interactive or real-time system, it is good to do as little work as possible before responding to a request. The reason is twofold: first, a rapid response is better for the users, and second, the load usually varies a great deal, so there is likely to be idle processor time later in which to do background work. Many kinds of work can be deferred to background. The Interlisp and Cedar garbage collectors do nearly all their work this way. Many paging systems write out dirty pages and prepare candidates for replacement in background. Electronic mail can be delivered and retrieved by background processes, since delivery within an hour or two is usually acceptable. Many banking systems consolidate the data on accounts at night and have it ready the next morning. These four examples have successively less need for synchronization between foreground and background tasks. As the amount of synchronization increases more care is needed to avoid subtle errors; an extreme example is the on-the-fly garbage collection algorithm given in. But in most cases a simple producer-consumer relationship between two otherwise independent processes is possible.

> **<u>Use batch processing if possible</u>**. Doing things incrementally almost always costs more, even aside from the fact that disks and tapes work much better when accessed sequentially. Also, batch processing permits much simpler error recovery. The Bank of America has an interactive system that allows tellers to record deposits and check withdrawals. It is loaded with current account balances in the morning and does its best to maintain them during the day. But early the next morning the on-line data is discarded and replaced with the results of night’s batch run. This design makes it much easier to meet the bank’s requirements for trustworthy long-term data, and there is no significant loss in function.

Again, I recommend reading the paper.

# In Action

Let's put a few of the lessons from the paper into practice

Suppose we're designing a <a href="https://en.wikipedia.org/wiki/Comparison_of_distributed_file_systems">distrubted file system</a>, basically something that fetches files from the cloud or some network. Let's suppose in this case it's log files.

To start with, we start with usecases. Well in this case it could be opening files, reading them, then closing then. We can optimize its speed with the advice of "do one thing well" for the interface. In this case, optimizing it with smart buffers and caches, basically read a lot of lines at a time before we parse and return to the user.

Now this is great, but sometimes some users may not want the approach of reading line by line, perhaps because the text is in a different language that doesnt get parsed right normally or some other reason. In this case, we can use the advice of "don't hide power" which in the paper is explained in detail:

> <u>Don’t hide power.</u> This slogan is closely related to the last one. When a low level of abstraction allows something to be done quickly, higher levels should not bury this power inside something more general. The purpose of abstractions is to conceal undesirable properties; desirable ones should not be hidden. Sometimes, of course, an abstraction is multiplexing a resource, and this necessarily has some cost. But it should be possible to deliver all or nearly all of it to a single client with only slight loss of performance.

We use it by providing another interface, an alternate that would provide file blocks instead of lines.

# Interfaces

We've been mentioning interfaces for some time now, but never really looked into it. Interfaces or APIs (Application Programming Interfaces) are like contracts or a spec that allow other developers to develop things on your interface without them needing to know the implementation of the application, and that these developers can trust you that it'll work even if you make some implementations or updates to the code because as said Lampson in the paper "Keep basic interfaces stable" or explained more in the 9th page of the paper:

> Keep basic interfaces stable. Since an interface embodies assumptions that are shared by more than one part of a system, and sometimes by a great many parts, it is very desirable not to change the interface. When the system is programmed in a language without type-checking, it is nearly out of the question to change any public interface because there is no way of tracking down its clients and checking for elementary incompatibilities, such as disagreements on the number of arguments or confusion between pointers and integers. With a language like Mesa that has complete type-checking and language support for interfaces, it is much easier to change an interface without causing the system to collapse. But even if type-checking can usually detect that an assumption no longer holds, a programmer must still correct the assumption. When a system grows to more than 250K lines of code the amount of change becomes intolerable; even when there is no doubt about what has to be done, it takes too long to do it. There is no choice but to break the system into smaller pieces related only by interfaces that are stable for years. Traditionally only the interface defined by a programming language or operating system kernel is this stable

An example of working with interfaces is in the previous blog post <a href="/articles/2023/05/09/peek-into-web">Peek into Web Development</a>. I'll bring up the image of the OSI model layer again from that post

<img src="/photos/2022/osi.png">

In the real world, interfaces allow us to work through many different layers. As we can see, the internet is built on top of many different layers, we use interfaces to develop higher level abstractions. Like say on the HTTP layer we can build web services, and on web services we can build whole apps. Having different layers is important for designing systems as it helps make things easily testable which makes one pinpoint which things arent working correctly fast.
