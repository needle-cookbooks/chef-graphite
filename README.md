Description
===========

Installs and configures Graphite http://graphite.wikidot.com/

Requirements
============

* Ubuntu 10.04 (Lucid) - with default settings
* Ubuntu 11.10 (Oneiric) - change node[:graphite][:python_version] to "2.7"

Attributes
==========

* `node[:graphite][:password]` sets the default password for graphite "root" user.


AMQP Attributes
===============

Values in the `node[:graphite][:carbon][:amqp]` hash control the parameters for connecting carbon to an AMQP broker.

* `node[:graphite][:carbon][:amqp][:port]`
* `node[:graphite][:carbon][:amqp][:vhost]`
* `node[:graphite][:carbon][:amqp][:user]`
* `node[:graphite][:carbon][:amqp][:password]`
* `node[:graphite][:carbon][:amqp][:metric_name_in_body]`

Usage
=====

`recipe[graphite]` should build a stand-alone Graphite installation.

`recipe[graphite::ganglia]` integrates with Ganglia. You'll want at
least one monitor node (i.e. recipe[ganglia]) node to be running
to use it.

Caveats
=======

Ships with two default schemas, stats.* (for Etsy's statsd) and a
catchall that matches anything. The catchall retains minutely data for
13 months, as in the default config. stats retains data every 10 seconds
for 6 hours, every minute for a week, and every 10 minutes for 5 years.
