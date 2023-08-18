---
layout: default
title: How to Design Programs
---

<center><p><big>Fixed Size Data</big></p></center>

These are notes I took while going through the HTDP book and its exercises.

<img src="/photos/books/htdp2.jpg" height ="300">

COMPOSITION and AUXILIARY

- Typically, programs consist of a main function as well as other programs that turns the output of 1 function as input for another

- this is called COMPOSITION, in analogy to algebra

- and the additional functions are called AUXILIARY FUNCTIONS

DEFINE ONE FUNCTION PER TASK

- one function per task and one main function that puts it all together

- to get small programs and composition that’s easy to understand

- organized collection of small functions are easier to work with than a large MONOLITHIC block

- see page 60 for an example of how a problem was broken down

MAGIC NUMBERS

- <p>give NAMES to constant numbers so future code readers would know where that number is from, dont just do something like</p>

```racket
(define (attendees ticket-price)
        (- 120 (* (- ticket-price 5.0) (/ 15 0.1))))
```

- <p>instead, do something like the ff, the usefulness will be seen more effectively in a larger codebase</p>

```racket
(define NUMBER_ATTENDEES 120)
(define PRICE_OF_TICKET 5.0)
(define ATTENDANCE_CHANGE 15)
(define PRICE_DOWN 0.1)

(define (attendees ticket-price)
        (- NUMBER_ATTENDEES (* (- ticket-price PRICE_OF_TICKET) (/ ATTENDANCE_CHANGE PRICE_DOWN))))
```

<a href="/bookshelf/htdp2">⬅️ back to HTDP</a>
