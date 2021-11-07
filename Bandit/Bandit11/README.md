# Bandit Level 11 → Level 12

Site: https://overthewire.org/wargames/bandit/bandit11.html
## Goal
> The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

## Commands you may need to solve this level
> grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

## References:
* [Rot13 on Wikipedia](https://en.wikipedia.org/wiki/Rot13)

-----------------

> username: bandit11
>
> password: IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR
>
> server: bandit.labs.overthewire.org
>
> port: 2220

ssh into the server:
```bash
ssh -l bandit11 bandit.labs.overthewire.org -p 2220
```

1. Ran the following command:
```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```
> Note:
> `tr` translates/ deletes characters
> 
> `'A-Za-z'` is the range of characters I want `tr` top match on (which is all alphabetical characters from A-Z and a-z)
> 
> `'N-ZA-Mn-za-m'` is what I want to translate the characters to (note I start N to signify 13 characters from A)
2. The result of the above command gave me the output:
```bash
The password is 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu
```


Bandit12's password: 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu
