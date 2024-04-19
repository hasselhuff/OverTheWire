# Bandit Level 4 → Level 5

Site: https://overthewire.org/wargames/bandit/bandit5.html
## Goal
> The password for the next level is stored in the only human-readable file in the inhere directory. 
> 
> Tip: if your terminal is messed up, try the “reset” command.

## Commands you may need to solve this level
> ls, cd, cat, file, du, find

-----------------

> username: bandit4
>
> server: bandit.labs.overthewire.org
>
> port: 2220

ssh into the server:
```bash
ssh -l bandit4 bandit.labs.overthewire.org -p 2220
```

1. Ran `file` on all the files in the `inhere` directory to determine their file types
```bash
file inhere/*
```
> Note:
> 
> `*` is a wildcard that shows anything that matches, well, anything

2. Noticed a file called `-file07` is the only file with `ASCII` type
3. Concatenate the file
```bash
cat inhere/-file07
```
