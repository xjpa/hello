---
layout: post
title: 'A New Portal'
description:
category: articles
tags: [life, upskill]
comments: true
---

<style type="text/css" rel="stylesheet">
.video-responsive{
    overflow:hidden;
    padding-bottom:56.25%;
    position:relative;
    height:0;
}
.video-responsive iframe{
    left:0;
    top:0;
    height:100%;
    width:100%;
    position:absolute;
}
</style>

I recently renewed my passport, and going through the process slowly reminded me of
my youthful passion for travel. I mused about it for a while but the day's events made the fleeting reminiscences gradually fade from my mind

Until I woke up at 4:20 ([Blaze it!](https://youtu.be/ek1G1hVliMI)) in the morning, perhaps thanks to my dog's snores sleeping on her comfy indoor dog house next to mine. It's dark in my room, so I reached for my phone, and its lights unveiled a soft glow. My gaze fell into a corner of the room. And saw a bracelet, a cheap souvenir from a trip to Colombia in 2019. Seeing that was the ultimate catalyst. Igniting a desire within me to seek something new. I want to travel again, and not just that, I want to start a new journey.

<!-- more -->

And while dazed by sleepiness, I opened my laptop, and recorded myself in the dark, with just the light from my macbook piercing the room as I plot out what messy epiphanies for a manifesto I have in mind before I went back to sleep again. You can watch it below:

<hr>

<video controls ="" width="100%" src="https://xjpa-assets-2023.netlify.app/2023-manifesto.mp4" type='video/mp4'>
</video>

I talked about my plans in the above 8 minute video, I compressed it to 40 MB for those using mobile data. I went over the why for these decisions, such as the Olson hypothesis or the lack of context cues in Japanese. A potpourri of topics from a sleepy guy talking fast so he can go back to sleep quick

<hr>

## I. ML and Infra

A journey worth looking into: AI

> "Artificial intelligence represents the biggest potential long-term support for profit margins. Our economists' productivity estimates suggest AI could boost net margins by nearly 400 bp over a decade" - Goldman Sachs, 2023-05-18

<a href="/photos/2023/dragons-to-slay.png"><img src="/photos/2023/dragons-to-slay.png"></a>

AI agents are the future, they'll just keep getting better and better. And not just AI, the complexity of software as well. The difference between now and back when I was still in college, was that the infrastructure has exploded. So many new infra patterns today like containers and k8s. Even the dev environment has gotten more complicated.

> Don't you dare to tell me that my isomorphic Node trpc graphql with redux and sagas on top of next.js with SSG and SSR and parts in server components with my home grown validation and ORM framework and still no translations because they don't work together with everything else and deployed on serverless docker lambdas to a kubernetes cluster is over engineering a landing page with a contact form. So fast!
>
> That's a state of the art WebApp. You old PHP developer!
>
> ([source: HN comment](https://news.ycombinator.com/item?id=35898209))

Understanding distributed systems will be harder, because of the added mental overhead, you must now choose which abstraction level(s) you must focus on

There's definitely some pessimism in software from veterans as well:

> Modern programming is becoming complex, uninteresting, full of layers that just need to be glued. It is losing most of its beauty. In that sense, most programming is no longer art nor high engineering (most programs written at big and small corporations are trivial: coders just need to understand certain ad-hoc abstractions, and write some logic and glue code). Only very few programmers are facing the artistic face of programming. Only very few programmers are facing high engineering in programming.
>
> ([source: the creator of redis](http://invece.org/))

Of which attracts me instead to the 'wild west' worlds of software: AI, its infra, and crypto.

I am still developing my plan for how to approach AI and Infra, the above image of my trello board is just me throwing every interest or idea to the wall, and it includes all my other interests in software, such as graphics. It still needs to have some of its branches pruned. A lot. One that focuses into ML & AI infra (the whole suite of it-- not just MLops and Data Engineering).

Currently, I have enrolled to a few courses on udemy such as

- [A deep understanding of deep learning (with Python intro)](https://www.udemy.com/course/deeplearning_x/)

- [Master statistics & machine learning: intuition, math, code](https://www.udemy.com/course/statsml_x/)

As well as I have enrolled to a few courses by Andrew Ng at coursera, and will be learning data engineering as well, properly this time. Crack open a few books collecting dust on my bookshelf.

Skipping data engineering and jumping straight into the 'data engineering' part of ML Engineering is also another viable route, given that majority of today's data engineering still tends to focus too much on SQL and ETL pipelines. While MLOps overlaps a lot with Data Engineering, ML Engineering tends to have a different focus and more into implementation of ML papers or some MVP, more work with distributed programming and python, more focus on streaming data, and has unique parts such as it is mostly working with FTI pipelines (Feature, Training, Inference). When a data engineer hears the word "transformation" they automatically think of aggregations, ETLs, and data preprocessing. ML Engineers on the other hand think of things like label encoding and log transformation, and localizing transformations based on the model. So while it seems that data engineering overlaps with ML Engineering, the devil is in the details: data engineers focus on data transformations, while ML Engineers focus on the feature and model transformations.

I am also interested in learning a few fundamentals in software engineering, at least those that are focused on the backend, adjacent to infra needs. While we've mentioned that infra has exploded, many of the things from the past still maps to the ones we have today. For example here's a few examples of fundamental concepts and what they map out to in the very buzz word/hyped-up world of cryptocurrencies

- <u>consensus</u>: sybil attacks, incentive mechanisms/cryptoeconomics, proof of work, proof of stake

- <u>deterministic computation</u>: crypto algorithms, crypto wallets, merkle trees (uses deterministic hashing algos)

- <u>P2P networking</u>: decentralized architecture, peer discovery, various network security (eg. sybil attacks, eclipse attacks) and application (various network topologies)

Lots of the "innovations" we use today in computer science were lifted from a paper 20+ years ago. The computer scientists back in the 80s-90s did a lot of the heavy lifting and now we're just revisiting them.

Their generation had memory constraints and hardware constraints, things we are abundant with today. It was only a decade ago when SSDs became mainstream. As Howard Stark in Iron Man 2 says:

> I built this for you. And some day you'll realize that it represents a whole lot more than just people's inventions. It represents my life's work. This is the key to the future. <mark>I'm limited by the technology of my time</mark> ([source](https://www.imdb.com/title/tt1228705/characters/nm0805476))

I've been reading CS papers and some of the last papers I read were from that decade. I'm planning to make a toy clone of redis, and would you know that the approximate counting algorithm that redis uses stemmed out [from a paper from the 90s](https://dl.acm.org/doi/10.1145/78922.78925). That's why revisiting the classics and foundational texts can be important. All these hyped up "breakthrough" hipster languages today like Rust, Zig, and Carbon, the features and compiler optimizations they have today were penned decades ago.

<center><p><mark>Backend curiosities</mark></p></center>

I also have a few curiosities into backend engineering, I might pursue them. If I were to approach learning backend, I would do them in the following to get me to understand concepts that would cross-pollinate to other domains such as infra better, some of them are in the trello board image:

- <p>Typically I would recommend something like this when learning web engineering, in the following order and I think it's still a fine plan but I am just not feeling a methodical approach</p>

```
1. frontend

-> -> -> HTML/css
-> -> JS state (e.g. Vuex, Redux)
-> JS (e.g. Vue, React, GraphQL, service workers)

2. backend engineering

-> Load Balancer (e.g. nginx)
-> -> Caching (e.g. redis, memcached)
-> -> Containers (e.g. Kube, Docker)
-> -> MQ/Bus (e.g. RocketMQ, Kafka, PubSub)
-> -> -> Async RPC services (e.g. grpc, thrift)
-> -> -> -> SQL (e.g. Spanner, Aurora)
-> -> -> -> NoSQL (e.g. Cassandra, Neo4j for graphs)
```

- Instead, I'll just start with just getting some practice with CRUD, build a project perhaps start with a simple note sharing app, or maybe something will give me more practice with DB schema design like a CMS. A more complex one for practicing DB would be an e-commerce system, and would give us a lot more to play with, like say designing it for scale -- what if there's lots of read/write traffic during sales and holidays? It gets us then to play with things like DB replicas.

- Speaking of replicas, worth a look into drilling into essential concepts of it for data recovery and continuous redundancy. A good exercise would be to setup replication between 2 SQL Servers, then backups, then how to restore.

- Speaking of disaster recovery, look into leader election. Read papers about it, implement it. Probably might be an interesting weekend project to put on the resume, like call it a "generic crash-recovery framework." No need to spin up multiple machines to simulate it, just start with something simple, like coding up a few threads and just having the master thread kill itself.

- Get a side project that gives me a whirlwind tour of "big corp" backend development. Like I got an n-tier system, with each component being dockerized and some components using a different stack+programming language, each broken down into microservices, gateway and service discovery for the microservices, load balancers for system and client, has tracing+monitoring+logging, system is built to scale with caching+async+batch processing+uses distributed DB, and kubernetes to manage the deployment of this garbage. Basically build an overengineered pile of mess.

- A good project for the above would be a clone of a social network. Follow some quick tutorial on youtube to build a facebook or whatever clone fast, [lots of tutorials on youtube use MERN stack](https://www.youtube.com/results?search_query=facebook+clone). Then rearchitect them for scale. Add redis for caching. GraphQL for microservices. Add distributed tracing, service discovery, circuit breaker pattern -- not sure what libraries to use for these on MERN ecosystem, I'd have to search. Websockets for anything low latency and realtime like chat/messages. Add Kafka for fun, like use it for user analytics or notification management or newsfeed generation. Apache Solr or Elasticsearch for search. Possibilities are endless here. Play with micro-optimizations like micro-CDN optimizations like many people dont know you can optimize images in CDN, do some connection pooling, etc.

- Get a whirlwind tour of streaming projects. Build a project that processes streaming data, utilizing AWS for RDD and in-memory caching. [This is a good project idea to start with](https://databricks.gitbooks.io/databricks-spark-reference-applications/content/twitter_classifier/index.html).

- Toy distributed system project: build something with redis, kafka, cassandra, pub/sub, and websockets, configure the load balancer, shard the DB, etc. It could just be a simple service, like it could be a database query or a map reduce function. What matters is the integration of such technologies. Dockerize all and deploy to AWS or some other cloud.

- Do some projects to practice low latency programming, perhaps a server as a project as I'm only thinking about general network latency and not the low latency usually referred in finance/high frequency trading (HFT) which is mostly data latency (reading from FPGAs)

- Build a URL shortener. Not your typical URL shortener youtube tutorial project. Built it with Domain Driven Design (DDD) in mind and for scale. Add analytics capturing + visualization with say elasticsearch. Design for low latency, like say adding a cache to reduce the DB load and the latency. With these in mind, implement a good encoding scheme to learn the bits of it, get to learn sharding, partitioning, and dealing with pseudorandomness.

- get some practice with realtime app development. like say start with something basic like socketIO practice by building an FB messenger clone, or pick up a harder project like learn some CRDT and play with P2P communication algorithms like a gossip protocol to build a google docs clone. or how does video streaming work and video caching? look that up and build some netflix clone [Netflix-What Happens When You Press Play?](http://highscalability.com/blog/2017/12/11/netflix-what-happens-when-you-press-play.html?currentPage=3). Figure out why Netflix rewind is so good and fast compared to other on demand services like HBO Go. How do they cache that?

- big data project: apache spark -> spark streaming

- read posts from highscalability.com

- [YouTube-DeFogTech](https://www.youtube.com/c/DefogTech/videos)

- read: [https://jenkov.com/tutorials/java-concurrency/index.html](https://jenkov.com/tutorials/java-concurrency/index.html)

- read: [http://jeremymanson.blogspot.com/](http://jeremymanson.blogspot.com/)

- learn about design of stateless/soft-state services

- read famous papers on backend systems ex. GFS, MapReduce, HDFS, Cassandra, Earlybird, Kafka, Aerospike, Zookeeper, Twitter Earlybird, CockroachDB, Spanner, Monarch

- optional: blockchain hype, read papers at: [http://nil.lcs.mit.edu/6.S974/papers.html](http://nil.lcs.mit.edu/6.S974/papers.html)

- read a few papers and projects linked at the "End" section here: [The Log: What every software engineer should know about real-time data's unifying abstraction](https://engineering.linkedin.com/distributed-systems/log-what-every-software-engineer-should-know-about-real-time-datas-unifying)

- play around with zookeeper, cassandra, kafka, redis, etc. try them with docker and use them to build some dockerized components to form the backend of popular/simple projects. focus on the backend for these types of projects, leave off complexity that doesnt contribute (ex. proper auth implementation, frontend)

- look into their codebase, understand their internals or read up more about their features

- maybe try contributing to the source code of these projects

- build a simple clone of these tools, i looked at github and lots are building stripped down versions of these like kafka and redis. Redis is probably good to start with. I get to dive more into lock free programming, good resources: [github.com/JCTools/JCTools/](https://github.com/JCTools/JCTools/tree/master/resources)

- build an upload service: perhaps for photos and videos? or just log files? or how about a file system? goal is get to learn serving static files, and how to scale them, CDN stuff. Maybe write a very simplified clone of AWS S3. Wait, not a maybe. Let's write one.

- learn kubernetes/mesos/docker swarm, build a clone of these. Docker should be approachable.

- work on project that will get me studying state machine replication , such as building/working with a matchmaking engine for stock trading or heavy transaction systems or blockchain/distributed ledgers

- more practice with distributed systems, specifically with managing consensus and locking, projects like build a fault tolerant reservation system

- how can we handle things like double booking? go for pessimistic locking or optimistic? if so how will the implementation be, etc.

- build a search engine: get to learn some information retrieval concepts and parsing and NLP skills that'd be helpful for a software engineer

- 📚 read DB internals book

- build a database system or database engine

- 📚 read Designing Data Intensive Applications/DDIA book

- 📚 read Building Secure and Reliable Systems from sre.google

- build a KV store, preferably SQL backed

- pick up the KV store built, then this time build a realtime DB on top of it. practice with handling broadcasting in this case will be a good practice

- continuing from previous, learning to do high speed and reliable broadcast would be good, so perhaps after learning all of the above, do a more serious attempt at building an exchange

I might learn them, or just focus headfirst on ML instead, then deep dive into infra later by building clones of systems like Google Colossus, Database Engines like SQLite or an RDBMS, an analytics engine like Apache Spark, Docker, and more like a network stack.

Or I can just learn infra from a devops perspective, such as taking [this route](https://news.ycombinator.com/item?id=33398284) I saw at HN.

Then I'll turn myself forward into my other curiosities like building a compiler, just because of blog posts like [Steve Yegge's about the value of learning compilers](https://steve-yegge.blogspot.com/2007/06/rich-programmer-food.html). I've built one before, but I never went deep into it.

We shall see.

<hr>

## II. Economics

I am still not sure of my plans for how to approach this one.

As mentioned in the video, I have brought up books like Rise and Decline of Nations, so that makes me more keen to start studying it from a [geoeconomic](https://en.wikipedia.org/wiki/Geoeconomics) perspective

<img src="https://xjpa-assets-2023.netlify.app/pics/rise-decline-nations-compressed.jpeg">

But among the top of my questions I want to get answered is:

> why do layoffs happen?

It's a curious thing. You can easily google it and convince yourself that you truly understand it from bits of articles and forum discussions. But I want to dive deep into it. Why is it that my highly performing friends got laid off? These people are geniuses. Why is it that my friends who KTLO, such as those who work on areas such as infra whether that be platform or ML infra, and those who work on ops (dataOps, MLOps, site reliability engineering although you could argue nowadays it is a separate field as infra complexity is ever increasing) are typically the first ones to get laid off en masse at big tech companies?

And the more I read about it, the more I get hooked into the interesting rabbit hole of economics

Is it just because of P&L analysis by the higher ups? Maybe for some but even still, what factors are taken in? I read a book recently called [Sense And Nonsense In Corporate Finance](https://www.amazon.com/Sense-Nonsense-Corporate-Finance-Lowenstein/dp/0201523582), and it helped me understand a bit of it.

It is by the way, a really good book, here's my brief review of it from my website:

> Capital allocation is a great subject to learn as it provides a unique big picture view, especially that for a crucial aspect of business strategy that many developers and leaders lack. Why do layoffs happen that way? How to think about PIP? How to think about earnings? What projects should we focus on? How do we measure efficiency? How do unprofitable “moonshot” companies/startups like Uber survive and what’s their gameplan?

But I want more. Going down the rabbit hole of capital allocation gets you eventually reading into the philosophies of other schools of thoughts, such as the Austrian school whose skepticism towards central banking, especially from renowned economists like [Ludwig von Mises](https://en.wikipedia.org/wiki/Ludwig_von_Mises) and [Friedrich Hayek](https://en.wikipedia.org/wiki/Friedrich_Hayek), eventually gets you down to things like bitcon.

[Nick Szabo](https://en.wikipedia.org/wiki/Nick_Szabo), one of the guys theorized as the bitcoin creator thanks to his work on Bit Gold in 1998, has a blog that has taken hold of my interest lately, as it's a good collection of writings on finance, economics, and CS.

Here's what I'm reading of Nick's: [Of wages and money: cost as a proxy measure of value](https://unenumerated.blogspot.com/2011/07/)

Read that, and tell me that out of all the non-falsifiable subjects (since plenty of people nowadays dismiss it like one), tell me how this is one intellectual rabbit hole that is not worth getting into

<hr>

## III. Live a better life

The bracelet from Colombia was my portal, my [call to adventure](https://en.wikipedia.org/wiki/Hero's_journey)

To seek something new, and that pushed me to move to the wild west of software: ML & its Infra. And to pursuea intellectual curiosities such as a better understanding of the complex system of economies.

I want to live a better life that is driven by internal curiosity, and of which provides me enough economic mobility and individual mobility to stay upwind. Thus two things came up, I'll add more in the future:

#1. Get Fit

Get healthier, so that we can live a longer life and live those years at our best performance.

ALSO AESTHETICS. I need to get back to working out with weights, all I've been doing are cardio like Muay Thai and some calisthenics, doing at least 300-400 pushups and 150 pullups every session. But these arent giving me gains. I'm sick of not looking like I dont FUCKING WORKOUT. Just look at myself in the video. <mark>Being gym built is still king.</mark>

When I used to hit the gym, every chick I walked by from Asians to Europeans checked me out and smiled at me when I passed them. I felt good at myself and had no problems saying hi followed by some bullshit assumption to start a conversation like "you must be an artist," later asking them out. How on Earth did I got convinced by youtube videos during the COVID-19 pandemic (at the time every gym got shut down) that calisthenics and "functional training" is better?

I also need to fix my sleeping patterns. I would bet you also arent getting a good 8-hour sleep every night as well, we ought to fix that. Mental health is also worth looking into as well as mental performance.

Finally: Healthspan vs Lifespan.

> My bones are worn, my hip won't hold
>
> I used to be so young, how did I get so old?
>
> (<a a href="https://youtu.be/ysFZ3Uqudww?t=135" target="_blank">source: song by Dan Mangan called Basket</a>

Focus on maximizing healthspan. Sure, you dont need to hit the gym to live long, you can just eat well and stay away from bad vices. But that's the difference with healthspan and lifespan. Focusing on one's health lets you not just live long, but also gets you to spend most of your days especially the last years of your life with a far superior quality of life, away from sickness, and atrophied muscles and weak joints. In a way, maximizing healthspan also maximizes one's overall span of life.

#2. Learn a new language

In the video, I described my decisions for learning Japanese as it provides me a different philosophy. But the main reasoning for learning a new language is to open up myself to unforeseen opportunities, as well as to polish my faculty for memory.

Let's expand on the topic of memory...

A problem among those in tech is that they tend to look down on this because we can

> "just google it"

But memory is one giant factor for understanding complexity and even for creative tasks.

You will see this more when you're around people at the top of their game.

I remember going through a book called [Black Hole Blues](https://www.amazon.com/Black-Blues-Other-Songs-Outer/dp/030794848X)

<center><a href="https://images-na.ssl-images-amazon.com/images/S/compressed.photo.goodreads.com/books/1528655022i/27430326.jpg"><img src="https://images-na.ssl-images-amazon.com/images/S/compressed.photo.goodreads.com/books/1528655022i/27430326.jpg" width="250"></a></center>

It was about a landmark experiment in the 2010s that won a [Nobel prize in 2017](https://www.washingtonpost.com/news/speaking-of-science/wp/2017/10/03/nobel-prize-in-physics-won-by-rainer-weiss-barry-barish-and-kip-thorne/). It gave us the first observation of gravitational waves cementing Albert Einstein's theory from 100 years ago (1915 General Theory of Relativity).

In the book, they explain that a big part of why [the whole project](https://en.wikipedia.org/wiki/LIGO) succeeds is because of one scientist named [Rana](https://en.wikipedia.org/wiki/Rana_X._Adhikari). Whenever there's anything wrong with the instruments or the system, it is much faster to debug it by consulting this one person. And Rana attributes it to memory.

> He memorizes everything he can about each system so he can just think through issues and possibilities instead of trying to go back to a desk and a computer, paper and pens, to devote several hours to calculating. There just isn’t the time for that sort of thing, and so he has to imagine it, imagine how it would all work, and then he can just sort of say yes or no, that will or won’t work.

So much of who you think is a high performer, is there thanks to their exercised memory

As information gets easier and democratized to everyone through apps like ChatGPT and its inevitable better iterations in the future, the ability to process these information will be vital to stay competitively ahead.

We ought to sharpen both our technocapital and biocapital tools that would enable us to tackle life as if like a hill climbing optimization process, focusing on the local minima.

You could approach it like a gradient descent process as well, but it might be poor thanks to the noise of man's psychology that seeking the global minima (ultimate goals) would need large quantities of willpower, as well as self-reflection. For example, have you done enough self-reflection that you have an answer to this: What do you truly want in life that you'll want it bad enough that you can grind 4 hours/day for years until you get it? 4 hours is already a modest amount, should be more.

Hill climbing optimization is a quicker way to build expertise, as well as escaping the challenges in the local minima is easier to do in real life when we take things one at a time.

Algorithms that exploits the neighbouring solutions follows closely what PG advises on his excellent writing, [What You'll Wish You'd Known](http://www.paulgraham.com/hs.html). As PG writes, it is better to stay upwind. To take the small victories as they add up, then we can just re-align ourselves with the wind. The world moves so fast, that there may be better things that'll grab hold of your interest in the future.

We get to see more portals that provide us with the calls to adventure that way too.

---

And to that, I end the post with this

<div class="video-responsive">
  <iframe src="https://www.youtube.com/embed/pb_yvBNLjNk" height="344" width="459" frameborder="0" allowfullscreen></iframe>
</div>

<p></p>

One of my favourite parts of monomyth movies is the training montage. Where the hero seeks tutelage from an old master, or goes to a dojo in the snowy mountains, and they would just start training relentlessly until we later see them emerge as a new man.

But unlike movies, life is full of noise. Distractions are everywhere.

Some people make it their mission to trap you into it. Turn on the television or your phone and what do you see?

People everywhere including the media telling you that the world is ending. Such as in my country:

> "We have a new president, and he's bad. Read this, join our cause."

But years later, looking back from all the news from my country, and all the "sky is falling" posts at [reddit.com/r/philippines](https://reddit.com/r/philippines) and facebook about this bad president ([Duterte](https://en.wikipedia.org/wiki/Rodrigo_Duterte)), he just ended being as mediocre as his predecessors including [NoyNoy](https://en.wikipedia.org/wiki/Benigno_Aquino_III). Duterte was supposed to be the worst according to NoyNoy/liberal supporters, but it only took a [global black swan event](https://en.wikipedia.org/wiki/COVID-19_pandemic) that brought even the most competent governments down, to experience a bad time in his presidency. Same with the new president ([BongBong Marcos](https://en.wikipedia.org/wiki/Bongbong_Marcos)), both all the outrage and hype during his run, were for naught. He ended up being a boring president.

Almost none of what the media says is important matters. Wars, new leaders, some issue far from the country. You have no influence over them. In the end, it was all just noise.

Designed to buy your attention and increase the P/E ratio of their company.

Ignore the noise, and focus on your reality

A new portal has opened, let us begin our training montage

What kind of character will you emerge at in the end?

<center>
<a href="https://www.uoguide.com/images/8/8d/Skillgump.jpg"><img src="https://www.uoguide.com/images/8/8d/Skillgump.jpg"></a>
<p>there's <a href="https://youtube.com/shorts/BHmkPFtzly4?feature=share">no better time</a> to take over</p>
</center>

---

<center>
<a href="https://xjpa-assets-2023.netlify.app/pics/bookshelf-2023-compressed.jpg"><img src="https://xjpa-assets-2023.netlify.app/pics/bookshelf-2023-compressed.jpg"></a>
</center>
