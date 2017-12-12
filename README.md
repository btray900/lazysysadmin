# lazysysadmin
Vulnhub walkthrough

The optional steps are ones I took before the end result was acheived, so there are multiple ways to obtain the necessary information to root this VM.



## netdiscover

Obtain the DHCP IP of the VM.

![Alt text](./netdiscover.png?raw=true)



## nmap

Find interesting ports and dig some on SMB. A RW share is found.

![Alt text](./nmap.png?raw=true)

![Alt text](./enum-smb.png?raw=true)



## enum4linux

I assumed this was a Windows box, note 'togie' user found. I missed the 'Unix' part until later. When I ran the PHP code widget with the PHP reverse shell I used cmd.exe at first but received Not Found error. Don't rush your enumeration.

![Alt text](./enum4linux.png?raw=true)



## smbclient

Found Wordpress dir, interesting TXT files and get wp-config.php password. I could not write to the share.

![Alt text](./smbclient.png?raw=true)



## Get (optional)

Downloaded the wp-config.php file for inspection. Credentials found.

![Alt text](./wp-config.png?raw=true)



## Browser

Browsing to deets.txt exposed another compromised password.

![Alt text](./deets.png?raw=true)



## wpscan (optional)

Enumerated WP users. Since I could not write to the share, a semi-brutable WP login seemed likely.

![Alt text](./wpscan.png?raw=true)



## WP Admin Login (optional)

User: admin

Password: Compromised in wp-config.php file



## PHP Code plugin (optional)

Download/upload PHP Code Widget plugin and insert Pentest Monkey reverse PHP code. This is where I used cmd.exe originally and the error was a clue for OS detection.

![Alt text](./widget.png?raw=true)



## nc & shell (optional)

Start listener, visit home page, get shell.

![Alt text](./shell.png?raw=true)

cat /etc/passwd

![Alt text](./etcpasswd.png?raw=true)



## SSH

Try togie user with WP credentials. Fail.

Try togie user with deets.txt credentials for shell then sudo to root. Success

![Alt text](./rooted.png?raw=true)



# THANKS

Some strings to poke around on. Thanks out to Togie.
