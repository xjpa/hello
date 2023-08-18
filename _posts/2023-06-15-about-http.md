---
layout: post
title: 'About HTTP'
description:
category: articles
tags: [backend-engineering, javacript, programming]
comments: true
---

In the previous blog post of this series, we looked into client-server computing and promised that we'll be looking into HTTP more in-depth and do some java programming where we'll look a bit into concurrency, of which I claimed is a good setup for learning modern frameworks. Today, let's look into it, with a little bit of JavaScript.

<!-- more -->

Let's review first: so what happens when you go on your browser and request something like a URL?

This was explained earlier in the post <a href="/articles/2023/05/09/peek-into-web">Peek into Web Development</a> under the "What happens when one types something like facebook.com into the browser?" section. But I'm in the mood for drawing it out on excalidraw lately:

<img src="/photos/2023/http-building-blocks-01.svg">

Basically your browser makes a request usually in the form of a URL to the web server which is by default at port 80. The server then handles the request for the URL, then respond back usually with a document or web page.

## URL

URL means Uniform Resource Locator

- Uniform: a standard way to follow across different protocols

- Resource: describes what we're referring to -- the resource

- Locator: location spec for the resource

URL is basically both a name/identifier and a location for the resource.

## HTTP - state protocol and sessionless exchanges

HTTP (HyperText Transfer Protocol) is a stateless protocol originally meant for sessionless exchanges.

By state we mean that the server does not keep information (state) about previous requests made by the client. By sessionless exchange we mean that requests happen independently with one another.

In the early days of the web, it was assumed that most of the requests were going to be documents, it wasnt designed to have a session that is preserved after the user makes a request.

Nonetheless, stateless model has its benefits, mostly on the server side like it provides minimal server load. But this comes some drawbacks, such as because every request is processed independently, it would request more information from the user and this would lead to more unnecessary transfers.

In time, the notion of sessionless changed. Web services started popping up where users started logging in and getting permissions. State were stored in things called `cookies` which are basically key-value pairs stored in the browser. HTTP started getting upgrades, like in HTTP/1.1, persistent connections were added which allows us to do multiple requests and responses. Over time, HTTP became more session based.

## Simple HTTP Request

Here's a simple HTTP request message, the user sends a GET request to the server (example.com)...

```
GET /index.html HTTP/1.1
Host: www.example.com
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 12.4; rv:85.0) Gecko/20100101 Firefox/85.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Connection: keep-alive
Upgrade-Insecure-Requests: 1
```

And the server responsd with an OK status code `202`, to say that the request was a success. There are a few other status codes, perhaps the most famous one is `404` for Not found. The response also includes some header information such as the `Content-Length` which says how big the document is in bytes (16384 bytes in the example), followed by a blank line, and then finally the HTML document that the user requested, you get this HTTP response message

```
HTTP/1.1 200 OK
Date: Mon, 15 Jun 2023 12:00:00 GMT
Server: Apache/2.4.6 (CentOS) OpenSSL/1.0.2k-fips PHP/7.3.25
Last-Modified: Tue, 01 Jun 2023 16:00:00 GMT
ETag: "abcd1234"
Accept-Ranges: bytes
Content-Length: 16384
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=UTF-8

<!DOCTYPE html>
<html>
<head>
	<title>Example Website</title>
</head>
<body>
	<h1>Welcome to Example Website!</h1>
	<p>This is a sample web page served from the server.</p>
</body>
</html>
```

Here's one in javascript

The right half of the screen is the javascript code on emacs. Left half of the screen is two terminal windows, the one at the top is where I'm running the server, the one below is one i'll use to enter curl commands later to the server.

<img src="/photos/2023/http-building-blocks-01-01.jpg">

I entered the curl command to visit `localhost:42069` on the bottom terminal, notice the change

<img src="/photos/2023/http-building-blocks-01-02.jpg">

Below, I ran curl on `localhost:42069/curl-me`, where I coded in specific instructions to send back "received get request" followed by a newline (\n). Notice also the terminal message at the top.

<img src="/photos/2023/http-building-blocks-01-03.jpg">

Below, this time I run `curl --data`, which sends specific data in a POST request

<img src="/photos/2023/http-building-blocks-01-04.jpg">

Again, notice the messages in the 2 terminals in the left.

## Request Types

You may have notice a few things, especially GET and POST.

- GET is a request that happens when you type URL into your browser, which retrieves the resource at the URL. <u>Idempotent operations</u> only, meaning if I do GET multiple times like for a webpage, it will do the same thing (return the same page, unless otherwise the webpage you're fetching has been modified).

- POST is used for submitting, and allows key-value pairs which you've seen in the above example where we sent the kv pair `{"hello":"world"}`. In contrast to GET, POST allows for <u>non-idempotent operations</u>, like suppose if you used POST 2 times to submit a form, you are submitting multiple (2) forms.

A few other request operations are HEAD (returns just the header, useful if you dont want to get long documents), PUT (for publishing documents on a server), and DELETE (delete documents on a server). Most static servers dont allow PUT and DELETE, those are for servers handling dynamic content
