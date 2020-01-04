# SQL Server

## Validate SQL scripts

Add this statement as the first line to prevent SQL Server from executing the
statements.

```sql
SET NOEXEC ON;
```

To turn it off, do

```sql
SET NOEXEC OFF;
```

## Convert INSERT statements from MySQL to SQL Server

1. Replace table name from 'table' to [database].[tablename]
2. Replace column name from 'column' to [column]
3. Replace escaped quotes \' with ''.
4. Replace b'0' and b'1' with 0 and 1 (bits to integer).
5. Replace zero-dates '0000-00-00' with NULL.

## INSERT statement

Example insert statement for SQL server:

```sql
INSERT INTO [mydb].[table] ([id],[name]) VALUES (121480, 'Rock Name');
```
