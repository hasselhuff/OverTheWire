# Bandit Level 18 → Level 19

Site: https://overthewire.org/wargames/bandit/bandit19.html
## Goal
> There are 2 files in the homedirectory: **passwords.old and passwords.new**. 
> 
> The password for the next level is in **passwords.new** and is the only line that has been changed between **passwords.old and passwords.new**

## NOTE: 
> if you have solved this level and see ‘Byebye!’ when trying to log into bandit18, this is related to the next level, bandit19

## Commands you may need to solve this level
> cat, grep, ls, diff

-----------------

> username: bandit18
>
> password: kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd
>
> server: bandit.labs.overthewire.org
>
> port: 2220

ssh into the server:
```bash
ssh -l bandit18 bandit.labs.overthewire.org -p 2220
```

1. I googled how to run a command immediately after an ssh attempt and came up with:
```bash
ssh -l bandit18 bandit.labs.overthewire.org -p 2220 cat readme
```
Output:
```bash
IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x
```

Bandit19's password: IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x
