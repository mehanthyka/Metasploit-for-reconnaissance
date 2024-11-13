# Date
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

# PROGRAM:
Find out the ip address of the attackers system
## OUTPUT:
# ![image](https://github.com/Roselineb/Metasploit-for-reconnaissance/assets/128909895/596009e2-721a-464d-a5da-c2eddef9f229)

# Invoke msfconsole:
## OUTPUT:
# ![image](https://github.com/Roselineb/Metasploit-for-reconnaissance/assets/128909895/a921039a-ef67-48c4-a220-72f5d1988bf8)


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

# OUTPUT:


Port Scanning: Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000). msf > nmap -sT 192.168.1810/24 -p1-1000

# OUTPUT:
# ![image](https://github.com/Roselineb/Metasploit-for-reconnaissance/assets/128909895/c828d30e-6b39-458a-b7c3-dc060d1d8f36)


## Step4: use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.
scan the targets with the command db_nmap as follows. msf > db_nmap 192.168.181.0/24

# OUTPUT:
# ![image](https://github.com/Roselineb/Metasploit-for-reconnaissance/assets/128909895/de019dde-b084-477a-b11b-1d57c68ccec9)


Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules. cd /usr/share /metasploit-framework/modules/auxiliary kali > ls -l

# OUTPUT:
# ![image](https://github.com/Roselineb/Metasploit-for-reconnaissance/assets/128909895/d4643fe7-93ed-4ba7-ba3f-3b201ccccb87)
# ![image](https://github.com/Roselineb/Metasploit-for-reconnaissance/assets/128909895/525099e5-b9e9-4eff-bde6-6f2ea65e3e1e)


Search is a powerful command in Metasploit that you can use to find what you want to locate. msf >search name:Microsoft type:exploit

# ![image](https://github.com/Roselineb/Metasploit-for-reconnaissance/assets/128909895/0304bbcf-92c9-4a7b-b0f5-22e0182fa47f)


The info command provides information regarding a module or platform

# OUTPUT:
# ![image](https://github.com/Roselineb/Metasploit-for-reconnaissance/assets/128909895/e7286010-d75a-4197-bc5a-6f3840863850)


Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows: systemctl start postgresql msfdb init ##MYSQL ENUMERATION Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port. db_nmap -sV -sC -p 3306 <metasploitable_ip_address>
# ![image](https://github.com/Roselineb/Metasploit-for-reconnaissance/assets/128909895/060ca852-a89b-4a38-bcdc-55dadd9b8658)


Use the search option to look for an auxiliary module to scan and enumerate the MySQL database. search type:auxiliary mysql

# ![image](https://github.com/Roselineb/Metasploit-for-reconnaissance/assets/128909895/565df6c6-15d6-4837-ba9b-6cd729c028ed)


use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details. use 11 Or: use auxiliary/scanner/mysql/mysql_version

# ![image](https://github.com/Roselineb/Metasploit-for-reconnaissance/assets/128909895/cefefc7c-4546-4cfd-bde0-d025b387f58c)


Use the set rhosts command to set the parameter and run the module, as follows:

# ![image](https://github.com/Roselineb/Metasploit-for-reconnaissance/assets/128909895/3c2a2285-73ad-4998-88cf-15bc84189a20)


After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.

# ![image](https://github.com/Roselineb/Metasploit-for-reconnaissance/assets/128909895/54a679b7-b2dd-4f26-bdd4-524056ad09f3)


set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists: set PASS_FILE /usr/share/wordlistss/rockyou.txt Then, specify the IP address of the target machine with the RHOSTS command. set RHOSTS Set BLANK_PASSWORDS to true in case there is no password set for the root account. set BLANK_PASSWORDS true
# ![image](https://github.com/Roselineb/Metasploit-for-reconnaissance/assets/128909895/f358c88d-99ce-4560-bec1-44cc06350abc)





## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
