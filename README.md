### Date:
# Ex-5: Metasploit-for-reconnaissance
## Metasploit
Metasploit for reconnaissance in pentesting

## AIM:

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
### OUTPUT:
</br>

![1)](https://github.com/user-attachments/assets/0132360f-56b4-4f13-bdfd-6b92f0cdaf12)

Invoke msfconsole:
</br>
![2)](https://github.com/user-attachments/assets/2bdf0f50-d53a-4fdb-b638-3f6d774c1ab1)


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
</br>
![3)](https://github.com/user-attachments/assets/2d24b5bc-8eb7-4010-966c-0faea002d0b5)


## Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000
### OUTPUT:
</br>

![4)](https://github.com/user-attachments/assets/b66f8712-e30c-464e-a9e0-aa848c28861f)

Step_4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
### OUTPUT:
</br>

![5)](https://github.com/user-attachments/assets/0886345e-4981-47e6-b6ed-1deea8b3424c)


Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
### OUTPUT:
</br>

![6)](https://github.com/user-attachments/assets/adbd54c6-1411-40f0-9e30-7a8caa65103c)

Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit

The info command provides information regarding a module or platform,
### OUTPUT:
</br>

![7)](https://github.com/user-attachments/assets/60ab4bb3-fdbe-41c2-912a-17c03fff4d49)


Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## MYSQL ENUMERATION:
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>
</br>

![8)](https://github.com/user-attachments/assets/d565bd94-e516-406a-8198-c1450cfcd55d)

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
</br>

![9)](https://github.com/user-attachments/assets/0b38cede-395e-482b-9273-25eed7f4b21a)

use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11 Or: use auxiliary/scanner/mysql/mysql_version
</br>
![10](https://github.com/user-attachments/assets/17b4a9fc-fb44-4b75-908e-56b0e77a64fa)


Use the set rhosts command to set the parameter and run the module, as follows:
</br>

![11)](https://github.com/user-attachments/assets/43782d45-4c2a-4d3f-a5de-5236d4e854ea)


After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
</br>

![12)](https://github.com/user-attachments/assets/31104842-1963-4032-9b0b-4df892258e73)

set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
</br>

![13)](https://github.com/user-attachments/assets/7acb3041-15d7-4d5c-8689-1ac0d6be4add)

## RESULT:
The Metasploit framework for reconnaissance is  examined successfully.
