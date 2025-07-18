# HackTheBox – Cap

## Task 1
How many TCP ports are open?
For this task i used the command `sudo nmap -p- --min-rate 10000 -Pn -oA scans/nmap-alltcp 10.10.10.245` 
it scans all the tcp ports across all the ports it returned 

## Open Ports

| Port     | State | Service |
|----------|-------|---------|
| 21/tcp   | open  | ftp     |
| 22/tcp   | open  | ssh     |
| 80/tcp   | open  | http    |


## Task 2
After running a "Security Snapshot", the browser is redirected to a path of the format /something/[id], where [id] represents the id number of the scan. What is the [something]?
data

After going to the `http://10.10.10.245` and going to the pcap analysis section and looking at the url 
`http://10.10.10.245/data/6` we understand that before the id the something mentioned is data

## Task 3
Are you able to get to other users' scans?

We are able to look at other users scans by changing the id in the url

## Task 4
What is the ID of the PCAP file that contains sensitive data?

`http://10.10.10.245/data/0` contains the sensitive data

## Task 5
Which application layer protocol in the pcap file can the sensitive data be found in?
ftp(file transmission protocol) 

## Task 6
We've managed to collect nathan’s FTP password. On what other service does this password work?
ssh
`ssh nathan@10.10.10.245`
## Task 7
Submit the flag located in the nathan user’s home directory.
User flag owned

after logging in as nathan we can accesses nathan homedirectory and acess the file `user.txt` which contains the password

## Task 8
What is the full path to the binary on this machine that can be abused to obtain root privileges?

/usr/bin/python3.8
using the command `getcap -r / 2>/dev/null` we get the posix capabilities of binaries on this machine

## Task 9 
Submit the flag located in root’s home directory.

after logging in as root we view the root.txt file which conatins the final flag
