---
description: Anything related to MySQL.
---

# MySQL

## Backup everything including master data

```bash
mysqldump -uroot -p --all-databases --routines --flush-privileges --triggers --events --master-data=1 --quick | gzip -1 > ./dbbackup.sql.gz;
```

**📝Note**: If the database is mixed MyIsam and InnoDB then you must lock the database first and --single-transaction will not work.

## Restore

```bash
mysql -uroot -p < /mnt/backupdrive/dbbackup.sql.gz;
```

## Global variables

Query global variables:

```sql
SHOW GLOBAL VARIABLES LIKE 'slow_query_log';
```

Set global variable:

```sql
SET GLOBAL slow_query_log = 'ON';
```

## Do not use Stored Procedures or Functions unless it saves network traffic

A stored procedure is slower. That the server is optimizing is a myth. Stored procedures is also more difficult to maintain. 

_Like most rules, this isn't a hard rule_: If the query would require multiple queries back and forth but would have been faster to put in a procedure, then you might consider using a stored procedure or function.

## Delete slow\_log table

Deleting from MySQL's log gives you this error:

`You can't use locks with log tables.`

To delete from a system log you need to disable it and rename it, then run your _"Delete"_ query, and rename it back again.

```sql
SET GLOBAL slow_query_log = 'OFF';
RENAME TABLE `mysql`.`slow_log` TO `mysql`.`slow_log_temp`;
DELETE FROM `mysql`.`slow_log_temp` WHERE `start_time` < '2019-09-01';
RENAME TABLE `mysql`.`slow_log_temp` TO `mysql`.`slow_log`;
SET GLOBAL slow_query_log = 'ON';
```

## 

