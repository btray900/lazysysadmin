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

### Find Wordpress dir and get wp-config.php password

![Alt text](./wp-config.png?raw=true)


## Login

Try togie user and password from config


## wpscan

Enumerate users to try password for login

Login OK

## PHP Code plugin

Insert PHP shell code into plugin

Start listener

cat /etc/passwd


