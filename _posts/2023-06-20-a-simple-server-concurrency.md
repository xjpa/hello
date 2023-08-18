---
layout: post
title: 'A Simple Server and a Look Into Concurrency'
description:
category: articles
tags: [backend-engineering, backend-odyssey, java, programming]
comments: true
---

Continuing from the previous post in this backend engineering series where we discussed HTTP and the building blocks of a server, let's look into one.

Below is the code for a very simple server written in Java

```java
import java.io.*;
import java.net.*;
public class Server {
    public static void main(String[] args) throws IOException {
        ServerSocket serverSocket = new ServerSocket(80);
        while(true){
            Socket socket = serverSocket.accept();
            InputStreamReader reader = new InputStreamReader(socket.getInputStream());
            BufferedReader in = new BufferedReader(reader);
            PrintWriter out = new PrintWriter(socket.getOutputStream(), true);
            out.println("<html>" +
                    "<head><style> body { font-family: Tahoma } </style></head>" +
                    "<body>" +
                    "<p><big><big>&lt;uwu&gt;Hello this is my doggo!&lt;/uwu&gt;</big></big></p>" +
                    "<p><a href='https://xjpa.github.io/star/'>" +
                    "<img src='https://xjpa.github.io/star/doggo.jpeg'>" +
                    "</a></p>" +
                    "<body></html>");
            socket.close();
        }
    }
}
```

<!-- more -->

When visiting the port on a browser, it shows the following page with a picture of my family's doggo

<img src="/photos/2023/server-star.jpg">

## What happened there?

Let's look at some important lines of code

```java
while(true){
 ServerSocket serverSocket = new ServerSocket(80);
```

^In the above we started with an infinite loop to listen to port :80 for requests, creating a socket object

```java
Socket socket = serverSocket.accept();
```

^Then we connected through the input through a socket...

```java
 InputStreamReader reader = new InputStreamReader(socket.getInputStream());
```

^...which we would read through an input stream.

After that, we returned through that same socket an HTTP response:

```java
out.println("<html>" +
                    "<head><style> body { font-family: Tahoma } </style></head>" +
                    "<body>" +
                    "<p><big><big>&lt;uwu&gt;Hello this is my doggo!&lt;/uwu&gt;</big></big></p>" +
                    "<p><a href='https://xjpa.github.io/star/'>" +
                    "<img src='https://xjpa.github.io/star/doggo.jpeg'>" +
                    "</a></p>" +
                    "<body></html>");
```

Of which gave us the screenshot of the browser tab that has a pic of my family's dog above.

This server basically accomplishes the core blocks we discussed on the previous section. But what it doesnt do, is handle concurrent socket requests.

## But first, an aside: context switching

[According to wikipedia](https://en.wikipedia.org/wiki/Context_switch), in computing, a context switch is the process of storing the state of a process or thread, so that it can be restored and resume execution at a later point

When a processor switches between tasks, it must first save the state of the current task, including its registers, program counter, and other important data. It then loads the state of the next task and begins executing it. This process is known as a context switch because the processor must switch its execution context from one task to another.

Context switching is an essential part of multitasking operating systems, which allow multiple processes or threads to run concurrently on a single processor. It allows the system to allocate resources to different tasks as needed, providing the illusion of parallelism even though the processor can only execute one task at a time.

Context switches can be expensive in terms of time and resources, so they are typically minimized whenever possible. For example, some operating systems use techniques like prioritization and preemption to minimize the frequency of context switches and improve overall system performance.

## Running things simultaneously

Okay so let's get back, how do we handle concurrent socket requests? One thing we ought to take note of is that today, we use multicore processors in our computing devices. Even our small computers like our smartphones range from having 2 to 8 cores. Servers have more than that, having 64 cores to double or quadruple of that. We can take advantage of this by running a program on EACH core. To be specific, we will handle each request by running a copy of the program for each of the cores.

It's a simple solution, but it's not a good one. Even your OS doesnt do this, because most applications are running idle, thus you have CPU cores wasting time. In our case, it'll be wasted on waiting for web requests. Not to mention the fact that we have more programs than we'll have cores.

So what will happen is that on multicore prcessors, we're going to do a lot of <u>context switching</u>. Basically we're running parallel programs, BUT what really happens is we're running Program A, then we switch to program B.

You see, one thing to take note of that when we write processes (process-execution of a program), a process assumes that it has all the resources for itself, like as if they own all the memory and the machine itself. <u>They should not see each other's variables for security reasons.</u> Thus, they get to have something called a <u>virtual memory</u>, a space for them that protects them from other programs.

When we're running a lot of processes, this is often done through called <u>pre-emptive multitasking</u>. Basically the system will run program A for a short amount of time (milliseconds), then the system takes a "snapshot" of its state and puts it into a queue of other programs, then we switch over (meaning the instruction pointer will now move) to program B or program C, depending on what's on the queue. Then after they're done, we go back to load the "snapshot" of program A, and the cycle repeats. Through every step, we're swapping the virtual memory, stack, and instruction pointers, and we're doing them so fast that it looks like we have multiple programs running simultaneously and that you dont even notice that there is context switching.

The problem we got though is that for our web server, we dont want multiple programs. We just want one that can do simultaneous requests. Remember that processes ought to not see each other's variables and state for security purposes. But for a web server, we have to share global resources with web request handlers. We want to do both context switching AND to sharing memory.

One way to do this, is by using threads and its variant, thread pools. We'll see it on the next post of this backend engineering series.
