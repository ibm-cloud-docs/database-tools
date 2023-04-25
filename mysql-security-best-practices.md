---

copyright:
  years: 2014, 2023
lastupdated: "2019-08-21"

keywords: mysql security

subcollection: database-tools

---

{{site.data.keyword.attribute-definition-list}}

# MySQL security best practices
{: #dbt-mysql-security}

Many {{site.data.keyword.BluSoftlayer_full}} users rely on {{site.data.keyword.mysql}} for their database solution. Because databases house various important and sensitive information, make sure to secure {{site.data.keyword.mysql}} databases to protect your information. Security practices for {{site.data.keyword.mysql}} are dependent upon individual needs and business requirements. However, you can use best practices for getting started. Make sure that you align with the following tips to get a head start in securing your {{site.data.keyword.mysql}} database.

* Set the root {{site.data.keyword.mysql}} password.
* Delete the test account and database that were created during the initial installation of {{site.data.keyword.mysql}}.
* Make sure that each individual {{site.data.keyword.mysql}} account password is set.
* Grant privileges on an as-needed basis. Avoid granting global privileges unnecessarily.
* Don't use wildcards in the hostname value that is associated with accounts.
* Periodically review an account's {{site.data.keyword.mysql}} users and databases to make sure that the permissions that are defined are valid.
* Don't use passwords in the command line with the command `shell>mysql -u root - password=somepassword mysql`

Use the following command to grant any other user with command line access to pull the password with the command `shell>ps`. Use the command `shell>mysql -u root -p mysql` to be prompted for password entry, instead. This command secures your password.
{: tip}

## More resources
{: #dbt-more-resources}

Start with the {{site.data.keyword.mysql}} security guidelines that are based on the version of {{site.data.keyword.mysql}} that is on your device:

* [{{site.data.keyword.mysql}} Version 5.7](http://dev.mysql.com/doc/refman/5.7/en/security.html){: external}

{{site.data.keyword.mysql}} has various extra resources that are not managed by {{site.data.keyword.BluSoftlayer_full}} that might be helpful. You can also find resources that are not managed by {{site.data.keyword.mysql}}. Find these resources by searching for "{{site.data.keyword.mysql}} Security" in any search engine. Because third-party resources are not maintained by the makers of {{site.data.keyword.mysql}}, use this information with caution. As with all resources, use trusted sites and refer to official documentation and support sites whenever possible.
