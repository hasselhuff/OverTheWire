# Bandit Level 13 → Level 14

Site: https://overthewire.org/wargames/bandit/bandit14.html
## Goal
> The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. 
> 
> For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. 
> 
> Note: localhost is a hostname that refers to the machine you are working on

## Commands you may need to solve this level
> ssh, telnet, nc, openssl, s_client, nmap

## References:
* [SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

-----------------

> username: bandit13
>
> password: 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL
>
> server: bandit.labs.overthewire.org
>
> port: 2220

ssh into the server:
```bash
ssh -l bandit13 bandit.labs.overthewire.org -p 2220
```

1. Noted there was a `sshkey.private` in the home directory.
2. Used the above file to SSH into the same server (loopback address) as Bandit14:
```bash
ssh bandit14@127.0.0.1 -i sshkey.private
```
3. Then I `cat` the file the password was stored in:
```bash
cat /etc/bandit_pass/bandit14
```
4. Which gave:
```bash
4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
```

Bandit14's password: 4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
