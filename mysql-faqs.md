---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-27"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# FAQs: MySQL

## How can I monitor my MySQL server?

_mytop_, a handy little Linux application is a near-time monitor (similar to the UNIX utility 'top') that specifically looks at what the {{site.data.keyword.mysql}} server is doing. _mytop_ updates every few seconds so you can get a reasonable look at your SQL performance. _mytop_ is also capable of displaying a huge amount of information. It also assumes that you're connecting to the {{site.data.keyword.mysql}} server on localhost with the root user and no password. Credentials can be changed either in the script itself or on the command line.

## What is my root password for MySQL?

* If the server was auto-provisioned with {{site.data.keyword.mysql}}, the root password is the same as the server root password.
* If Plesk is auto-provisioned on your server, use "admin" and the admin password for Plesk.
* If you installed {{site.data.keyword.mysql}} through source, RPM, or up2date, then the initial root account passwords are empty. Anyone can connect to the {{site.data.keyword.mysql}} server as root without a password and be granted all privileges, unless you set the root password during or after the {{site.data.keyword.mysql}} installation.

## What is the best online resource for information about MySQL?

The [{{site.data.keyword.mysql}} website ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://dev.mysql.com/doc/){: new_window} has a complete reference manual with available search capabilities.

The documentation covers everything from basic installation, SQL syntax, to advanced usage like replication and clustering. Additionally, there are translations of the reference manual in German, French, Japanese, Portuguese, and Russian.
