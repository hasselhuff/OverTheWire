# Bandit Level 8 → Level 9

Site: https://overthewire.org/wargames/bandit/bandit8.html
## Goal
> The password for the next level is stored in the file data.txt and is the only line of text that occurs only once

## Commands you may need to solve this level
> grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

## References
* [Piping and Redirection](https://ryanstutorials.net/linuxtutorial/piping.php)

-----------------

> username: bandit8
>
> password: cvX2JJa4CFALtqS87jk27qwqGhBM9plV
>
> server: bandit.labs.overthewire.org
>
> port: 2220

ssh into the server:
```bash
ssh -l bandit8 bandit.labs.overthewire.org -p 2220
```

1. Ran the following command with:
```bash
cat data.txt | sort | uniq -u
```
> Note:
> `sort` will sort the output of `cat data.txt` in descending order
> 
> `|` redirects the output from the previous command and sends it into the following command
> 
> `uniq` will show every unique line that is in the data
> 
> `uniq -u` will only show unique lines that are only displayed one time in the data
2. The result of the above command gave me the output:
```bash
UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR
```


Bandit9's password: UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR
