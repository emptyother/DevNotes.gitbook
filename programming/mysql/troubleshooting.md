# Troubleshooting

## Unable to convert MySQL date/time value to C\#'s System.DateTime

I get this error: `Unable to convert MySQL date/time value to System.DateTime`while I am trying to fetch the data from a MySQL database. I have the date datatype in my MySQL database. But while retrieving it into my datatable, it get the error above. How can I fix this?

**Solution**: You must add Convert Zero Datetime=True to your connection string, for example:

```bash
server=localhost;User Id=root;password=****;Persist Security Info=True;database=mydatabase;Convert Zero Datetime=True
```

**Source**: [http://stackoverflow.com/questions/5754822/](http://stackoverflow.com/questions/5754822/unable-to-convert-mysql-date-time-value-to-system-datetime)

## MySQL Workbench hangs

I was ready to throw away workbench due to the frequent freezes every time I worked with. Found this thread, and noticing the timeout issue, tried this:

```text
Edit > Preferences
SQL Editor > MySQL Session > DBMS connection keep-alive interval
```

The default here was set to 600 seconds. I've reduced that 30 seconds. No issues so far.

**Source**: [https://bugs.mysql.com/bug.php?id=69241](https://bugs.mysql.com/bug.php?id=69241)

