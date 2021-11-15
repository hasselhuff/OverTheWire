# Bandit Level 19 → Level 20

Site: https://overthewire.org/wargames/bandit/bandit20.html
## Goal
> To gain access to the next level, you should use the setuid binary in the homedirectory. 
> 
> Execute it without arguments to find out how to use it. 
> 
> The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.

## References: 
* [setuid on Wikipedia](https://en.wikipedia.org/wiki/Setuid)

-----------------

> username: bandit19
>
> password: IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x
>
> server: bandit.labs.overthewire.org
>
> port: 2220

ssh into the server:
```bash
ssh -l bandit19 bandit.labs.overthewire.org -p 2220
```

1. Ran the binary found in the home directory:
```bash
./bandit20-do
```
Output:
```bash
Run a command as another user.
  Example: ./bandit20-do id
```
2. Ran the example command:
```bash
./bandit20-do id
```
Output:
```bash
uid=11019(bandit19) gid=11019(bandit19) euid=11020(bandit20) groups=11019(bandit19)
```
Note:
* `euid` means Effective User ID, so we have bandit20 permissions 
3. Read the password file for bandit20:
```bash
./bandit20-do cat /etc/bandit_pass/bandit20
```
Output:
```bash
GbKksEFF4yrVs6il55v6gwY5aVje5f0j
```
Bandit20's password: GbKksEFF4yrVs6il55v6gwY5aVje5f0j
