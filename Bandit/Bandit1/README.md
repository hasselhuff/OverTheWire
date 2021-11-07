# Bandit Level 1 → Level 2

Site: https://overthewire.org/wargames/bandit/bandit2.html
## Goal
> The password for the next level is stored in a file called - located in the home directory

## Commands you may need to solve this level
> ls, cd, cat, file, du, find

## Resources
* [Google Search for “dashed filename”](https://www.google.com/search?q=dashed+filename)
* [Advanced Bash-scripting Guide - Chapter 3 - Special Characters](http://tldp.org/LDP/abs/html/special-chars.html)
-----------------

> username: bandit1
>
> password: boJ9jbbUNNfktd78OOpsqOltutMc3MY1
>
> server: bandit.labs.overthewire.org
>
> port: 2220

ssh into the server:
```bash
ssh -l bandit1 bandit.labs.overthewire.org -p 2220
```

1. Ran an `ls` to list the contents of `bandit1`'s home directory
2. Noticed a file called `-`
3. To concatenate a file that is in the current directory you preface the file with `./`
> Note:
> `.` is the shortcut for "current directory and the `/` to signify you are looking for a file or folder
```bash
cat ./-
```
Which uncovered bandit2's password: CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9
