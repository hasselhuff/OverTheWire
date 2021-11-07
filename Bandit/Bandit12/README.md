# Bandit Level 12 → Level 13

Site: https://overthewire.org/wargames/bandit/bandit12.html
## Goal
> The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. 
> 
> For this level it may be useful to create a directory under /tmp in which you can work using mkdir. 
> 
> For example: mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv (read the manpages!)

## Commands you may need to solve this level
> grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd, mkdir, cp, mv, file

## References:
> https://en.wikipedia.org/wiki/Hex_dump

-----------------

> username: bandit12
>
> password: 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu
>
> server: bandit.labs.overthewire.org
>
> port: 2220

ssh into the server:
```bash
ssh -l bandit12 bandit.labs.overthewire.org -p 2220
```

1. Made a directory in `/tmp` to create a workspace:
```bash
mkdir /tmp/2021test
```
2.  Since `data.txt` is an ouytput of a hexdump we need to convert the hexdump back into a file:
```bash
cat data.txt | xxd -r > /tmp/2021test/test
```
3. Lets move into the new directory and see what file we have:
```bash
cd /tmp/2021test
file test
```
4. Out outpur shows it is a `gzip compressed data` so we will need to rename the file for `gunzip` to see it:
```bash
mv test test.gz
gunzip test.gz
```
5. I then did a `file` on `test` to determine the file type and proceeded with the appropriate archive utility to decompress:
```bash
bunzip2 test              # this command changed the file from test to test.out
mv test.out test.gz
gunzip test.gz
tar -xvf test             # decompressed file was renamed to data5.bin
tar -xvf data5.bin        # decompressed file was renamed to data6.bin
bunzip2 data6.bin         # decompressed file was renamed to data6.bin.out
tar -xvf data6.bin.out    # decompressed file was renamed to data8.bin
mv data8.bin data8.gz
gunzip data8.gz           # decompresses file was renamed to data8
```
6. When I ran `file` on data8 it displayed `ASCII text` so I know I was ready to `cat data8` which gave me:
```bash
The password is 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL
```


Bandit13's password: 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL
