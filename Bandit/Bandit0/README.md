# Bandit Level 0 → Level 1

Site: https://overthewire.org/wargames/bandit/bandit1.html
## Goal
> The password for the next level is stored in a file called readme located in the home directory. 
> Use this password to log into bandit1 using SSH. 
> Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

## Commands you may need to solve this level
> ls, cd, cat, file, du, find
-----------------

From the [Level 0](https://overthewire.org/wargames/bandit/bandit0.html) page:
> username: bandit0
>
> password: bandit0
> 
> server: bandit.labs.overthewire.org
> 
> port: 2220

I ssh'ed into the server using:
```bash
ssh -l bandit0 bandit.labs.overthewire.org -p 2220
```

1. Ran an `ls` to list the contents of `bandit0`'s home directory
2. Noticed a file called `readme`.
3. Concatenated  the `readme` file with `cat`
```bash
cat readme
```
Which uncovers bandit1's password.
