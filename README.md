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

I assumedit was a Windows box, note 'togie' user found. I missed the 'Unix' part until later ;)

![Alt text](./enum4linux.png?raw=true)


## smbclient

Found Wordpress dir and get wp-config.php password

![Alt text](./smbclient.png?raw=true)

![Alt text](./wp-config.png?raw=true)

Found deets.txt with compromised credential information

![Alt text](./deets.png?raw=true)


## wpscan

Enumerate users.

![Alt text](./wpscan.png?raw=true)


## WP Admin Login

User: admin
Password: Compromised in wp-config


## PHP Code plugin

Insert PHP shell code into plugin

![Alt text](./widget.png?raw=true)

Start listener, get shell

![Alt text](./shell.png?raw=true)


cat /etc/passwd

![Alt text](./etcpasswd.png?raw=true)


Try togie user with WP credentials. Fail.

Try togie user with deets.txt credentials. Success

![Alt text](./rooted.png?raw=true)


