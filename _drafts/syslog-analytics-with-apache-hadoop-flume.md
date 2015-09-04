---
layout: post
title: Realtime Syslog Analytics
author: Kevin W. Monroe
author_url: "@kwmonroe"
---

As Cory alluded to in our [intro post][intro-post], we're excited to talk about
a bundle that truly demonstrates an end-to-end Big Data solution:
[Realtime Syslog Analytics][syslog-bundle].

<img src= 'https://cdn.rawgit.com/juju-solutions/bigdata-community/gh-pages/img/realtime-syslog-analytics.svg' width=680px>

I won't duplicate too much of the bundle's README here; you can find usage,
testing, and scaling information from the previous link. However, I think
restating some of the Introduction is important to help describe what you see
in the above image:

### Introduction
This bundle models a 9 node cluster designed to scale out. It contains the
following units:

* 1 HDFS Master
  - 1 Rsyslog Forwarder (colocated on the HDFS Master unit)
* 1 HDFS Secondary Namenode
* 1 YARN Master
* 3 Compute Slaves
* 1 Flume-HDFS
  - 1 Plugin (colocated on the Flume unit)
* 1 Flume-Syslog
* 1 Spark
 - 1 Plugin (colocated on the Spark unit)
 - 1 Zeppelin (colocated on the Spark unit)

Deploying and relating all these services is a simple one-liner:

    juju quickstart u/bigdata-dev/realtime-syslog-analytics

You can learn more about getting started with Juju and quickstart
[here][juju-getstarted]. When you're ready, read on to dive a little deeper
into the capabilities of this bundle.

### Ingestion
This bundle uses a pair of Apache Flume agents to coordinate the storing of
syslog events into Hadoop's Distributed File System (HDFS). Data flows into
our environment as follows:

* Syslog events are generated on the HDFS Master
* Rsyslog (configured on the HDFS Master) forwards these events to Flume-Syslog
* Flume-Syslog serializes these events and forwards them to Flume-HDFS
* Flume-HDFS (which is "plugged in" to our Hadoop core) writes event data to HDFS

At this point, you *could* SSH to the Flume-HDFS unit and `hdfs dfs -cat` an
event:

    juju ssh flume-syslog/0
    hdfs dfs -cat /user/flume/flume-syslog/<yy-mm-dd>/<HH>/FlumeData.<id>

But that's not very useful if you want to derive meaning from your data (e.g.:
what time of day do I get the most failed login attempts to my HDFS Master, and
where are they coming from?). For that, you'll need to execute jobs and analyze
results.

### Processing / Visualization
Once syslog data makes it to HDFS, we leverage services that can process jobs
and visualize results. The processing/visualization flow goes like this:

* Submit a Spark job
* Spark uses the YARN Master to send work to (and retrieve results from) Compute Slaves
* The Spark web interface lets you view job status and results

The "Submit a Spark job" bullet is certainly vague. You *could* SSH to the
Spark unit and manually submit a job. For example, estimate Pi with the
following:

    juju ssh spark/0
    spark-submit --class org.apache.spark.examples.SparkPi \
     --master yarn-client /usr/lib/spark/lib/spark-examples*.jar 10

But that's about as cool as using `hdfs dfs -cat` to view syslog events.

We've included another service that I haven't mentioned yet:
[Apache Zeppelin][apache-zeppelin]. It's a web-based notebook that offers a
simple way to submit jobs and interact with your data using Spark (among other
things). We provide a [sample notebook][zeppelin-tutorial] in the
[zeppelin charm][zeppelin-charm] to analyze the syslog events captured
by this bundle. If you have this deployed, see this notebook in action at
`http://<spark_unit_ip_address>:9090`.

### Conclusion
I hope this has piqued your interest in some of the cool solutions we're
offering in the Big Data corner of the Juju ecosystem. We're always interested
in the Big Data problems you're facing, so if you have question/comments about
this or any of our other [bundles][bigdata-dev-bundles], reach out to us in
`#juju` on `irc.freenode.net`.

Thanks for reading!

[intro-post]: http://bigdata.juju.solutions/2015-08-31-new-blog/
[syslog-bundle]: https://jujucharms.com/u/bigdata-dev/realtime-syslog-analytics/
[juju-getstarted]: https://jujucharms.com/get-started
[apache-zeppelin]: https://zeppelin.apache.org/
[zeppelin-tutorial]: http://bazaar.launchpad.net/~bigdata-dev/charms/trusty/apache-zeppelin/trunk/view/head:/resources/flume-tutorial/note.json
[zeppelin-charm]: https://jujucharms.com/apache-zeppelin/trusty
[bigdata-dev-bundles]: https://jujucharms.com/u/bigdata-dev/#bundles
