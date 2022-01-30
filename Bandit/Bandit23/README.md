# Bandit Level 23 → Level 24

Site: https://overthewire.org/wargames/bandit/bandit24.html
## Goal
> A program is running automatically at regular intervals from cron, the time-based job scheduler. 
> 
> Look in /etc/cron.d/ for the configuration and see what command is being executed.

## NOTE: 
> This level requires you to create your own first shell-script. 
> 
> This is a very big step and you should be proud of yourself when you beat this level!

## NOTE 2: 
> Keep in mind that your shell script is removed once executed, so you may want to keep a copy around… 

## Commands you may need to solve this level:
> cron, crontab, crontab(5) (use “man 5 crontab” to access this)

-----------------

> username: bandit23
>
> password: jc1udXuA1tiHqjIsL8yaapX5XIAI6i0n
>
> server: bandit.labs.overthewire.org
>
> port: 2220

ssh into the server:
```bash
ssh -l bandit23 bandit.labs.overthewire.org -p 2220
```

1. List the contents in `/etc/cron.d/`:
```bash
ls /etc/cron.d/
```
2. Noticed a file called `cronjob_bandit24`:
Contents:
```bash
@reboot bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
* * * * * bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
```
3. Attempted to read `/usr/bin/cronjob_bandit24.sh`:
Contents
```bash
#!/bin/bash

myname=$(whoami)

cd /var/spool/$myname
echo "Executing and deleting all scripts in /var/spool/$myname:"
for i in * .*;
do
    if [ "$i" != "." -a "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" ./$i)"
        if [ "${owner}" = "bandit23" ]; then
            timeout -s 9 60 ./$i
        fi
        rm -f ./$i
    fi
done
```
# Script Breakdown:
* The script gets the user running the script with `whoami`
* Changes directories to /var/spool/<output of whoami>
* Iterates through all the files in the current directory
* Skips over the `.` and `..` directories and grabs the owner for each file
* If the file is owned by `bandit23` execute the file and after 60 seconds kill the process
* After the 60 seconds remove the file that got executed and finish
4. Lets see which folders are in /var/spool and their priviliges:
```bash
ls -l /var/spool
```
Output:
```bash
drwxrwx-wx 73 root bandit24 4096 Jan 30 04:06 bandit24
```

Bandit24's password: jc1udXuA1tiHqjIsL8yaapX5XIAI6i0n
