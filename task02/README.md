## Objective: Crack SSH login credentials via brute-force and retrieve the flag.

## Task 1
we just had to deploy the machine nothing much to do

## Task 2
Reconnaissance
First, identify open ports and services on the target machine.
`nmap -sS -sV -Pn -T4 10.10.222.82` (this helps us find the open ports)
`nmap -sCV -p22,80  10.10.222.82` (from the open ports we can find more information on it)
### How many ports are open?
2
### What version of SSH is running?
OpenSSH 7.6p1
### What version of Apache is running?
2.4.29
### Which Linux distribution is running?
Ubuntu
### Search for hidden directories on web server.
What is the hidden directory?
/admin
on the `10.10.222.82/admin` page we see a login page

## Task 3
we inspect the `10.10.222.82/admin` page and find out the usename is 'admin' but the password we dont know for thi swe use the brute forcing tool hydra
with the file 'rockyou.txt'
`hydra -l nehamanoj100 -P /usr/share/wordlists/rockyou.txt -t 4 ssh://10.10.222.82`
hydra will try all passwords from rockyou.txt for the username
this takes some time but finds the password to be 'xavier`
#### Explanation:
##### - `-l` specifies the username
##### - `-P` specifies the password wordlist
##### - `-t 4` sets the number of parallel tasks
##### - `ssh://` defines the service and target

### Crack the RSA key you found.
after logiing in with the found username and password get the rsa key 

### What is John's RSA Private Key passphrase?
rocknroll
for this we use the tool johntheripper
we create a hash file from id_rsa using a python script named ssh2john.py
with the hash file we use john to work on cracking it and we get the password as rocknroll

### user.txt
we log in as john and access the user.txt file within
THM{a_password_is_not_a_barrier}

### Web flag
when we logged in as admin password: xavier the web flag was dispalyed
THM{brut3_f0rce_is_e4sy}

## Task 4 
`sudo cat /etc/shadow` 
this gives us a hash we dont know what kind of hash is used 
so we use a tool called the hash-identifier
and we find out it is hashed with SHA-256

### What is the root's password?
football
using `hashcat -m 1880 roothash /usr/share/wordlists/rockyou.txt`
we find the root password as football

### Final Flag
After this we log in as root and access root.txt and in it we find the final flag
THM{prv1l3g3g3_3sc4l4t10n}

| Category         | Details                                     |
|------------------|----------------------------------------------|
| **Techniques Used** | - brute force attack using hydra and dictionary (rockyou.txt) |
| **Tools Used**      | - nmap<br>- hydra<br>- rockyou.txt (common wordlist) |
| **Flags Captured**  | - **User Flag**: `THM{a_password_is_not_a_barrier}`<br>- **Web Flag**: `THM{brut3_f0rce_is_e4sy}`<br>- **Root Flag**: `THM{prv1l3g3g3_3sc4l4t10n}` |

