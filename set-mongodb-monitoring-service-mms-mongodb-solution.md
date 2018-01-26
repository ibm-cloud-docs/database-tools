---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}


# Setting up MongoDB Monitoring Service (MMS)

After you complete your {{site.data.keyword.mongodb}} solution, the hosts in the replica set can be set up to work with 10gen's free {{site.data.keyword.mongodb}} Monitoring Service (MMS). You can use this monitoring service to see a detailed technical analysis of the replicated database. You need the MMS API key and Secret key to get started, which is obtained by registering an account at the [10gen MMS registration website ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://www.10gen.com/mongodb-monitoring-service){: new_window}.
{:shortdesc}

**Note:** These MMS credentials might already be set up for you if you entered your MMS keys or your new MMS account information when you ordered your {{site.data.keyword.mongodb}} solution.

The MMS API key and Secret key for an account can be found at the [10gen MMS website ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://mms.10gen.com/){: new_window}. Log in using the provided credentials and select **Settings** to reveal the MMS Group's **API Key** and **Secret Key**.

## Configuring hosts

Before you configure MMS, you need to update the API key and Secret key on the hosts. **Note:** These steps only need to be performed on a single host in the set. However, the same steps can be performed on multiple hosts to enable fail-over backup MMS agents. Only one agent in a set ever communicates information to the MMS service.

1. SSH to one of the hosts in the solution (network address and credentials can be found in the {{site.data.keyword.slportal_full}}.
2. Run the following command, substituting the appropriate API and Secret keys.

    `# /opt/local/bin/mongoConfigureAuthentication.sh -a -s`

    `Updating the /opt/local/10gen/mms-agent/settings.py file with the`
    `MMS API/secret keys...`

    `Restarting MMS agent...`

    `Shutting down MMS-agent:                                   [  OK  ]`

    `Starting MMS-agent:                                        [  OK  ]`


## Configuring the MMS Group

After you configure your hosts and the MMS agents are restarted, you need to restart the MMS Group at the 10gen MMS website.

1. Log in to the [10gen MMS website ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://mms.10gen.com/){: new_window}.
2. Select **Hosts > Agents**.
3. Verify that the configured agents are in the list. One agent is listed for each that was configured and restarted.
4. To add a host to the list, select **Hosts** and click **plus (+)** .
5. Enter the *private IP address* of the host and the port number for {{site.data.keyword.mongodb}}. The default port number for SoftLayer MongoDB solutions is 27018.
6. Enter the database admin username and password, which can be found in **Passwords** for a device in the {{site.data.keyword.slportal}} and select **Add**.
  * **Important:** These credentials are mandatory.

**Note:** It can take up to 30 minutes before data shows up in MMS.
