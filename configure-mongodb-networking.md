---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-13"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Configuring MongoDB networking

## Overview

{{site.data.keyword.Bluemix}} engineered servers with {{site.data.keyword.mongodb}} installed are configured to have {{site.data.keyword.mongodb}} bound to the private network IP address. This is by the recommendation of 10gen, and it serves to minimize the security risks of having an open, accessible {{site.data.keyword.mongodb}} instance exposed publicly upon deployment. 
{:shortdesc}

## Changing the Bound Interface

{{site.data.keyword.mongodb}} can be configured to bound to any interface by changing the `‘bind_ip’` attribute in the `/etc/mongod.conf` file in your installation as shown:

        # mongo.conf
        bind_ip = 0.0.0.0  

This attribute changes the binding to be on all interfaces, or you can set the specific interface's IP address in this field (available from your deployment details). A restart of the {{site.data.keyword.mongodb}} instance is required.

**Important:** Do not expose {{site.data.keyword.mongodb}} openly to public interfaces without some other security measures in place, such as firewalls or iptables that limit access to the instance.
