# Bandit Level 3 → Level 4

Site: https://overthewire.org/wargames/bandit/bandit4.html
## Goal
> The password for the next level is stored in a hidden file in the inhere directory.

## Commands you may need to solve this level
> ls, cd, cat, file, du, find

-----------------

> username: bandit3
>
> server: bandit.labs.overthewire.org
>
> port: 2220

ssh into the server:
```bash
ssh -l bandit3 bandit.labs.overthewire.org -p 2220
```

1. Ran `ls` with the `l` and `a` options on the `inhere` directory to show all items including hidden items in long format
```bash
ls -la inhere
```
2. Noticed a file called `.hidden` in the directory
3. Concatenate the hidden file
```bash
cat inhere/.hidden
```
