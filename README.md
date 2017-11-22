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

I assumedit was a Windows box, note 'togie' user found. I missed the 'Unix' part until later. When I ran the PHP code widget with the PHP reverse shell I used cmd.exe but received Not Found error. ;)

![Alt text](./enum4linux.png?raw=true)


## smbclient

Found Wordpress dir, interesting TXT files and get wp-config.php password. I could not write to the share.

![Alt text](./smbclient.png?raw=true)

![Alt text](./wp-config.png?raw=true)

Found deets.txt with compromised credential information.

![Alt text](./deets.png?raw=true)


## wpscan

Enumerated WP users.

![Alt text](./wpscan.png?raw=true)


## WP Admin Login

User: admin

Password: Compromised in wp-config.php file


## PHP Code plugin

Download/upload PHP Code Widget plugin.

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


This was big fun! Many thanks to Togie!
