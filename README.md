# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting

# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find out the ip address of the attackers system
## OUTPUT:
![Alt Text](1.png)


Invoke msfconsole:
## OUTPUT:
<img width="688" height="645" alt="2" src="https://github.com/user-attachments/assets/394a93e0-4dd5-4006-80c7-44dbeeb7803c" />


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
<img width="701" height="832" alt="3" src="https://github.com/user-attachments/assets/2460c87c-d5cf-4b31-9891-4165be1ca933" />




Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000  (Replace with appropriate IP Address)
## OUTPUT:
<img width="594" height="648" alt="4" src="https://github.com/user-attachments/assets/96fe1a49-82b1-4fc9-9d9a-e6b66208e52c" />

step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:

<img width="697" height="685" alt="5" src="https://github.com/user-attachments/assets/c15bb563-09be-44d0-b792-3fdcdd5a1b2b" />


Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l

## OUTPUT:

<img width="638" height="528" alt="6" src="https://github.com/user-attachments/assets/f9f0ba04-10f2-469c-b281-250d19a0da81" />


Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT:


<img width="641" height="564" alt="7" src="https://github.com/user-attachments/assets/61f34485-d0ba-41b1-83e1-c54f728c0460" />


The info command provides information regarding a module or platform,

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## OUTPUT:

<img width="643" height="525" alt="8" src="https://github.com/user-attachments/assets/d97405ba-a7f7-4ada-b1e1-cc78ece5f899" />



## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>


<img width="631" height="377" alt="9" src="https://github.com/user-attachments/assets/d42373f8-5321-463a-bf94-2ff6c0b75ca2" />

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql


<img width="667" height="556" alt="10" src="https://github.com/user-attachments/assets/7dfccf03-316d-4d8a-84d6-aa5c48efbc04" />


use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
## OUTPUT:

<img width="653" height="535" alt="11" src="https://github.com/user-attachments/assets/89e6f678-9205-4866-ad30-6d1022102e52" />


Use the set rhosts command to set the parameter and run the module, as follows:
## OUTPUT:

<img width="641" height="147" alt="12" src="https://github.com/user-attachments/assets/893347d0-346c-4159-aa12-76061ed3d3b4" />


After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.

## OUTPUT:

<img width="651" height="406" alt="13" src="https://github.com/user-attachments/assets/e182a4f3-9f88-4e3d-93c5-1c90e162a54f" />



set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
## OUTPUT:

<img width="658" height="267" alt="14" src="https://github.com/user-attachments/assets/4c05cdfa-3a56-4332-b550-d7ad48954bdc" />





## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
