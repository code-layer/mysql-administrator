# backup and restore

Assume that mysql server is running on x.x.x.22 machine. How to move the data from this machine to say another machine x.x.x.23

There are many methods available for backup and restoring mysql data.Let us use the MySQL inbuilt tool set for simple cases like dev,test and clone cases.

![Simple backup!](/assets/images/simple-backup.jpg)


## setup
Make sure that both machines are running on same mysql version.

## backup
Connect to x.x.x.22 instance. Put the server in read only mode, so that writes are disabled during backup.

``` java
  mysqldump -u root -p --lock-all-tables --all-databases > server1_backup.sql

  //copy file to server2
  scp server1_backup.sql root@x.x.x.23:/root
```

## restore
Import data into x.x.x.23 machine

``` java
  mysql -u root -p < /root/server1_backup.sql

```
Connect to x.x.x.23 instance.
Verify the database, tables and data.


## links
[Datalayer](https://datalayer.in/)

## contributing
Pull requests are welcome.