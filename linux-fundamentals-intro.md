
# Workflow

## Navigtion

What is the name of the hidden "history" file in the htb-user's home directory?

$ ls -la

What is the index number of the "sudoers" file in the "/etc" directory?


$ cd /etc

$ ls -i | grep sudoers

## Working with Filesand Directories
What is the name of the last modified file in the "/var/backups" directory?(man ls)

$ ls -t | head -n

What is the inode number of the "shadow.bak" file in the "/var/backups" directory?

$ ls -i | grep shadow.bak

## Find Files and Directories

What is the name of the config file that has been created after 2020-03-03 and is smaller than 28k but larger than 25k?

$ find / -type f -name *.conf -user root -size +25k -size -28k -newermt 2020-03-03 -exec ls -al {} \; 2>/dev/null

How many files exist on the system that have the ".bak" extension?
(use wc cont line)

$ find / -type f -name *.bak -exec ls -al {} \; 2>/dev/null |wc -l

or

$ locate *.bak | wc -l 

Submit the full path of the "xxd" binary.

$ locate xxd

## File Descriptors and Redirections


How many files exist on the system that have the ".log" file extension?

$ find / -name "*.log" 2>/dev/null | wc -l


How many total packages are installed on the target system?

$ apt list --installed | grep -c installed


## Filter Contents

How many services are listening on the target system on all interfaces? (Not on localhost and IPv4 only)

$ netstat -tunleep4 | grep -v “127.0.0”

or

$ ss -l -4 | grep -v “127.0.0” | grep “LISTEN” | wc -l

Determine what user the ProFTPd server is running under. Submit the username as the answer.

$ cat /etc/proftpd/proftpd.conf | grep User


