# Bandit Level 9 → Level 10

Site: https://overthewire.org/wargames/bandit/bandit10.html
## Goal
> The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.

## Commands you may need to solve this level
> grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

-----------------

> username: bandit9
>
> password: UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR
>
> server: bandit.labs.overthewire.org
>
> port: 2220

ssh into the server:
```bash
ssh -l bandit9 bandit.labs.overthewire.org -p 2220
```

1. Ran the following command:
```bash
cat data.txt | strings | grep "====*"
```
> Note:
> `strings` prints the strings of printable characters in files
> 
> `====*` since I did not know the exact number of `=` to search for I placed a few with a `*` to show lines that have anything else after four `=`'s
> 
2. The result of the above command gave me the output:
```bash
========== the*2i"4
========== password
Z)========== is
&========== truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk
```


Bandit10's password: truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk
