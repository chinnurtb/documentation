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


