#### Guide on the Meow CTB

1. What does the 3-letter acronym FPT stand for?
file transfer protocol

2. Which port does the FTP service listen on usually?
21
	- 20 or 21 is the commonly used port that ftp service listens to

3. What acronym is used for the secure version of FTP?
sftp

	- ftps (file transfer protocol with ssl/tls)
	- sftp (ssh file transfer protocol
	- both are called secure ftp

4. What is the command we can use to send an ICMP echo request to test our connection to the target?
ping 
	- ping sends an icmp echo request to the machine

5. From your scans, what version is FTP running on the target?
vsftpd 3.0.3

	- nmap -p 21 -sV 10.129.130.158
	- this command will check the opened services on port 21 of 10.129.130.158

6. From your scans, what OS type is running on the target?
unix

7. What is the command we need to run in order to display the 'ftp' client help menu?
ftp -h

8. What is username that is used over FTP when you want to log in without having an account?
anonymous

9. What is the response code we get for the FTP message 'Login successful'?
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

10. There are a couple of commands we can use to list the files and directories available on the FTP server. One is dir. What is the other that is a common way to list files on a Linux system.
ls

11. What is the command used to download the file we found on the FTP server?
get
	```bash
	ls
	get flag.txt
	# the flag.txt file will be stored to our machine's download directory
	```
12. Submit root flag

	```bash
	# go to ~/Downloads directory and display the contents of flag.txt
	cs ~/Downloads
	cat flag.txt
	```
