---
layout: post
title: Juju Big Data at Strata+Hadoop World
author: Andrew McLeod
author_url: "@andrewdmcleod"
---
<img src= 'https://cdn.rawgit.com/juju-solutions/bigdata-community/gh-pages/img/2015-strata-logo.png' width=720px>

Earlier this month, myself and Kevin &mdash; another member of the Juju big
data team &mdash; attended the 2015 Strata+Hadoop World conference in New York
City. As my first big data conference since joining the Juju team, it was an
impressive experience, both running the competition pod at our Canonical booth
and hearing speakers go over the technical and not-so-technical details of
their big data implementations.

While many of the talks were not particularly technical from an operational
perspective, the Q&A time at the end of each talk provided &mdash; as you would
expect &mdash; opportunity to dig more deeply. The Walmart talk was particularly
interesting with respect to how their culture has changed to allow employees to
more easily access and utilize their big data platform to allow quick and easy
deployment of a cluster which a user could then populate with whatever data
their particular endpoints would provide to them. This allowed people to take
their innovative ideas and test them almost immediately on real data without
having to wade through paperwork and wait for approvals. I couldn’t help but
think how useful Juju would be in this environment &mdash; not necessarily
replacing something like Ambari or Cloudera Manager, but supplementing it to
allow data scientists and other end uses to create test/production clusters
without taking time from an operations team.

All of the Netflix talks were absolutely packed, showing that big names draw
big crowds. From our perspective, it's very exciting to hear about services
that are shaping the future of big data within large organizations like Netflix
and Walmart. It gives us insight into projects that are gaining traction in the
big data world, and helps us plan future charm development to make sure we have
those offerings represented in Juju.  Spark Streaming and support of the
Parquet data format are two exciting topics for us to work on during our
upcoming development cycle. We’ll also be keeping on eye on Kudu and expanding
our ingestion endpoints with Kafka and Flume.

Attendance at our booth was consistent throughout the event. We had lots of
interest in our live demos and want to extend a big THANK YOU to our partners
for helping us showcase some of the solutions made simple with Juju:

* [DataArt](http://blog.dataart.com/stratahadoop-world-nyc-2015-reflections/)
* [France Labs](http://www.francelabs.com/en/datafari.html)
* [QuasarDB](https://www.quasardb.net/)
* [Saiku](http://www.meteorite.bi/products/saiku)
* [SpagoBI](http://www.spagobi.org/2015/09/spagobi-and-canonical-partnering-to-deliver-open-source-business-analytics-on-cloud/)

<img src= 'https://cdn.rawgit.com/juju-solutions/bigdata-community/gh-pages/img/2015-strata-juju-booth.jpg' width=720px>

Another special thanks to everyone who came over to the Canonical booth to chat
with us &mdash; it was great meeting you all. Overall, we felt that the
conference was a huge success.  We look forward to putting our new knowledge to
good use and hope you’ll join us in extending the Juju Big Data ecosystem!
