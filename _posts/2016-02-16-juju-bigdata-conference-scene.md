---
layout: post
title: Juju Big Data hits the conference scene
---

Though only a few weeks into 2016, the Juju Big Data team has already been busy
engaging diverse communities at conferences and meetups.  We'd like to share
our perspective on a few of those engagements here.


### SCaLE 14x / UbuCon, Jan 20-24, Pasadena

This year's [Southern California Linux Expo](https://www.socallinuxexpo.org/scale/14x)
was especially exciting as it also hosted [UbuCon](http://ubucon.org/) and
[DevOps Days LA](http://www.devopsdays.org/). This meant we had the chance to
speak with a wide range of attendees, from
casual users to hard core developers, all under one roof.

Jorge Castro and Kevin Monroe gave a talk about complexities in Big Data
environments and how Juju helps simplify them.  There were ~40 audience members
that watched us deploy our syslog analytics bundle live on an OrangeBox in
about 20 minutes.  We've written about this bundle
[before](http://bigdata.juju.solutions/2015-09-22-syslog-analytics-with-apache-hadoop-flume),
but talking through it on stage was really well received.  The audience had
tons of great questions about Juju and MAAS &mdash; luckily we had Marco Ceppi
there to field all the hard ones ;)  The talk was recorded if you're interested:

[![Juju Big Data at SCaLE](http://img.youtube.com/vi/nksi_tf2xRk/0.jpg)](https://www.youtube.com/watch?v=nksi_tf2xRk&t=4m15s)

Outside of our formal talk, we had plenty of great hallway chats.  I think one
in particular sums up why we're so excited to do what we do:  We met a
community member that is learning R and is interested in running Big Data jobs
with SparkR, but has *zero* interest in setting up or configuring Hadoop.  This
almost led him to give up on Big Data, but he decided to come to SCaLE to see
if anyone had this figured out.  We pitched Juju and our Big Data offerings on
Thursday night, and he was so intrigued that he wanted us to block out some
time so we could put Juju on his laptop.  Marco set him up with
[free AWS creds](http://developer.juju.solutions), and Kevin walked him through
deployment of an HDFS/Spark/Zeppelin bundle.  In under an hour, he was running
Spark jobs in his own Big Data AWS environment.  He was blown away and asked if
it would be ok if he extended our Spark charm to support SparkR.  Awesome.

This week wasn't just about preaching for us.  We had lots of opportunity to
learn from other players in the Big Data space.  During the DevOps Days open
spaces event, we heard from people implementing the
[Lambda architecture](https://en.wikipedia.org/wiki/Lambda_architecture) and
walked away with ideas on how we can offer speed, batch, and serving layers in
our bundles.  We also heard about testing methodologies that go beyond typical
function/integration tests.  Behavioral testing &mdash; the notion of verifying
your model behaves consistently over time &mdash; was particularly interesting.
This bleeds into hotspot detection, where you identify hardware, software, or
data anomalies that may be affecting your model's behavior.  This is really
cool stuff that we can't wait to build into our offerings!

While we love talking about our own stuff, we are equally excited to hear from
Big Data enthusiasts large and small.  The community around Big Data is
thriving, and we're happy to play a role in it.  Hopefully, we'll see you at
SCaLE for many years to come!


### cfgmgmtcamp & Juju Charmer Summit, Feb 1-5, Ghent

Mark Shuttleworth kicked off the 2016 "Config Management Camp" with what was
almost an impromptu demo deploying OpenStack on an OrangeBox, which went over
well and helped get more people into the Juju track rooms later in the week.
The Canonical employees taking up space had to make way for curious attendees,
and we were all very pleased with the turnout. The Big Data session was no
exception; a packed room, a great
[presentation](https://docs.google.com/presentation/d/1nyD_XsyDBymaD5oOlKbZcjLjppGPiKLUH_p6jpjLeWc/)
(although we may be biased) and numerous well thought out questions. Tom Barber
from meteorite.bi (who had [some](http://www.meteorite.bi/blog/142)
[excellent](http://www.meteorite.bi/blog/143)
[thoughts](http://www.meteorite.bi/blog/144) on the event) wanted to know if we
had any plans to couple with popular, fast moving projects, such as
[Apache Zeppelin](https://zeppelin.incubator.apache.org/).
Luckily, Alexander Bezzubov, sitting next to him, raised his hand and replied:
"I'm the release manager for Zeppelin, and yes, we're working on it."

<img src="/img/2016-ghent-cory-kevin-mark.jpg" width="720px" />

Our live demo was &mdash; we thought &mdash; pretty cool, this time validated
by feedback from the audience. When the presentation began we asked people to
SSH into our primary Hadoop NameNode with "Funny Usernames (no profanity
please)" to generate "access denied" syslog messages. These would be sent to
HDFS by Apache Flume to demonstrate the ingestion and storage capabilities of
our Big Data charms and subsequently processed with Apache Spark to count words.
The result of all of this calculation would be displayed graphically
(beautifully) with Apache Zeppelin. What we hadn't counted on was that we had a
room full of computer-type-people who knew how to write for-loops and after a
few minutes we noticed we had more than a few login attempts:

<img src="/img/2016-ghent-demo-count.png" width="720px" />

By the end of the session we had somewhere around 30,000 login attempts, and a
screenshot from Zeppelin looked something like this:

<img src="/img/2016-ghent-demo-names.png" width="720px" />

While the weather in Ghent wasn't warm or sunny, the faces of our attendees
were, and we were ecstatic to share the experience with them.
