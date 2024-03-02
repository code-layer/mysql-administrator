# install software
Learn to install MySQL software from Percona vendor. Percona is a drop in replacement for oracle.com MySQL product.Provides various tool sets and xtrabackup tool.


## install dependencies
Setup any VM or Container.

Update system packages and setup hotname,network and timezone info.


## configure repos

yum install https://repo.percona.com/yum/percona-release-latest.noarch.rpm.

### install particular version

``` java
percona-release setup ps80

//install server package
yum install percona-server-server

``` 

### install additional packages

``` java
percona-release enable-only tools release

yum install percona-toolkit
yum install percona-xtrabackup-80

```

## start service
systemctl start mysqld

verify using ps aux | grep mysqld

## root password

On startup mysql generates default root user and a password for root user.Password is saved in mysqld.log file.
root user is accessible from localhost only.

### reset root password
Get root password.
cat /var/log/mysqld.log | grep 'temporary password'

``` java
mysql -u root -p
mysql> alter user 'root'@'localhost' identified by 'data@MySQL8';
mysql> flush privileges;
mysql> exit;
```

## process details
	ps aux | grep mysql
	cat /var/run/mysqld/mysqld.pid
	netstat -tlpn | grep 3306

	new os user 'mysql' and os group 'mysql' are added to linux box
		mysql:x:27:
		mysql:x:27:27:Percona Server:/var/lib/mysql:/bin/false

	Note: process takes more RAM, by default performace data is enabled and collected.
	
## file layouts

log file

	/var/log/mysqld.log

configuration file

	/etc/my.cnf

data files

	/var/lib/mysql

other files

	/var/lib/mysql-files
	/var/lib/mysql-keyring

## stop service
systemctl stop mysqld

## links
[Datalayer](https://datalayer.in/)

## contributing
Pull requests are welcome.