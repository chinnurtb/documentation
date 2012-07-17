Dumping a database via ssh
--------------------------

    ssh server "mysqldump -u$mysqluser -p$mysqlpass $mysqldatabase"


Dumping schema only
-------------------

    mysqldump --no-data ...

Dumping data only
-----------------

    mysqldump --no-create-info ...

Each insert in its own line
---------------------------

Useful when saving dump diffs in version control

    mysqldump --extended-insert=FALSE ...

# Export Table Generation

```
SHOW CREATE TABLE tbl_name;
```


Truncate all tables
-------------------

**not working yet**

    mysql -Nse 'show tables' -uroot -proot gynny | awk '{print "TRUNCATE "$0";"}' | mysql -uroot -proot gynny

    mysql -Nse 'show tables'

Shows all tables without boilerplate

    awk '{print "TRUNCATE "$0";"}

Transforms the table into a truncate

# mysql client

## show all tables

    show tables;

    describe $table;

    show CREATE TABLE $table
