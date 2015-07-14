TODO:
- add charm/bundle oneliner descriptions
- link to design docs
- Roadmap (project plans, blueprints, etc.)
- How to get involved (features, paper cuts, etc.)

# Juju Big Data community

When exploring big data solutions, one of the most daunting tasks users face is
the setup and configuration of these usually complex environments. This can take
from hours to days; time you could spend testing, evaluating, and putting your
big data solutions to good use.

The mission of the Juju big data team is to offer a simple and repeatable
method for deploying big data environments. We've created a "pluggable" model
using Juju charms and bundles to let users focus on the fun part (actually
solving big data problems) without worrying about the intricacies of configuring
core Hadoop services.

This repo serves as our hub for talking about the work we're doing. We'll show
off solutions that provide a solid foundation for interfacing with Hadoop, as
well as extensions to that foundation that make for totally awesome demos.

You'll also find the regular stuff here:  how to contact us and (more
importantly) how to dig in and get involved!


## Code

We have three main focus areas for development. First, we have a library
to help with tasks that are commonly needed when doing big data development.
Next are the Juju charms that model individual big data services. Finally,
we have pre-canned solutions in the form of bundles that tie charms together
for simple and repeatable deployment.

Where useful, we've included a DEV-README.md in our repositories. That
document is meant to guide users interested in extending our generic offerings
for more specific uses. We'll point out the repository locations and
these development documents as we get into the details of our focus areas
below.

### Juju big data library
The `jujubigdata` Python library is an collection of functions and classes for
simplifying the development of big data applications. This includes things like
synchronizing /etc/hosts across a cluster, configuring core-site.xml,
interacting with Hadoop, etc.

 * [repo](https://github.com/juju-solutions/jujubigdata)
 * [issue tracker](https://github.com/juju-solutions/jujubigdata/issues)

### Charms
Charms are at the heart of our development. Each charm models a particular big
data service (e.g.: the HDFS Master, Apache Flume, Hue, etc). Most of our
charm development is in Python and makes use of the Juju big data library
mentioned above.

While somewhat helpful as a method to install a service, charms really shine
when you relate them to other services. We'll talk more about that when
we discuss bundles below, but first, here are our current charms:

 * apache-flume-hdfs \[[dev repo](https://code.launchpad.net/~bigdata-dev/charms/trusty/apache-flume-hdfs/trunk) |
 [dev charm](https://jujucharms.com/u/bigdata-dev/apache-flume-hdfs)\]

 * apache-flume-syslog \[[dev repo](https://code.launchpad.net/~bigdata-dev/charms/trusty/apache-flume-syslog/trunk) |
 [dev charm](https://jujucharms.com/u/bigdata-dev/apache-flume-syslog)\]

 * apache-flume-twitter \[[dev repo](https://code.launchpad.net/~bigdata-dev/charms/trusty/apache-flume-twitter/trunk) |
 [dev charm](https://jujucharms.com/u/bigdata-dev/apache-flume-twitter)\]

 * apache-hadoop-client \[[dev repo](https://code.launchpad.net/~bigdata-dev/charms/trusty/apache-hadoop-client/trunk) |
 [dev charm](https://jujucharms.com/u/bigdata-dev/apache-hadoop-client) |
 [stable repo](https://code.launchpad.net/~bigdata-charmers/charms/trusty/apache-hadoop-client/trunk) |
 [stable charm](https://jujucharms.com/apache-hadoop-client)\]

 * apache-hadoop-compute-slave \[[dev repo](https://code.launchpad.net/~bigdata-dev/charms/trusty/apache-hadoop-compute-slave/trunk) |
 [dev charm](https://jujucharms.com/u/bigdata-dev/apache-hadoop-compute-slave) |
 [stable repo](https://code.launchpad.net/~bigdata-charmers/charms/trusty/apache-hadoop-compute-slave/trunk) |
 [stable charm](https://jujucharms.com/apache-hadoop-compute-slave)\]
   - [DEV-README](http://bazaar.launchpad.net/~bigdata-dev/charms/trusty/apache-hadoop-compute-slave/trunk/view/head:/DEV-README.md)

 * apache-hadoop-hdfs-master \[[dev repo](https://code.launchpad.net/~bigdata-dev/charms/trusty/apache-hadoop-hdfs-master/trunk) |
 [dev charm](https://jujucharms.com/u/bigdata-dev/apache-hadoop-hdfs-master) |
 [stable repo](https://code.launchpad.net/~bigdata-charmers/charms/trusty/apache-hadoop-hdfs-master/trunk) |
 [stable charm](https://jujucharms.com/apache-hadoop-hdfs-master)\]
   - [DEV-README](http://bazaar.launchpad.net/~bigdata-dev/charms/trusty/apache-hadoop-hdfs-master/trunk/view/head:/DEV-README.md)

 * apache-hadoop-hdfs-secondary \[[dev repo](https://code.launchpad.net/~bigdata-dev/charms/trusty/apache-hadoop-hdfs-secondary/trunk) |
 [dev charm](https://jujucharms.com/u/bigdata-dev/apache-hadoop-hdfs-secondary) |
 [stable repo](https://code.launchpad.net/~bigdata-charmers/charms/trusty/apache-hadoop-hdfs-secondary/trunk) |
 [stable charm](https://jujucharms.com/apache-hadoop-hdfs-secondary)\]
   - [DEV-README](http://bazaar.launchpad.net/~bigdata-dev/charms/trusty/apache-hadoop-hdfs-secondary/trunk/view/head:/DEV-README.md)

 * apache-hadoop-plugin \[[dev repo](https://code.launchpad.net/~bigdata-dev/charms/trusty/apache-hadoop-plugin/trunk) |
 [dev charm](https://jujucharms.com/u/bigdata-dev/apache-hadoop-plugin) |
 [stable repo](https://code.launchpad.net/~bigdata-charmers/charms/trusty/apache-hadoop-plugin/trunk) |
 [stable charm](https://jujucharms.com/apache-hadoop-plugin)
   - [DEV-README](http://bazaar.launchpad.net/~bigdata-dev/charms/trusty/apache-hadoop-plugin/trunk/view/head:/DEV-README.md)

 * apache-hadoop-yarn-master \[[dev repo](https://code.launchpad.net/~bigdata-dev/charms/trusty/apache-hadoop-yarn-master/trunk) |
 [dev charm](https://jujucharms.com/u/bigdata-dev/apache-hadoop-yarn-master) |
 [stable repo](https://code.launchpad.net/~bigdata-charmers/charms/trusty/apache-hadoop-yarn-master/trunk) |
 [stable charm](https://jujucharms.com/apache-hadoop-yarn-master)\]
   - [DEV-README](http://bazaar.launchpad.net/~bigdata-dev/charms/trusty/apache-hadoop-yarn-master/trunk/view/head:/DEV-README.md)

 * apache-hive \[[dev repo](https://code.launchpad.net/~bigdata-dev/charms/trusty/apache-hive/trunk) |
 [dev charm](https://jujucharms.com/u/bigdata-dev/apache-hive) |
 [stable repo](https://code.launchpad.net/~bigdata-charmers/charms/trusty/apache-hive/trunk) |
 [stable charm](https://jujucharms.com/apache-hive)\]

 * apache-pig \[[dev repo](https://code.launchpad.net/~bigdata-dev/charms/trusty/apache-pig/trunk) |
 [dev charm](https://jujucharms.com/u/bigdata-dev/apache-pig) |
 [stable repo](https://code.launchpad.net/~bigdata-charmers/charms/trusty/apache-pig/trunk) |
 [stable charm](https://jujucharms.com/apache-pig)\]

 * apache-spark \[[dev repo](https://code.launchpad.net/~bigdata-dev/charms/trusty/apache-spark/trunk) |
 [dev charm](https://jujucharms.com/u/bigdata-dev/apache-spark) |
 [stable repo](https://code.launchpad.net/~bigdata-charmers/charms/trusty/apache-spark/trunk) |
 [stable charm](https://jujucharms.com/apache-spark)\]

 * apache-spark-notebook \[[dev repo](https://code.launchpad.net/~bigdata-dev/charms/trusty/apache-spark-notebook/trunk) |
 [dev charm](https://jujucharms.com/u/bigdata-dev/apache-spark-notebook)\]

 * apache-zeppelin \[[dev repo](https://code.launchpad.net/~bigdata-dev/charms/trusty/apache-zeppelin/trunk) |
 [dev charm](https://jujucharms.com/u/bigdata-dev/apache-zeppelin) |
 [stable repo](https://code.launchpad.net/~bigdata-charmers/charms/trusty/apache-zeppelin/trunk) |
 [stable charm](https://jujucharms.com/apache-zeppelin)\]

### Bundles
Bundles are groups of charms that model a solution. We've come up with a few
that we think the big data community will find useful right away:

 * apache-core-batch-processing \[[dev bundle](https://jujucharms.com/u/bigdata-dev/apache-core-batch-processing) |
 [stable bundle](https://jujucharms.com/apache-core-batch-processing)\]

 * apache-hadoop-spark \[[dev bundle](https://jujucharms.com/u/bigdata-dev/apache-hadoop-spark)\]
   - apache-hadoop-spark-notebook \[[dev bundle](https://jujucharms.com/u/bigdata-dev/apache-hadoop-spark-notebook)\]
   - apache-hadoop-spark-zeppelin \[[dev bundle](https://jujucharms.com/u/bigdata-dev/apache-hadoop-spark-zeppelin)\]

 * apache-analytics-sql \[[dev bundle](https://jujucharms.com/u/bigdata-dev/apache-analytics-sql)\]

 * apache-analytics-pig \[[dev bundle](https://jujucharms.com/u/bigdata-dev/apache-analytics-pig)\]

 * apache-ingestion-flume \[[dev bundle](https://jujucharms.com/u/bigdata-dev/apache-ingestion-flume)\]


## Media

We have a few presentations, videos, and other bits of media that may be
helpful if you want to see what we're all about.

 * [Ubuntu Online Summit, 04/2015](http://summit.ubuntu.com/uos-1505/meeting/22428/deploying-big-data-workloads-with-juju/)


## Contributors

* @[asanjar](https://github.com/asanjar) \[[email](mailto:amir.sanjar@canonical.com)\]
* @[johnsca](https://github.com/johnsca) \[[email](mailto:cory.johns@canonical.com)\]
* @[kwmonroe](https://github.com/kwmonroe) \[[email](mailto:kevin.monroe@canonical.com)\]


## Contact

You can find us in `#juju` on `irc.freenode.net`, or feel free to email our list
at <bigdata-dev@lists.launchpad.net>. We look forward to hearing from you!
