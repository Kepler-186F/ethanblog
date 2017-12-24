---
layout: post
title: "Open Search Network - Visioning the next generation of internet searching"
date: 2017-11-20 11:05:00 -0800
comments: true
categories:
---
As the major internet search/indexing system, google has been around for almost a decade now. The way people search and the way indexer index hasn't change much since. Over the years, with the advancement of AI and big data, incremental improvements has been applied which contributes to better accuracy and better customization of search results. However, two fundamental issues still remains:

**Two Fundamental Issues**

First and foremost, *the trust of the quality of information.*

Let's say for Google, because their revenue model, it is already difficult for them to justify the quality of those search results, such as the rankings. There is a famous "do no evil" promise, however, after 2016 when blockchain concept become more and more popular, people start to not just satisfy with ethical promises, they learned that to get the highest level of correctness we have to have some form of *mathematical proof*. Mathematically correct is more trustworthy than Ethically correct.

Secondly, *the privacy.*

Every user asks google therefore google knows everyone. Once the centralized part of this system is compromised (by either hacker or government), it is unavoidable that user will worry about safety of their searching records.

Summing up, the this is the current searching process.
{% img /images/img/G1.jpg %}


"The Instinct"

These two issues are hard to solve, because **asking a single authority (google) is not the natural way people search for answers**.

Let's look at the bees, each bee communicate with peers, the network optimizes the transportation and processing of information as a whole. So how does people in the natural word search for answers? Let's say you want to know where to find Ethan, you go ask the friends you think are reliable. If your friends don't the answer right of the bat, they will ask their friends (like a recursion). When the answer comes back, collected and aggregated, you will rank the trust of each answers based on the *trust of the sources*, i.e., those friends. Hence the idea of "Open Search Network".

"Open Search Network"

In the next generation of searching, I envision people broadcast their question to only the direct neighbors, and they broadcast to their neighbors. All the answers this world has will be evaluated and collected based on each person's "perspective"(see below) to form an answer.

{% img /images/img/O1.jpg %}



So, for every particular topic, if we assign a number "weight" to every friends we have, we now have a system to rank the credibility of that information source. For all the future incoming answers, we will use this "weight" to adjust how much should we trust this answer. Of course we'll adjust these weights as we go, each time an answer get picked or not get picked, the corresponding source becomes more or less trustable (by a little). At the end of the day, every user under every particular topic will have a set of weights. That is called "perspective" matrix, representing the perspective of how a person view the world nearby.

In action it looks like this:
{% img /images/img/O2.jpg %}

as compare to 
{% img /images/img/G2.jpg %}

"OK, Now the implementation"
This search solution looks more like Facebook, as it is peer searcher based, i.e., a social network. Let's create something called Open Search Engine Agent, a daemon thread that broadcast and route the answers on behalf of each user. This thing can run in cloud, but not necessary, since ultimately it's owned by that user.

This will be a great open source project.
