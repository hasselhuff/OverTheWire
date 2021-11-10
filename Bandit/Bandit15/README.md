# Bandit Level 15 → Level 16

Site: https://overthewire.org/wargames/bandit/bandit16.html
## Goal
> The password for the next level can be retrieved by submitting the password of the current level to ** port 30001 on localhost ** using SSL encryption.
> 
> 
> Helpful note: Getting “HEARTBEATING” and “Read R BLOCK”? Use -ign_eof and read the “CONNECTED COMMANDS” section in the manpage. 
> 
> Next to ‘R’ and ‘Q’, the ‘B’ command also works in this version of that command…

## Commands you may need to solve this level
> ssh, telnet, nc, openssl, s_client, nmap

## References:
* [Secure Socket Layer/Transport Layer Security on Wikipedia](https://en.wikipedia.org/wiki/Secure_Socket_Layer)
* [OpenSSL Cookbook - Testing with OpenSSL](https://www.feistyduck.com/library/openssl-cookbook/online/ch-testing-with-openssl.html)



-----------------

> username: bandit15
>
> password: BfMYroe26WYalil77FoDi9qh59eK5xNr
>
> server: bandit.labs.overthewire.org
>
> port: 2220

ssh into the server:
```bash
ssh -l bandit15 bandit.labs.overthewire.org -p 2220
```

1. Googled how to connect to servers with openssl and came up with the following:
```bash
openssl s_client -connect 127.0.0.1:30001
```
2. The output gave TLS information, and then stopped at a blank line. When I hit enter it disaplyed:
```bash
    Extended master secret: yes
---

Wrong! Please enter the correct current password
closed
```
3. I re-ran the command from step one but this time pasted `BfMYroe26WYalil77FoDi9qh59eK5xNr` when the line was blank and hit enter.
>
Output:
```bash
BfMYroe26WYalil77FoDi9qh59eK5xNr
Correct!
cluFn7wTiGryunymYOu4RcffSxQluehd

closed
```
Bandit16's password: cluFn7wTiGryunymYOu4RcffSxQluehd
