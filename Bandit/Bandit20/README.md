# Bandit Level 20 → Level 21

Site: https://overthewire.org/wargames/bandit/bandit21.html
## Goal
> There is a setuid binary in the homedirectory that does the following: 
> 
> it makes a connection to localhost on the port you specify as a commandline argument. 
> 
> It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). 
> 
> If the password is correct, it will transmit the password for the next level (bandit21).

## NOTE:
> Try connecting to your own network daemon to see if it works as you think

## Commands you may need to solve this level: 
> ssh, nc, cat, bash, screen, tmux, Unix ‘job control’ (bg, fg, jobs, &, CTRL-Z, …)

-----------------

> username: bandit20
>
> password: GbKksEFF4yrVs6il55v6gwY5aVje5f0j
>
> server: bandit.labs.overthewire.org
>
> port: 2220

ssh into the server:
```bash
ssh -l bandit20 bandit.labs.overthewire.org -p 2220
```

1. Ran the binary found in the home directory:
```bash
./suconnect
```
Output:
```bash
Usage: ./suconnect <portnumber>
This program will connect to the given port on localhost using TCP. 
If it receives the correct password from the other side, the next password is transmitted back.
```
NOTE:
* It does not specify which port to use
* We will need to create a port that is waiting for a connection to transmit the current password
2. Open up `tmux` so we can have two interactive terminals on one screen:
```bash
tmux
```
3. Split the panel to have one screen on top and one screen on bottom:
> Press the following key combinations: `CTRL`+`B` then `SHIFT`+`"`
4. On one screen open up a port that is staging the current password:
```bash
cat /etc/bandit_pass/bandit20 | nc -lp 8888
```
NOTE:
* `cat` the file so that its piping the output to `nc`
* `-lp 8888` is to listen on port 8888
5. Switch to the other screen with the following combination:
> `CTRL`+`B` then either the up or the down arrow
6. Run the binary with the port we made as the arguement:
```bash
./suconnect 8888
```
Output:
```bash
Read: GbKksEFF4yrVs6il55v6gwY5aVje5f0j
Password matches, sending next password
```
Output on the screen with the `nc` command after the command executed:
```bash
gE269g2h3mw3pwgrj0Ha9Uoqen1c9DGr
```
7. Exit each `tmux` session by entering the command `exit`
>
Bandit21's password: GbKksEFF4yrVs6il55v6gwY5aVje5f0j
