---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# MySQL security best practices

Many {{site.data.keyword.BluSoftlayer_full}} users rely on {{site.data.keyword.mysql}} for their database solution. Because databases house various important and, at times, sensitive information, make sure to secure {{site.data.keyword.mysql}} databases to protect your information. Security practices for {{site.data.keyword.mysql}} are dependent upon individual needs and business requirements; however, there are best practices that are recommended to get started. Make sure that you align with the following tips to get a head start in securing your {{site.data.keyword.mysql}} database.

* Set the root {{site.data.keyword.mysql}} password.
* Delete the test account and database that were created during the initial installation of {{site.data.keyword.mysql}}.
* Make sure that each individual {{site.data.keyword.mysql}} account password is set.
* Grant privileges on an as-needed basis. Avoid granting global privileges unnecessarily.
* Don't use wildcards in the hostname value that is associated with accounts.
* Periodically review an account's {{site.data.keyword.mysql}} users and databases to make sure that permissions remain accurate.
* Don't use passwords in the command line with the command `shell>mysql -u root - password=somepassword mysql`

**Note:** Use the following command to grant any other user with command line access to pull the password with the command `shell>ps`. Use the command `shell>mysql -u root -p mysql` to be prompted for password entry, instead. This secures your password.

## Additional Resources

There are various resources that provide more details about securing your {{site.data.keyword.mysql}} database. Start with the {{site.data.keyword.mysql}} security guidelines that are based on the version of {{site.data.keyword.mysql}} that is on your device:

* [{{site.data.keyword.mysql}} Version 5.7 ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://dev.mysql.com/doc/refman/5.7/en/security.html){: new_window}

There are various extra resources that are not managed by {{site.data.keyword.mysql}} that might be of assistance. These resources are found by searching for "{{site.data.keyword.mysql}} Security" by using any search engine. Because third-party resources are not maintained by the makers of {{site.data.keyword.mysql}}, perform these practices with caution. As with all resources, use trusted sites and refer to official documentation and support sites whenever possible.
