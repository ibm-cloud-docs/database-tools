---

copyright:
  years: 2014, 2019
lastupdated: "2018-11-15"

keywords: configure mongodb, {{site.data.keyword.mongodb}}, {{site.data.keyword.Bluemix}}

subcollection: database-tools

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}


# Configuring MongoDB networking
{: #dbt-config-mongodb}

{{site.data.keyword.Bluemix}} engineered servers with {{site.data.keyword.mongodb}} installed are configured to bind {{site.data.keyword.mongodb}} to the private network IP address. This configuration is recommended gy 10gen, and it serves to minimize the security risks of having an open, accessible {{site.data.keyword.mongodb}} instance exposed publicly upon deployment. 
{: shortdesc}

## Changing the bound interface

{{site.data.keyword.mongodb}} can be configured to bound to any interface by changing the `‘bind_ip’` attribute in the `/etc/mongod.conf` file in your installation as shown:

        # mongo.conf
        bind_ip = 0.0.0.0  

This attribute changes the binding to be on all interfaces, or you can set the specific interface's IP address in this field (available from your deployment details). A restart of the {{site.data.keyword.mongodb}} instance is required.

**Important:** Do not expose {{site.data.keyword.mongodb}} openly to public interfaces without some other security measures in place, such as firewalls or iptables that limit access to the instance.
