# lazysysadmin
Vulnhub walkthrough

## netdiscover

Obtain the DHCP IP of the VM.
[netdiscver pic]

## nmap

Find interesting ports

### Check shares


## enum4linux

I assumedit was a windows box, note 'togie' user


### Find Wordpress dir and get wp-config.php password


## Login

Try togie user and password from config


## wpscan

Enumerate users to try password for login

Login OK

## PHP Code plugin

Insert PHP shell code into plugin

Start listener

cat /etc/passwd


