---

copyright:
  years: 2014, 2024
lastupdated: "2024-07-25"

keywords: mysql faq

subcollection: database-tools

---

{{site.data.keyword.attribute-definition-list}}

# FAQs: MySQL
{: #dbt-faq-mysql}

## How can I monitor my MySQL server?
{: faq}

`mytop`, a Linux application, is a near-time monitor (similar to the UNIX utility `top`) that specifically looks at what the {{site.data.keyword.mysql}} server is doing. `mytop` updates every few seconds so you can get a reasonable look at your SQL performance. `mytop` is also capable of displaying a huge amount of information. It also assumes that you're connecting to the {{site.data.keyword.mysql}} server on localhost with the root user and no password. Credentials can be changed either in the script itself or on the command line.

## What is my root password for MySQL?
{: faq}

* If the server was auto-provisioned with {{site.data.keyword.mysql}}, the root password is the same as the server root password.
* If Plesk is auto-provisioned on your server, use "admin" and the admin password for Plesk.
* If you installed {{site.data.keyword.mysql}} through source, Rational Portfolio Manager, or up2date, then the initial root account passwords are empty. Anyone can connect to the {{site.data.keyword.mysql}} server as root without a password and be granted all privileges, unless you set the root password during or after the {{site.data.keyword.mysql}} installation.

## What is the best online resource for information about MySQL?
{: faq}

The [{{site.data.keyword.mysql}} website ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://dev.mysql.com/doc/){: new_window} has a complete reference manual with available search capabilities.
