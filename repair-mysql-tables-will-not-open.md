---

copyright:
  years: 2014, 2024
lastupdated: "2024-07-17"

keywords: repair mysql table

subcollection: database-tools

---

{{site.data.keyword.attribute-definition-list}}

# Repairing MySQL tables that do not open
{: #dbt-repair-mysql-table}

{{site.data.keyword.mysql}} table repair is handled on a case-by-case basis. If you are using the default {{site.data.keyword.mysql}} table type of MyISAM (which is the default storage engine unless changed or specified differently), you have the following options:

1. You can run the myisamchk utility from a command line to check, repair, or optimize tables. Run this command while the database is not running.
2. The mysqlcheck command is similar in function to myisamchk, but it can be run while the database is running.
3. If you log in to the database, you can also run SQL commands that might fix your problem.

   *mysql> optimize table `your-tablename`
   *mysql> analyze table `your-tablename`
   *mysql> repair table `your-tablename`

4. If you are getting {{site.data.keyword.mysql}} error numbers and you are not sure what they are, you can run the perror utility to look up errors from the command line. For more information, see [MySQL documentation](https://dev.mysql.com/doc/){: external}.

   *shell> perror 13 64
   *Error code 13: Permission denied
   *Error code 64: Machine is not on the network
