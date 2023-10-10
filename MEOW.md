#### Guide on MEOW CTF Machine

1. What does the acronym VM stand for?
virtual machine

2. What tool do we use to interact with the operating system in order to issue commands via the command line, such as the one to start our VPN connection? It's also known as a console or shell.
terminal

3. What service do we use to form our VPN connection into HTB labs?
openvpn

4. What tool do we use to test our connection to the target with an ICMP echo request?
ping

5. What is the name of the most common tool for finding open ports on a target?
nmap

6. What service do we identify on port 23/tcp during our scans?
telnet

7. What username is able to log into the target over telnet with a blank password?
root
	```bash
	# use this command to connect to the machine using telnet, 23 is the port
	telnet 10.129.48.137 23
	Trying 10.129.48.137...
	Connected to 10.129.48.137.
	Escape character is '^]'.
	root

	```

8. Submit root flag
b40abdfe23665f766f9c61ecba8a4c19




