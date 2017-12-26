---
layout: post
title: "How to design a time machine to predict future"
date: 2016-10-23 12:23:00 -0800
comments: true
categories:
---
This post is a draft of something I want to build, a time machine, a system allows information to traverse through time.

{% img /images/img/t.jpg %}
##"The Problem"

This is how this idea gets started: in my day-to-day job, we deal with lots of application servers and database servers. At the center of it, here is the gist: the connection between app server and db server is critical because it directly impacts customer. However, the request that comes down from an app server, due to all sorts of unpredictable reasons, often ends up not reaching the db end. Some times they just got lost, some times they got abandoned.

So we have a whole team to study how can we minimize these cases. The traditional approach is by gathering the knowledge from the past outages, to build a model so we can predict future... straight forward. If in the past ten incidents, every time incident started we first observed a high CPU usage. Therefore, next time if someone saw another CPU usage peak, it's intuitive to predict the system is likely gonna broke soon.

But how about solve this problem in a different way: can we design a system to in general predict future, like a time machine?

Wait, a time machine?

With this in mind, please read on. So this is a plan: to use the quantum physics help us predict the connectivity between app server and db server..

First, this is the link of Double Slit Experiment. Strongly recommend this video if you haven't read it.
```
https://www.youtube.com/watch?v=DfPeprQ7oGc
```
The take away of first video is the following: "the particle changes its behavior simply because of 'aware' of being watched"

Next, this one:
```
https://www.youtube.com/watch?v=H6HLjpj4Nt4
```
The take away of the second video is, "the particle can predict what would have happened in the future, and travel back in time to decide to behave accordingly."

So to sum up, below is a prototype of the system, and has been proved will be functioning, as quoted from this third video(https://www.youtube.com/watch?v=DsxA7OU7fR0)


##"The Design"

First we have a particle gun, shooting electrons(or photons) through a double-slit barrier and landing on a screen. Both screen and each slit will have a detector connecting to a computer. The detectors attached at each slit will stay on at all time. And their data is constantly being collected by a computer. As in initial state, the screen will show a two-bands, because observer knowledge is collected constantly being collected.

Now, if we leave detectors stay on, but disconnect the cable between the detectors and the computer end, the screen will show a interference pattern. This because no observation knowledge will be successfully collected.

If we think about this for a sec: because the time takes for particle to travel from the slits to screen is almost simultaneous, however the time takes for data to transmit from slit detector to computer is usually much longer, this creates a future-prediction mechanism I can take advantage of: I will read the result from screen, to predict if the ongoing detector data would have or would have not end up at computer end, even thought the detector data bits may be still in the middle of being transmitted!

{% img /images/img/m1.jpg %}

##"An Application"

Detector reading is the end that will be carried by our application. Those bits will be packaged into small units, attached with each AppServer-To-DbServer-Request. If customers request can successfully reach the destination, so does the predictor bits. Therefore we should have reading a double-band on screen long before. And vice versa, if the screen starts showing a interference pattern, we will know for sure that soon the connection will broke somewhere, guaranteed.

{% img /images/img/m2.jpg %}
