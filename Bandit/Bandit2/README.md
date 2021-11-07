# Bandit Level 2 → Level 3

Site: https://overthewire.org/wargames/bandit/bandit3.html
## Goal
> The password for the next level is stored in a file called spaces in this filename located in the home directory

## Commands you may need to solve this level
> ls, cd, cat, file, du, find

## Resources
* [Google Search for “spaces in filename”](https://www.google.com/search?q=spaces+in+filename)
-----------------

> username: bandit2
>
> password: CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9
>
> server: bandit.labs.overthewire.org
>
> port: 2220

ssh into the server:
```bash
ssh -l bandit2 bandit.labs.overthewire.org -p 2220
```

1. Ran an `ls` to list the contents in the directory
2. Noticed a file called `spaces in this filename`
## Option 1
1. Insert a `\` before placing a `space` between each word in the file name
> Note:
> `\` tells the system to read the next character as a string if it has more than one way for the system to interpret it
```bash
cat spaces\ in\ this\ filename
```
## Option 2
1. To concatenate a file that is in the current directory you preface the file with `./`
2. Since this is the only file in the directory that begins with the letter `s`, type in `s` then hit tab to complete
```bash
cat ./s
```

Bandit3's password: UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK
