---

copyright:
  years: 2014, 2024
lastupdated: "2024-07-15"

keywords: configure mongodb, {{site.data.keyword.mongodb}}, {{site.data.keyword.Bluemix}}

subcollection: database-tools

---

{{site.data.keyword.attribute-definition-list}}

# Configuring MongoDB networking
{: #dbt-config-mongodb}

{{site.data.keyword.Bluemix}} engineered servers with {{site.data.keyword.mongodb}} installed are configured to bind {{site.data.keyword.mongodb}} to the private network IP address. This configuration is recommended gy 10gen, and it serves to minimize the security risks of having an open, accessible {{site.data.keyword.mongodb}} instance exposed publicly upon deployment.
{: shortdesc}

## Changing the bound interface
{: #dbt-change-bound-interface}

{{site.data.keyword.mongodb}} can be configured to bound to any interface by changing the `‘bind_ip’` attribute in the `/etc/mongod.conf` file in your installation as shown:

```
        # mongo.conf
        bind_ip = 0.0.0.0
```
{: code}

This attribute changes the binding to be on all interfaces, or you can set the specific interface's IP address in this field (available from your deployment details). A restart of the {{site.data.keyword.mongodb}} instance is required.

Do not expose {{site.data.keyword.mongodb}} openly to public interfaces without some other security measures in place, such as firewalls or iptables that limit access to the instance.
{: important}
