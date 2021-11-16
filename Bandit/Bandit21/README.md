# Bandit Level 21 → Level 22

Site: https://overthewire.org/wargames/bandit/bandit22.html
## Goal
> A program is running automatically at regular intervals from ** cron ** , the time-based job scheduler. 
> 
> Look in ** /etc/cron.d/ ** for the configuration and see what command is being executed.

## Commands you may need to solve this level: 
> cron, crontab, crontab(5) (use “man 5 crontab” to access this)

-----------------

> username: bandit21
>
> password: gE269g2h3mw3pwgrj0Ha9Uoqen1c9DGr
>
> server: bandit.labs.overthewire.org
>
> port: 2220

ssh into the server:
```bash
ssh -l bandit21 bandit.labs.overthewire.org -p 2220
```

1. List the contents in `/etc/cron.d/`:
```bash
ls /etc/cron.d/
```
2. Noticed a file called `cronjob_bandit22`:
Contents:
```bash
@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
```
3. Attempted to read `/usr/bin/cronjob_bandit22.sh`:
Contents
```bash
#!/bin/bash
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
```
4. Read the contents of `/tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv`:
Contents:
```bash
Yk7owGAcWjwMVRwrTesJEwB7WVOiILLI
```
Bandit22's password: Yk7owGAcWjwMVRwrTesJEwB7WVOiILLI
