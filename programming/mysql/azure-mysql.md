# Azure MySQL

## Limits

* No SUPER privilege.
  * Need to call built-in procedures to run replication commands.
* No MyISAM table engine.

## Replication

### Create backup

```bash
# Only make master copy of a single database
# master-data=2 to only add the CHANGE MASTER command as comment.
mysqldump -u username -p --single-transaction --master-data=2 --quick mydatabase > db.sql


```

### Useful links:

* [https://docs.microsoft.com/en-us/azure/mysql/howto-data-in-replication](https://docs.microsoft.com/en-us/azure/mysql/howto-data-in-replication)

### Commands

```sql
# CHANGE MASTER
CALL mysql.az_replication_change_master('master.companya.com', 'syncuser', 'P@ssword!', 3306, 'mysql-bin.000002', 120, '');
# Other replication commands
CALL mysql.az_replication_start;
CALL mysql.az_replication_stop;
CALL mysql.az_replication_remove_master;
CALL mysql.az_replication_skip_counter;
```

## Troubleshooting

### Error when restoring backup: "Table storage engine for 'dbo.table' doesn't have this option."

It probably tries to set `ROW_FORMAT=Dynamic`. Happens if the table is a InnoDB converted from MyISAM. Run this command before the restore to ignore this:

```sql
SET SESSION innodb_strict_mode=OFF;
```

