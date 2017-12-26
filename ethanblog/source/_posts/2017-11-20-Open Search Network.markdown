---
layout: post
title: "Open Search Network - Visioning the next generation of internet searching"
date: 2017-11-20 11:05:00 -0800
comments: true
categories:
---

***"Many do what they need, some do what they want"***  --  Alfa Romeo's commercial



Ever since Google start indexing the internet from 1998, the way people do searches hasn't change much since. (Read this paper to see how does page rank work today)
```
http://ilpubs.stanford.edu:8090/422/1/1999-66.pdf
```

{% img /images/img/G0.jpg%}

Over the years, the scale of data that allowed to be processed has been improved, along with the advancement of AI, these brought us the incremental improvements to better accuracy of search results. However, two fundamental issues still remains:

###**Two Fundamental Issues**

First and foremost, *user's trust for the quality of information.*

Let's say for Google, because their revenue model, it is already difficult to justify the quality of those search results, such as the which result should be ranked higher. Then there is a famous "do no evil" promise. However, after 2016 when blockchain concept become more and more popular (Read this famous Satoshi Nakamoto's paper),
```
https://bitcoin.org/bitcoin.pdf
```
people start to not just satisfy with ethical promises, they learned that to get the highest level of consensus, we have to reply on some form of *mathematical proof*. **Ethically correct is not enough, people want mathematically correct.**

Secondly, *the privacy.*

Every user asks google therefore google knows everyone. Once the centralized part of this system is compromised (by either a hacker or a government), it is unavoidable that user should start worry about safety of their searching records, due to a centralized system like this:
{% img /images/img/G1.jpg 400 450 %}


###**The Instinct to Solve**

These two issues are hard to solve, because **asking a single authority (google) is not the natural way people search for answers**.

Let's look at the bees, each bee communicate with peers, the network optimizes the transportation and processing of information as a whole. So how does people in the natural word search for answers? Let's say you want to know where to find Ethan, you go ask those friends you think are reliable. If your friends don't have the answer right of the bat, they will ask their friends for help, so on so forth like a recursion. When the answer comes back, the are collected and aggregated, that's when you will rank the trust of each answers based on the ***credibility of the peers***, not the ***credibility of the sources***. Hence the idea of "Open Search Network". Ultimately, the sources (like stackoverflow.com) will also become one of the peers as well, but they are just not the whole of it.

In real world, people communicate peers for information. The technology advancements enables us to be able to scan through tons of information in sub-seconds, but the bandwidth of information that a fresh human being is able to interface hasn't improve much. During thousands years of evolution, people learned to evaluate the source first then apply the trust on it moving forward. How wide is this interface.... Robin Dunbar (see this wiki) has a number to quantifies exactly this. Let's start from there.
```
https://en.wikipedia.org/wiki/Dunbar%27s_number
```


###**Open Search Network**


In the next generation of searching, I envision people broadcast their question to only the direct neighbors, and they broadcast to their neighbors. All the answers collected from the outside world will be evaluated and sent back to user the same path they fan out, weighted on each person's "perspective"(see below) to form an ranked answer.

{% img /images/img/O1.jpg %}


So, for every particular topic, if we assign a number "weight" to every friends we have, we now have a system to rank the credibility of that information source. For all the future incoming answers, we will use this "weight" to adjust how much should we trust this answer. Of course we'll adjust these weights as we go, each time an answer get picked or not get picked, the corresponding source becomes more or less trustable (by a little). At the end of the day, every user under every particular topic will have a set of weights. That is called "perspective" matrix, representing the perspective of how a person view the world nearby.

In action it looks like this:
{% img /images/img/O2.jpg %}


###Page ranking with collective filter vs OSN
Google's search reply on a set of sources, with the collective filter account for peers that may be similar, but that's still just half of OSN has. In this process, page ranking is done as the following:

{% img /images/img/f13.jpg 300 50%}

in which, R(u) is the page rank assigned, E is the array of web pages that corresponds to a source of rank.

If we let S be as follows almost any vector over Web pages (E.g., E), Then the page rank can be computed in this loop, (referred from that paper)

{% img /images/img/f14.jpg 300 300 %}

There are two observations here, for one, no information of user-user's peer is involved; and two, the rank is tagged to each source. But a source can be more fond to one user but not the others. To solve that, let's see how OSN's matrix gets updated.

Essentially, to evaluate ***how one bad answer changes one person's perspective towards that source, is a problem of partial derivative.***, hence, let's picture something like this: In ANN, how does a feedback adjust the weight matrix of network, is essentially updating the network with:

{% img /images/img/NF1.jpg 200 40%}

the change of result applies feedback to the of network, straight forward.

Fast forward to result, updating weight matrix in OSN is very alike to updating weight matrix in ANN, which described here.

{% img /images/img/NF4.jpg %}

Read this
```
http://www.cs.cornell.edu/courses/cs5740/2016sp/resources/backprop.pdf
```

Refer to this, https://github.com/aertoria/OSN, each user will have a matrix looks like below

| Topic        | neighborId     | Weight  |

| ------------- |:-------------:| -----:|
|   |   |   |
| t1      | n1 | 0.65 |
|   |   |   |
| t1      | n2      |   0.35 |
|   |   |   |
| t2 | n1      |    1.00 |

Sum(weight) for all neighborId = 1



###**Pulling off**
{% img /images/img/TM.jpg %}

This search model looks more like Facebook, as it is peer to peer searcher based, i.e., a social network. Let's create something called Open Search Engine Agent, a daemon thread that broadcast and route the answers on behalf of each user. This thing can run in cloud, but not necessary, since ultimately it's owned by that user.

Posting this idea since I want it to start as another open source project...search on.
