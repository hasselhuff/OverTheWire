# Bandit Level 6 → Level 7

Site: https://overthewire.org/wargames/bandit/bandit6.html
## Goal
> The password for the next level is stored somewhere on the server and has all of the following properties:
>
>>  owned by user bandit7
>
>>  owned by group bandit6
>
>>  33 bytes in size


## Commands you may need to solve this level
> ls, cd, cat, file, du, find, grep

-----------------

> username: bandit6
>
> password: DXjZPULLxYr17uwoI01bNLQbtFemEgo7
>
> server: bandit.labs.overthewire.org
>
> port: 2220

ssh into the server:
```bash
ssh -l bandit6 bandit.labs.overthewire.org -p 2220
```

1. Ajusted previous `find` command with new filters:
```bash
find / -user bandit7 -group bandit6 -size 33c 2>/dev/null -exec cat {} \;
```
> Note:
> 
> `/` begins the search recursively from the root of the filesystem
>  
>  `2>/dev/null`  sends all on screen errors to `null` in order to remove errors from displaying on the screen
2. The result of the above command gave me the output `HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs`


Bandit7's password: HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs
