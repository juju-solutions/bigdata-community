---
layout: post
title: Realtime Syslog Analytics
author: Kevin W. Monroe
author_url: "@kwmonroe"
---

As Cory alluded to in our [intro post][intro-post], we're excited to talk about
a bundle that truly demonstrates an end-to-end Big Data solution:
[Realtime Syslog Analytics][syslog-bundle].

<img src= 'https://cdn.rawgit.com/juju-solutions/bigdata-community/gh-pages/img/realtime-syslog-analytics.svg' width=640px>

This bundle models a 9 node cluster designed to scale out. Built around [Apache
Hadoop][apache-hadoop] components, it contains the following units:

* 1 HDFS Master
  - 1 Rsyslog Forwarder (colocated on the HDFS Master)
* 1 HDFS Secondary Namenode
* 1 YARN Master
* 3 Compute Slaves
* 1 Flume-HDFS
  - 1 Plugin (colocated on the Flume unit)
* 1 Flume-Syslog
* 1 Spark
 - 1 Plugin (colocated on the Spark unit)
 - 1 Zeppelin (colocated on the Spark unit)

Syslog events generated on the HDFS Master unit are forwarded to the
`apache-flume-syslog` charm. These events are serialized and sent to the
`apache-flume-hdfs` charm to be stored in HDFS. We have included a sample
application to analyze these events with Spark/Zeppelin.

[intro-post]: http://bigdata.juju.solutions/2015-08-31-new-blog/
[syslog-bundle]: https://jujucharms.com/realtime-syslog-analytics/
[apache-hadoop]: https://hadoop.apache.org/
