---
layout: post
title: Now You're Charming with Layers
author: Cory Johns
author_url: "@johnsca"
---
<img src="/img/layers.png" />

Charming with layers is a relatively new approach to writing charms that we,
as the Juju community, are begining to use.  The idea is to allow better
re-use of common code in charms, more well-defined and consistent implementations
of interface protocols, and generally allow charm authors to focus on the
parts of the charm that is most relevant to their charm and leverage the
community for everything else.

Charming with layers is starting to gain momentum.  We're seeing new interface
and base layers being added to [interfaces.juju.solutions][] (which can be done
by anyone with a Launchpad ID), we've had discussions on creating a standardized
Java interface layer for providing JREs or JDKs, and I've been working this week
on creating interface layers for the Apache Hadoop big data charms to make it
easier to connect to those charms and to enable us to restructure the core
Hadoop charms using layers to make them easier to understand and maintain.  So I
thought that it would be a good time to write up a short explanation about what
the different types of charm layers are, what I think belongs in them, and how
they can be used to make writing charms a much more pleasant experience.


## Types of Layers

There are three major categories of charm layers:

  * Base, or runtime layers
  * Interface layers
  * Charm layers

Each of these has a distinct role, and it's important to understand how a charm
should be broken up into these types of layers.  Generally, a charm will contain
one base layer, one charm layer, and one or more interface layers, but it is
possible that a charm might include more than one base layer, as well.


## Base, or Runtime, Layers

Base layers are layers that other charms can be built on.  They contain things
that are common to many different charms, and allow charms to reuse that
commonality without having to reimplement it each time.  Base layers typically
are not sufficient on their own to be considered a charm; they likely can't be
built into a deployable charm, and if they can, they're unlikely to do anything
useful.  However, other than how they're used, there's nothing inherent that
distinguishes base layers from charm layers.  It is possible for a fully working
charm to be written to also be used as a base for other charms, if that use-case
makes sense for the charm.  It should also be noted that it is common for a base
layer to build on another base layer, especially [layer-basic][].

The most basic example is just that, [layer-basic][].  It provides nothing more
than the minimum needed to effectively use layered charms: [charms.reactive][],
[charmhelpers][], and the skeleton hook implementations that call into the
reactive framework.  However, the most useful base layers are actually a type
of runtime layer.  For example, [layer-apache-php][] provides Apache2 and
mod-php, as well as mechanisms for fetching and installing a PHP project within
that runtime.

Base layers can be written in any language, but must at a minimum provide the
reactive framework that glues layers together, which is written in Python.
This can be done trivially by building the base layer off of [layer-basic][].


## Interface Layers

Interface layers are perhaps the most confusing type of layer, and are
responsible for the communication that transpires over a relation between two
services.  This type of layer encapsulates a single "interface protocol" and is
generally written and maintained by the author of the primary charm that
provides that interface.  However, it does cover both sides (provides and
requires) of the relation and turns the two-way key-value store that are Juju
relations under-the-hood into a full-fledged API for interacting with charms
supporting that interface.

It is important to note that interface layers **do not** actually **implement**
either side of the relation.  Instead, they are solely responsible for
the **communication** that goes on over the relation, relying on charms on
either end to decide what to do with the results of that communication.

A concrete example would be the [interface-hadoop-plugin][] layer for the big
data charm ecosystem.  It manages the communication between the
[apache-hadoop-plugin][] charm, and any charm that would want to use the plugin
to connect to the core Hadoop cluster.  Note that it does not implement the
plugin functionality, it just manages the the API that is exposed by the plugin
to the charm using it.

As another example, there is work in progress to define a JRE or JDK interface
that would standardize how a charm could provide a JRE to another service and
make it easy to choose which vendor's version of Java that service uses.  (This
would make it easy to use a version of Java tailored to the specific hardware
you happen to be deploying on, for instance.)  The various JRE or JDK charms,
such as [Zulu8][] or [IBMJavaSDK][], would then provide the `java` relation
interface, and various charms, such as [Tomcat][] or [WebSphere-Liberty][],
would require it.

The `interface-java` layer would not actually install or configure Java,
nor would it manage Tomcat or WebSphere.  What it would do is provide a
consistent API (through [reactive][charms.reactive] states) that would inform
the Tomcat or WebSphere charms when a JRE has been attached and provide methods
that can be called to send configuration options back to the charm providing
Java, as well as an API for the Java charms to receive those configuration
options and methods for them to send back relevant information.

Interface layers currently must be written in Python and extend the [ReactiveBase][]
class, though they can then be used by any language using the built-in CLI
API.


## Charm Layers

Building on base and interface layers, charm layers are what actually get turned
into charms.  This is where the core logic of the charm should go, the logic
specific to that individual charm.  This layer brings together all the pieces
needed to create the charm.  It is where most of the charm's config options
will be defined, and where the reactive handlers that do the specific work of
the charm will go.  It will need to contain the charm's README, copyright, icon,
and so on.

Charm layers should be the most common type of layer, and is what most charm
authors will be dealing with.  However, the goal is to keep them hyper-focused
on just that specific charm's logic and needs, and to push any commonality into
an appropriate base layer.  Charm layers should contain as little boilerplate
as possible.

Charm layers can be written in any language, and there are [helpers][reactive-bash]
for writing them in Bash.



[interfaces.juju.solutions]: http://interfaces.juju.solutions/
[charmhelpers]: https://pythonhosted.org/charmhelpers/
[charms.reactive]: https://pythonhosted.org/charms.reactive/
[layer-basic]: https://github.com/juju-solutions/reactive-base-layer
[layer-apache-php]: https://github.com/johnsca/apache-php
[interface-hadoop-plugin]: https://github.com/juju-solutions/interface-hadoop-plugin
[apache-hadoop-plugin]: https://jujucharms.com/apache-hadoop-plugin/
[Zulu8]: https://jujucharms.com/zulu8/
[IBMJavaSDK]: https://jujucharms.com/u/ibmcharmers/ibmjavasdk/
[Tomcat]: https://jujucharms.com/tomcat/
[WebSphere-Liberty]: https://jujucharms.com/websphere-liberty/
[ReactiveBase]: https://pythonhosted.org/charms.reactive/charms.reactive.relations.html#charms.reactive.relations.RelationBase
[reactive-bash]: https://pythonhosted.org/charms.reactive/#non-python-reactive-handlers
