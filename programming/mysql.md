---
description: Anything related to MySQL.
---

# MySQL

## Backup everything including master data

Hvis databasen er blandet myisam og innodb så må du låse databasen først, da fungerer ikke --single-transaction.

```bash
mysqldump -uroot -p --all-databases --routines --flush-privileges --triggers --events --master-data=1 --quick | gzip -1 > ./dbbackup.sql.gz;
```

## Restore

```bash
mysql -uroot -p < /mnt/backupdrive/dbbackup.sql.gz;
```

## Ikke bruk Stored Procedures eller Functions med mindre det sparer nettverkstrafikk

En stored procedure er tregere. At serveren optimaliserer er en myte.

Kode er vanskeligere å vedlikeholde:

* Må kjøre dbupdate hver gang spørringen endres.
* Koden blir ikke inkludert i kode-repositoriet.

Hvis spørringen ville krevd flere spørringer fram og tilbake men ville vært raskere å putte i en procedure, da kan du bruke en stored procedure eller function.

## Turn slave into master

To completely disable replication with a master-master setup, you should do the following on each slave:

1. STOP SLAVE;
2. RESET SLAVE; \(Use RESET SLAVE ALL; for MySQL 5.5.16 and later\)
3. Edit the my.cnf and remove any information \(if present\) which refers to

   "master-..." or "replicate-..." options. You may not have anything in the

   my.cnf, since replication can be setup dynamically as well.

4. Restart mysqld.

I know this is an old question but I found I also has to reset the slave variables. If you use "blah" like suggested, the server will try on start up to find server 'blah'.

```sql
CHANGE MASTER TO MASTER_HOST='',MASTER_USER='',MASTER_PASSWORD='';
```

You can verify that the machine is no longer a slave

```sql
SHOW SLAVE STATUS \G;
```

This no longer works. Setting CHANGE MASTER TO MASTER\_HOST='' now throws an error

```sql
STOP SLAVE;
SHOW SLAVE STATUS;
CHANGE MASTER TO
MASTER_HOST='',
MASTER_PORT=0,
MASTER_USER='',
MASTER_PASSWORD='';
RESET MASTER;
```

The quickest and dirtiest way to clear slave info from a MySQL instance

1. Add skip-slave-start to /etc/my.cnf under \[mysqld\]
2. service mysql stop
3. rm -f /var/lib/mysql/master.info /var/lib/mysql/relay-\*
4. service mysql start
5. Remove skip-slave-start from /etc/my.cnf

That should do it for you !!!

Source: [dba.stackexchange.com](http://dba.stackexchange.com/questions/21087/how-to-change-a-mysql-previous-slave-to-be-a-master-and-remove-slave-status-info)

## Unable to convert MySQL date/time value to C\#'s System.DateTime

I get this error:

```text
Unable to convert MySQL date/time value to System.DateTime
```

while I am trying to fetch the data from a MySQL database. I have the date datatype in my MySQL database. But while retrieving it into my datatable, it get the error above. How can I fix this?

**Answer**: You must add Convert Zero Datetime=True to your connection string, for example:

```bash
server=localhost;User Id=root;password=mautauaja;Persist Security Info=True;database=test;Convert Zero Datetime=True
```

Source: [http://stackoverflow.com/questions/5754822/unable-to-convert-mysql-date-time-value-to-system-datetime](http://stackoverflow.com/questions/5754822/unable-to-convert-mysql-date-time-value-to-system-datetime)

## MySQL Workbench hangs

I was ready to throw away workbench due to the frequent freezes every time I worked with. Found this thread, and noticing the timeout issue, tried this:

```text
Edit > Preferences
SQL Editor > MySQL Session > DBMS connection keep-alive interval
```

The default here was set to 600 seconds. I've reduced that 30 seconds. No issues so far.

**Source**: [https://bugs.mysql.com/bug.php?id=69241](https://bugs.mysql.com/bug.php?id=69241)

## How to re-sync the Mysql DB if Master and slave have different database incase of Mysql replication

This is the full step-by-step procedure to resync a master-slave replication from scratch:

At the master:

```sql
RESET MASTER;
FLUSH TABLES WITH READ LOCK;
SHOW MASTER STATUS;
```

And copy the values of the result of the last command somewhere.

Without closing the connection to the client \(because it would release the read lock\) issue the command to get a dump of the master:

```bash
mysqldump -u root -p --all-databases > /a/path/mysqldump.sql
```

Now you can release the lock, even if the dump hasn't ended yet. To do it, perform the following command in the MySQL client:

```sql
UNLOCK TABLES;
```

Now copy the dump file to the slave using scp or your preferred tool.

At the slave, open a connection to mysql and type:

```sql
STOP SLAVE;
```

Load master's data dump with this console command:

mysql -uroot -p &lt; mysqldump.sql

Sync slave and master logs:

```sql
RESET SLAVE;
CHANGE MASTER TO MASTER_LOG_FILE='mysql-bin.000001', MASTER_LOG_POS=98;
```

Where the values of the above fields are the ones you copied before.

Finally, type:

```sql
START SLAVE;
```

To check that everything is working again, after typing:

```sql
SHOW SLAVE STATUS;
```

you should see:

```bash
Slave_IO_Running: Yes
Slave_SQL_Running: Yes
```

That's it!

**Source**: [stackoverflow.com](http://stackoverflow.com/questions/2366018/how-to-re-sync-the-mysql-db-if-master-and-slave-have-different-database-incase-o)

