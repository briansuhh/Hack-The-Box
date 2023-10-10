#### Guide on the Meow CTB

#####  File Transfer Protocol (ftp) is used for sharing files over a Transmission Control Protocol/Internet Protocol (TCP/IP)-based network like LAN or the internet. The default port of ftp is port 21.

1. What does the 3-letter acronym FPT stand for?<br>
file transfer protocol

2. Which port does the FTP service listen on usually?<br>
21
	- 20 or 21 is the commonly used port that ftp service listens to

3. What acronym is used for the secure version of FTP?<br>
sftp

	- ftps (file transfer protocol with ssl/tls)
	- sftp (ssh file transfer protocol
	- both are called secure ftp

4. What is the command we can use to send an ICMP echo request to test our connection to the target?<br>
ping 
	- ping sends an icmp echo request to the machine

5. From your scans, what version is FTP running on the target?<br>
vsftpd 3.0.3
	```bash
	nmap -p 21 -sV 10.129.130.158
	# this command will check the opened services on port 21 of 10.129.130.158
	```

6. From your scans, what OS type is running on the target?<br>
unix

7. What is the command we need to run in order to display the 'ftp' client help menu?<br>
ftp -h

8. What is username that is used over FTP when you want to log in without having an account?<br>
anonymous

9. What is the response code we get for the FTP message 'Login successful'?<br>
230 
	```bash
	ftp 10.129.130.158
	Connected to 10.129.130.158.
	220 (vsFTPd 3.0.3)
	Name (10.129.130.158:ayumi): anonymous
	331 Please specify the password.
	Password: 
	230 Login successful.
	Remote system type is UNIX.
	Using binary mode to transfer files.
	ftp> 
	```

10. There are a couple of commands we can use to list the files and directories available on the FTP server. One is dir. What is the other that is a common way to list files on a Linux system.<br>
ls

11. What is the command used to download the file we found on the FTP server?<br>
get
	```bash
	ls
	get flag.txt
	# the flag.txt file will be stored to our machine's download directory
	```
12. Submit root flag<br>
035db21c881520061c53e0536e44f815
	```bash
	# go to ~/Downloads directory and display the contents of flag.txt
	cs ~/Downloads
	cat flag.txt
	```
