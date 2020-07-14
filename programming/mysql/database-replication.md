# Database Replication

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

**Source**: [dba.stackexchange.com](http://dba.stackexchange.com/questions/21087/how-to-change-a-mysql-previous-slave-to-be-a-master-and-remove-slave-status-info)

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

## Azure MySQL

### Limits

* No SUPER privilege.
  * Need to call built-in procedures to run replication commands.
* No MyISAM table engine.

### Replication

#### Create backup

```bash
# Only make master copy of a single database
# master-data=2 to only add the CHANGE MASTER command as comment.
mysqldump -u username -p --single-transaction --master-data=2 --quick mydatabase > db.sql


```

#### Useful links:

* [https://docs.microsoft.com/en-us/azure/mysql/howto-data-in-replication](https://docs.microsoft.com/en-us/azure/mysql/howto-data-in-replication)

#### Commands:

```sql
# CHANGE MASTER
CALL mysql.az_replication_change_master('master.companya.com', 'syncuser', 'P@ssword!', 3306, 'mysql-bin.000002', 120, '');
# Other replication commands
CALL mysql.az_replication_start;
CALL mysql.az_replication_stop;
CALL mysql.az_replication_remove_master;
CALL mysql.az_replication_skip_counter;
```

### Troubleshooting

#### Error when restoring backup: "Table storage engine for 'dbo.table' doesn't have this option."

It probably tries to set `ROW_FORMAT=Dynamic`. Happens if the table is a InnoDB converted from MyISAM. Run this command before the restore to ignore this:

```sql
SET SESSION innodb_strict_mode=OFF;
```

