pysnowflake
===========

pysnowflake is a Python implementation of Twitter's snowflake service - https://github.com/twitter/snowflake

This is based on the pysnowflak python trift service that Erans did - https://github.com/erans/pysnowflake

Our use case wasn't thrift oriented but HTTP based, so this is a service that runs under the 
Tornado web framework.  Which makes it possible to only have one depenancy (tornado).

Due to various reasons this implementation does not reach the performance indicated in the original 
Snowflake implementation, however it is good enough in most cases and can be combined with the 
help of a software load balancer such as HAProxy to run multiple processes to get higher performance.

Installation
------------

* Install Tornado   pip install tornado==4.0.1
* Run the service

Usage
-----
usage: pysnowflake.py [--debug] [--port=9000] [--datacenter=DC_ID] [--worker=WORKER_ID]

Python based Snowflake server over HTTP


See the original snowflake server docs for a detailed description, but the bottom line is
unique numbers will insure unique identifers generated.
  WORKER_ID is the identifier for this process 
  DATACENTER_ID is the identifier for this datacenter

API (aka URLs):
----

    /id/<USERAGENT>    -- get a unique ID, <USERAGENT> is provided for metrics purposes
    /timestamp/        -- get the current timestamp for this host
    /datacenter/       -- get the data center identifier for this process
    /worker/           -- get the data center identifier for this process


Issues
------

Please report any issues via [github issues](https://github.com/koblas/pysnowflake/issues)
