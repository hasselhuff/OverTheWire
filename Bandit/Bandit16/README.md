# Bandit Level 16 → Level 17

Site: https://overthewire.org/wargames/bandit/bandit17.html
## Goal
> The credentials for the next level can be retrieved by submitting the password of the current level 
> 
> to ** a port on localhost in the range 31000 to 32000**. First find out which of these ports have a server listening on them. 
> 
> Then find out which of those speak SSL and which don’t. There is only 1 server that will give the next credentials, 
> 
> the others will simply send back to you whatever you send to it.

## Commands you may need to solve this level
> ssh, telnet, nc, openssl, s_client, nmap

## References:
* [Port scanner on Wikipedia](https://en.wikipedia.org/wiki/Port_scanner)

-----------------

> username: bandit16
>
> password: cluFn7wTiGryunymYOu4RcffSxQluehd
>
> server: bandit.labs.overthewire.org
>
> port: 2220

ssh into the server:
```bash
ssh -l bandit16 bandit.labs.overthewire.org -p 2220
```

1. Ran the following nmap scan to see listening ports:
```bash
 nmap -sV 127.0.0.1 -p 31000-32000 -vv
```
## NOTE:
* `sV` switch is used to list service name's and versions on ports
* `-p 31000-32000` to scan the range of ports in one scan
* `-vv` for very verbose so you can monitor the scan progress
Output (of the ports):
```bash
PORT      STATE SERVICE     REASON  VERSION
31046/tcp open  echo        syn-ack
31518/tcp open  ssl/echo    syn-ack
31691/tcp open  echo        syn-ack
31790/tcp open  ssl/unknown syn-ack
31960/tcp open  echo        syn-ack
```
2. Run the command from the previous level on `31790` since the other has`/echo`:
```bash
openssl s_client -connect 127.0.0.1:31790
```
3. When prompted with a blank line I entered `cluFn7wTiGryunymYOu4RcffSxQluehd` and the ouput displayed:
```bash
---
cluFn7wTiGryunymYOu4RcffSxQluehd
Correct!
-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----

closed
```
4. Now we need to make a file to store the private key, copy the key (including the BEGIN AND END lines) and paste it into the new file:
```bash
mkdir /tmp/2021ssh
touch /tmp/2021ssh/id.rsa
vim /tmp/2021ssh/id.rsa
```
In vim:
* Click `i` to enter "Insert" mode
* Paste the entire private key
* Click `esc` key to exit "Insert" mode
* Now click `:` to enter "Command" mode
* Enter `wq!` and then hit enter to write and save the file
5. Now make the file only readable by bandit16 (requirement for private key files)
```bash
chmod 400 /tmp/2021ssh/id.rsa
```
6. Now ssh as bandit17:
```bash
ssh -i /tmp/2021ssh/id.rsa bandit17@127.0.0.1
```
7. Ready bandit17's password file
```bash
cat /etc/bandit_pass/bandit17
```
Output:
```bash
xLYVMN9WE5zQ5vHacb0sZEVqbrp7nBTn
```


Bandit17's password: xLYVMN9WE5zQ5vHacb0sZEVqbrp7nBTn
