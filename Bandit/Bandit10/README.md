# Bandit Level 10 → Level 11

Site: https://overthewire.org/wargames/bandit/bandit10.html
## Goal
> The password for the next level is stored in the file data.txt, which contains base64 encoded data

## Commands you may need to solve this level
> grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

## References:
> https://en.wikipedia.org/wiki/Base64

-----------------

> username: bandit10
>
> password: truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk
>
> server: bandit.labs.overthewire.org
>
> port: 2220

ssh into the server:
```bash
ssh -l bandit10 bandit.labs.overthewire.org -p 2220
```

1. Ran the following command:
```bash
cat data.txt | base64 -d
```
> Note:
> `base64` by itself encodes the given input into base64, since the data was already in base64 I used the `-d` switch to decode the data from base64
> 
2. The result of the above command gave me the output:
```bash
The password is IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR
```


Bandit11's password: IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR
