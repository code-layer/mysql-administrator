# default configuration
The mysql configuration file is located under /etc/my.cnf

On server startup all variables are initialized with default values. The number of variables are increasing with each version. Only few are listed in config file.
Check the official documentation or check the current values on a running instance.



## minimal configuration

``` java
  [mysqld]
  #core settings
  port=3306
  bind-address=0.0.0.0
  skip-name-resolve
  default-authentication-plugin=mysql_native_password

  #performace schema
  performance_schema=OFF
```

### check status
Connect to mysql instance.
> status;\
> show status;\
>	show status \G;\
>	show status like 'Connection%';

### check variables
> show variables;\
> show variables \G;\
> show variables like 'default%';


## make changes to configuration

First back up existing configuration file.

``` java
  cp /etc/my.cnf my.cnf.back
```
Let us say we want to log statements in local time and explicitly specify a log file destination.\
Open /etc/my.cnf file

``` java
  log_timestamps=SYSTEM
  log_output=FILE
  general_log=1
  general_log_file=/var/log/mysql/mysql.log
```
##### Note: make sure the log folder is present.

Restart mysql server. Check the log file and time stamp for log events.


## others
> show engines; \
> show plugins;

## show commands
``` java
  show character set;
  show collation;
  show processlist
  show errors
  show warnings
  show databases
```

## key show status commands
  show status like 'Bin%';
	
Similarly replace search option with any of the following
``` java
  'Com%'
  'Connection%'
  'Handler%'
  'Innodb%'
  'Max%'
  'Open%'
  'Performance%'
  'Select%'
  'Threads%'
```

## key show variable commands
config or settings related variables
``` java
  'default%'
  'auto%'
  'have%'
  'max%'
  '%cache%'
  'log%'
  'innodb%'
```

replication related variables 
``` java
  'binlog%'
  'gtid%'
  'relay%'
  'slave%'
```

performance related variables
``` java
  '%lock%'
  '%flush%'
  '%sess%'
  '%perf%'
```

## Note

The mysql server configuration changes can be made in differnet ways. These are covered in detail at a later stage. Right now learn to read various 
values or make some simple changes and observe the results.

## links
[Datalayer](https://datalayer.in/)

## contributing
Pull requests are welcome.