# Bandit Level 14 → Level 15

Site: https://overthewire.org/wargames/bandit/bandit14.html
## Goal
> The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

## Commands you may need to solve this level
> ssh, telnet, nc, openssl, s_client, nmap

## References:
* [How the Internet works in 5 minutes (YouTube) ](https://www.youtube.com/watch?v=7_LPdttKXPc) (Not completely accurate, but good enough for beginners)
* [IP Addresses](http://computer.howstuffworks.com/web-server5.htm)
* [IP Address on Wikipedia](https://en.wikipedia.org/wiki/IP_address)
* [Localhost on Wikipedia](https://en.wikipedia.org/wiki/Localhost)
* [Ports](http://computer.howstuffworks.com/web-server8.htm)
* [Port (computer networking) on Wikipedia](https://en.wikipedia.org/wiki/Port_(computer_networking))


-----------------

> username: bandit14
>
> password: 4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
>
> server: bandit.labs.overthewire.org
>
> port: 2220

ssh into the server:
```bash
ssh -l bandit14 bandit.labs.overthewire.org -p 2220
```

1. Ran the following command:
```bash
nc 127.0.0.1 30000
```
2. I used `nc` since it can read and send data to network connections and needed to send the current password to the localhost's (127.0.0.1) port 30000
3. After I entered the command my cursor only blinked on a new line, so I entered Bandit14's password and hit enter:
```bash
4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
```
4. I was then given the output:
```bash
Correct!
BfMYroe26WYalil77FoDi9qh59eK5xNr
```
Bandit15's password: BfMYroe26WYalil77FoDi9qh59eK5xNr
