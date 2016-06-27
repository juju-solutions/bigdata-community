---
layout: post
title: "Apache Bigtop and Juju: A Charming Approach to Big Data"
author: Cory Johns
author_url: "@johnsca"
---

Juju users have been enjoying our collection of Big Data charms for over two
years. During this time, we’ve learned a lot about what our users want from this
complex corner of big software.

<img style="float: right" src="https://insights.ubuntu.com/wp-content/uploads/15a2/pb-bigtop-300px.png" />

The [Apache Bigtop](http://bigtop.apache.org/) community distills best practices
for installing big data software. They extensively test and package Apache big
data projects to ensure users are able to manage their deployments.  This
community also provides a foundation for other projects and products to build
from.

Juju charms distill the operational intelligence needed to run big software such
as [Openstack](https://jujucharms.com/openstack),
[Kubernetes](https://jujucharms.com/observable-kubernetes), and the Bigtop stack
across clouds and architectures.  Charms provide an Open Source service-oriented
approach to sharing how complex software should be modeled.  By modeling Bigtop
with charms, we can rapidly deploy and test complex solutions at scale (and
across clouds).  These tests uncover hard problems, which leads to community
collaboration, which leads to making individual Bigtop components better.
 Bigtop charms allow operators and developers to use, test, and benchmark the
Bigtop stack on their laptops, bare metal, or favorite cloud.

Every time a Bigtop charm gets better, Bigtop also gets better - and vice versa.
Since Juju can repeatedly deploy charms on multiple clouds and architectures, it
allows us to quickly identify issues in individual components as well the
relationships to other components in the Bigtop stack.

<blockquote class="callout">
We're really excited about the combination of Juju and Bigtop. This seems good
match to me. This allows the Juju team to focus on the service orchestration
logic by leveraging the operational knowledge encapsulated in Bigtop.
<br/>
<span style="float: right">&mdash;Merlijn Sebrechts</span>
</blockquote>

Today we are thrilled to announce the Bigtop charms, bundles, and test plans
live alongside the Bigtop source!

The source layers for the charms for the Apache Hadoop component of Bigtop,
along with instructions for building the charms from these layers, can now be
found in the Apache Bigtop repository under
[bigtop-packages/src/charm](https://github.com/apache/bigtop/tree/master/bigtop-packages/src/charm).

The Bigtop repository also includes the hadoop-processing bundle, which
encapsulates how to deploy and relate these charms to get a fully-functioning,
scalable Hadoop cluster in minutes, under
[bigtop-deploy/juju/hadoop-processing](https://github.com/apache/bigtop/tree/master/bigtop-deploy/juju/hadoop-processing).

Additionally, we included a test plan for the [Cloud Weather
Report](https://github.com/juju-solutions/cloud-weather-report) project to run
the Bigtop solutions across multiple clouds and report back testing and
benchmarking results, under
[bigtop-tests/cloud-weather-report](https://github.com/apache/bigtop/tree/master/bigtop-tests/cloud-weather-report).

Jump in and submit a pull request for any of those charms or bundles. If there
is a specific workload that you would like to share with others, please mail the
[Bigtop Dev List](http://bigtop.apache.org/mail-lists.html). To see current
ideas, take a look at our [Apache Bigtop Charming Effort community
wiki](https://github.com/juju-solutions/bigdata-community/wiki/Apache-Bigtop)
and/or chime in on the in-progress [JIRA bugs][].

If you already have Juju 2 installed, give the latest Bigtop Hadoop bundle a try
with:

    juju deploy hadoop-processing

<script async src="https://assets.ubuntu.com/v1/juju-cards-v1.3.0.js"></script>
<div class="juju-card" data-id="hadoop-processing"></div>

If you’re new to Juju, follow the [getting started
instructions](https://jujucharms.com/docs/devel/getting-started) to start
developing on these Bigtop solutions. If you need help with that, we’d be happy
to walk you through the process on the [Juju mailing
list](https://lists.ubuntu.com/mailman/listinfo/juju).

For those of you looking for some face to face training, join us at the next
[Juju Charmer Summit](http://summit.juju.solutions/) September 12th-14th, 2016
in Pasadena, CA for charm development, design, and best practices. It’s free for
anyone to attend.

The Bigtop community is vibrant, collaborative, and friendly &mdash; a community we
are excited to be a part of to help make Apache big data software better!


[JIRA bugs]: https://issues.apache.org/jira/issues/?jql=project%20%3D%20BIGTOP%20AND%20reporter%20in%20(ktsakalozos%2C%20arosales%2C%20kwmonroe%2C%20AndrewMcLeod%2C%20petevg%2C%20johnsca)
