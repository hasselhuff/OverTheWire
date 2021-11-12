# Bandit Level 17 → Level 18

Site: https://overthewire.org/wargames/bandit/bandit18.html
## Goal
> There are 2 files in the homedirectory: **passwords.old and passwords.new**. 
> 
> The password for the next level is in **passwords.new** and is the only line that has been changed between **passwords.old and passwords.new**

## NOTE: 
> if you have solved this level and see ‘Byebye!’ when trying to log into bandit18, this is related to the next level, bandit19

## Commands you may need to solve this level
> cat, grep, ls, diff

-----------------

> username: bandit17
>
> password: xLYVMN9WE5zQ5vHacb0sZEVqbrp7nBTn
>
> server: bandit.labs.overthewire.org
>
> port: 2220

ssh into the server:
```bash
ssh -l bandit17 bandit.labs.overthewire.org -p 2220
```

1. Ran `diff` to see the differences between the two files:
```bash
diff passwords.old passwords.new
```
Output:
```bash
42c42
< w0Yfolrc5bwjS4qw5mq1nnQi6mF03bii
---
> kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd
```
2. Since the instructions said their was only a difference in the `passwords.new` I will use `kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd` for an ssh attempt.
```bash
ssh -l bandit18 bandit.labs.overthewire.org -p 2220
```
Output (last few lines):
```bash
  Enjoy your stay!

Byebye !
Connection to bandit.labs.overthewire.org closed.
```
3. The ssh attempt was a success.


Bandit18's password: kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd
