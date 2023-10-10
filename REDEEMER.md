#### Guide on REDEEMER CTF Machine

##### Redis, which stands for "Remote Dictionary Server," is an open-source, in-memory database. It is often referred to as a "data structure server" because it allows you to store and manipulate various data structures in memory, including strings, lists, sets, maps, and more. 

##### In-memory databases like Redis are typically used to cache data that is frequently requested for quick retrieval. For example, if there is a website that returns some prices on the front page of the site. The website may be written to first check if the needed prices are in Redis, and if not, then check the traditional database (like MySQL or MongoDB). When the value is loaded from the database, it is then stored in Redis for some shorter period of time (seconds or minutes or hours), to handle any similar requests that arrive during that timeframe. For a site with lots of traffic, this configuration allows for much faster retrieval for the majority of requests, while still having stable long term storage in the main database.

sudo nmap -sU 10.129.39.6

Nmap scan report for 10.129.39.6
Host is up (0.24s latency).
Not shown: 999 closed udp ports (port-unreach)
PORT   STATE         SERVICE
68/udp open|filtered dhcpc

nmap -p- -sV 10.129.39.6

Nmap scan report for 10.129.39.6
Host is up (0.24s latency).
Not shown: 65534 closed tcp ports (conn-refused)
PORT     STATE SERVICE VERSION
6379/tcp open  redis   Redis key-value store 5.0.7
