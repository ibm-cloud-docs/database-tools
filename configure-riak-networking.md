---

copyright:
  years: 2014, 2024
lastupdated: "2024-07-15"

keywords: configure riak, {{site.data.keyword.Bluemix}}

subcollection: database-tools

---

{{site.data.keyword.attribute-definition-list}}

# Configuring Riak networking
{: #dbt-riak-config}

When you install Riak on an {{site.data.keyword.Bluemix}} engineered server, Riak is bound to the private network IP address. Binding Riak minimizes the security risks of having an open, accessible Riak instance exposed publicly upon deployment. At any time, the IP address that is bound to Riak can be changed.
{: shortdesc}

Do not expose Riak openly to public interfaces without other security measures in place to limit external access to the instance (for example, firewalls and iptables).
{: important}

Complete the following steps to configure Riak networking to bind to a new interface.

## Binding Riak to a new interface
{: #dbt-bind-riak-new-interface}

1. Go to the `riak_core` section of the `/etc/riak/app.config` file in the installation.
1. Update the `http{}` attribute in the `riak_core` section to reflect the new IP address to which Riak is bound.
   `{http, [ {"127.0.0.1", 8098 } ] },`
1. Locate the `/etc/vm.args` file in the installation.
1. Edit the `-name` attribute within the `/etc/vm.args` file to reflect the new IP address:
   `-name riak@127.0.0.1`
1. Restart Riak to complete the binding changes.

## Next steps
{: abt-next-steps}

The changes that are made to the bind impact all previous binds to any interfaces associated with the Riak instance. After restart, the bound IP address is updated and functioning properly. If you restart the Riak instance and it does not result in a successful bind, contact [Support](/docs/get-support?topic=get-support-using-avatar).
