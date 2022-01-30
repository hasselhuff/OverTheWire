# Bandit Level 22 → Level 23

Site: https://overthewire.org/wargames/bandit/bandit23.html
## Goal
> A program is running automatically at regular intervals from cron, the time-based job scheduler. 
> 
> Look in /etc/cron.d/ for the configuration and see what command is being executed.

## NOTE: 
> Looking at shell scripts written by other people is a very useful skill. 
> 
> The script for this level is intentionally made easy to read. 
> 
> If you are having problems understanding what it does, try executing it to see the debug information it prints.

## Commands you may need to solve this level:
> cron, crontab, crontab(5) (use “man 5 crontab” to access this)

-----------------

> username: bandit22
>
> password: Yk7owGAcWjwMVRwrTesJEwB7WVOiILLI
>
> server: bandit.labs.overthewire.org
>
> port: 2220

ssh into the server:
```bash
ssh -l bandit22 bandit.labs.overthewire.org -p 2220
```

1. List the contents in `/etc/cron.d/`:
```bash
ls /etc/cron.d/
```
2. Noticed a file called `cronjob_bandit23`:
Contents:
```bash
@reboot bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
* * * * * bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
```
3. Attempted to read `/usr/bin/cronjob_bandit23.sh`:
Contents
```bash
#!/bin/bash

myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

cat /etc/bandit_pass/$myname > /tmp/$mytarget
```
4. We can deduce the password for `bandit23` by the following:
* The cron job has the script ran as `bandit23` so we know that will be returned when the script runs the `whoami` command
* We run the command subsitition for `mytarget` by running:
```bash
echo "I am user bandit23" | md5sum | cut -d ' ' -f 1
```
* The output should be: `8ca319486bfbbc3663ea0fbe81326349`
* Lastly we see that bandit23's password is placed in a file in the `/tmp` named with the output from the previous command
```bash
cat /tmp/8ca319486bfbbc3663ea0fbe81326349
```
Bandit23's password: jc1udXuA1tiHqjIsL8yaapX5XIAI6i0n
