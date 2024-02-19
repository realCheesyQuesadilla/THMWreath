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
