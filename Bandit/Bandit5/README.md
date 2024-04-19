# Bandit Level 5 → Level 6

Site: https://overthewire.org/wargames/bandit/bandit6.html
## Goal
> The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:
>
>>  human-readable
>
>>  1033 bytes in size
>
>>  not executable


## Commands you may need to solve this level
> ls, cd, cat, file, du, find

-----------------

> username: bandit5
>
> server: bandit.labs.overthewire.org
>
> port: 2220

ssh into the server:
```bash
ssh -l bandit5 bandit.labs.overthewire.org -p 2220
```

1. Ran `man find` to see the different options to better limit my search on all the files in the `inhere` directory:
```bash
find ./inhere -readable -size 1033c -not -executable -exec cat {} \;
```
> Note:
> 
> `*1033c` is 1033 bytes in the `find` command
>  
>  `-exec cat {} \;` is to execute the `cat` command on any file that gets matched with 
>  
>  `{}` being the placeholder for the file and 
>  
>  `\;` being required when using the `-exec` switch

## Bonus
To list the name of the file with the password:
```bash
find inhere/ -readable -size 1033c -not -executable -exec ls {} \; -exec  cat {} \;
```
