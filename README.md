# lazysysadmin
Vulnhub walkthrough



## netdiscover

Obtain the DHCP IP of the VM.

![Alt text](./netdiscover.png?raw=true)



## nmap

Find interesting ports and dig some on SMB. A RW share is found.

![Alt text](./nmap.png?raw=true)

![Alt text](./enum-smb.png?raw=true)



## enum4linux

I assumed this was a Windows box, note 'togie' user found. I missed the 'Unix' part until later. When I ran the PHP code widget with the PHP reverse shell I used cmd.exe at first but received Not Found error. ;)

I tend to rush my enumeration with CTF's and boot2roots because they are known to be vulnerable. It's a bad habit. :(

![Alt text](./enum4linux.png?raw=true)



## smbclient

Found Wordpress dir, interesting TXT files and get wp-config.php password. I could not write to the share.

![Alt text](./smbclient.png?raw=true)


## Get

Downloaded the wp-config.php file for inspection. Credetnials found.

![Alt text](./wp-config.png?raw=true)



## Browser

Browsing to deets.txt exposed another compromised password.

![Alt text](./deets.png?raw=true)



## wpscan

Enumerated WP users. Since I could not write to the share, a semi-brutable WP login seemed likely.

![Alt text](./wpscan.png?raw=true)



## WP Admin Login

User: admin

Password: Compromised in wp-config.php file



## PHP Code plugin

Download/upload PHP Code Widget plugin and insert Pentest Monkey reverse PHP code. This is where I used cmd.exe originally and changed it back to /bin/sh.

![Alt text](./widget.png?raw=true)



## nc & shell

Start listener, visit home page, get shell.

![Alt text](./shell.png?raw=true)

cat /etc/passwd

![Alt text](./etcpasswd.png?raw=true)



## SSH

Try togie user with WP credentials. Fail.

Try togie user with deets.txt credentials. Success

![Alt text](./rooted.png?raw=true)


# THANKS!

This was big fun! Many thanks to Togie!
