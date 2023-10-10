#### Guide on DANCING CTF Machine

##### Server message block (smb) is used for sharing files, printers and other resources on LAN or the internet.

1. What does the 3-letter acronym SMB stand for?<br>
server message block

2. What port does SMB use to operate at? <br>
445

3. What is the service name for port 445 that came up in our Nmap scan?<br>
microsoft-ds
	- microsoft directory services is a common service that runs over the Server Message Block (smb). It is responsiblef for directory and file-sharing services.
	
4. What is the 'flag' or 'switch' that we can use with the smbclient utility to 'list' the available shares on Dancing?<br>
-L

	```bash
	smbclient -L 10.129.23.34
	```
5. How many shares are there on Dancing?<br>
4
	```bash
	smbclient -L \\10.129.23.34\\Workshares
	Password for [WORKGROUP\ayumi]:

		Sharename       Type      Comment
		---------       ----      -------
		ADMIN$          Disk      Remote Admin
		C$              Disk      Default share
		IPC$            IPC       Remote IPC
		WorkShares      Disk    
		  
	Reconnecting with SMB1 for workgroup listing.
	do_connect: Connection to 10.129.23.34 failed (Error NT_STATUS_RESOURCE_NAME_NOT_FOUND)
	Unable to connect with SMB1 -- no workgroup available
	
	```
6. What is the name of the share we are able to access in the end with a blank password?<br>
WorkShares

7. What is the command we can use within the SMB shell to download the files we find?<br>
get
	```bash
	smbclient \\\\10.129.23.34\\WorkShares
	Password for [WORKGROUP\ayumi]:
	Try "help" to get a list of possible commands.
	smb: \> help
	?              allinfo        altname        archive        backup         
	blocksize      cancel         case_sensitive cd             chmod          
	chown          close          del            deltree        dir            
	du             echo           exit           get            getfacl        
	geteas         hardlink       help           history        iosize         
	lcd            link           lock           lowercase      ls             
	l              mask           md             mget           mkdir          
	more           mput           newer          notify         open           
	posix          posix_encrypt  posix_open     posix_mkdir    posix_rmdir    
	posix_unlink   posix_whoami   print          prompt         put            
	pwd            q              queue          quit           readlink       
	rd             recurse        reget          rename         reput          
	rm             rmdir          showacls       setea          setmode        
	scopy          stat           symlink        tar            tarmode        
	timeout        translate      unlock         volume         vuid           
	wdel           logon          listconnect    showconnect    tcon           
	tdis           tid            utimes         logoff         ..             
	!              
	smb: \> ls
	cd James.P
	smb: \James.P\> ls
	  .                                   D        0  Thu Jun  3 16:38:03 2021
	  ..                                  D        0  Thu Jun  3 16:38:03 2021
	  flag.txt                            A       32  Mon Mar 29 17:26:57 2021
	smb: \James.P\> get flag.txt
	getting file \James.P\flag.txt of size 32 as flag.txt (0.0 KiloBytes/sec) (average 0.1 KiloBytes/sec)
	```

8. Submit root flag<br>
5f61c10dffbc77a704d76016a22f1664

	- the flag.txt will be downloaded to your machine, so you can show that by using the command 'cat'
	
	
