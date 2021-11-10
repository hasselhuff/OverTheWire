# Bandit Level 7 → Level 8

Site: https://overthewire.org/wargames/bandit/bandit8.html
## Goal
> The password for the next level is stored in the file data.txt next to the word millionth

## Commands you may need to solve this level
> grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

-----------------

> username: bandit7
>
> password: HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs
>
> server: bandit.labs.overthewire.org
>
> port: 2220

ssh into the server:
```bash
ssh -l bandit7 bandit.labs.overthewire.org -p 2220
```

1. Ran the following command with `grep`
```bash
grep "millionth" data.txt 
```
2. The result of the above command gave me the output:
```bash
millionth       cvX2JJa4CFALtqS87jk27qwqGhBM9plV
```


Bandit8's password: cvX2JJa4CFALtqS87jk27qwqGhBM9plV
