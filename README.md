TODO:
- Development workflows
- beef up code:
  - Links to current development
- Roadmap (project plans, blueprints, etc.)
- How to get involved (features, paper cuts, etc.)

# Juju Big Data community

## Intro

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

### Juju big data library

### Charms
Charms are the core of our development. Each charm models a particular big
data service (e.g.: the HDFS Master, Apache Flume, Hue, etc). Most of our
charm development is in Python and makes use of the Juju big data library
mentioned above. While somewhat helpful as a method to install a service,
charms really shine when related to others. We'll talk more about that when
we discuss bundles below, but first, here are the services we've got charmed:

 * apache-flume-hdfs
 * apache-flume-syslog
 * apache-flume-twitter
 * apache-hadoop-client
 * apache-hadoop-compute-slave
 * apache-hadoop-hdfs-master
 * apache-hadoop-hdfs-secondary
 * apache-hadoop-plugin
 * apache-hadoop-yarn-master
 * apache-hive
 * apache-hue
 * apache-pig
 * apache-spark
 * apache-spark-notebook
 * apache-zeppelin

### Bundles
Bundles are groups of charms that model a solution. We've come up with a few
that we think the big data community will find useful right away:

 * apache-core-batch-processing
 * apache-hadoop-spark
   - apache-hadoop-spark-notebook
   - apache-hadoop-spark-zeppelin
 * apache-analytics-sql
 * apache-analytics-pig
 * apache-ingestion-flume


## Contributors

* Amir Sanjar (asanjar)
* Cory Johns (cory_fu)
* Kevin Monroe (kwmonroe)


## Contact

* bigdata-dev@lists.launchpad.net
* \#juju on freenode
