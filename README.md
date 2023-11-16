# Metasploit-for-reconnaissance
Metasploit for reconnaissance in pentesting

# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

1) Install kali linux either in partition or virtual box or in live mode
2) Investigate on the various categories of tools as follows
3) Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find out the ip address of the attackers system

![m1](https://github.com/anto-richard/Metasploit-for-reconnaissance/assets/93427534/adf4ec44-2581-4c00-b5af-f13d1f7ccf08)




Invoke msfconsole:

![m2](https://github.com/anto-richard/Metasploit-for-reconnaissance/assets/93427534/c4d90c44-8307-4444-9a38-91f7daf536de)




Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

![m3](https://github.com/anto-richard/Metasploit-for-reconnaissance/assets/93427534/72d651bd-c819-4fc9-aa9e-f2165b561374)




Port Scanning:

Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000). msf > nmap -sT 192.168.1810/24 -p1-1000

## OUTPUT:

![m4](https://github.com/anto-richard/Metasploit-for-reconnaissance/assets/93427534/97d087a9-a567-4411-b720-6bab7ba0844b)




USE the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows. msf > db_nmap 192.168.181.0/24


## OUTPUT:

![m5](https://github.com/anto-richard/Metasploit-for-reconnaissance/assets/93427534/c5f2dddc-f5ef-4558-af96-393fc1df021a)




Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules. cd /usr/share /metasploit-framework/modules/auxiliary kali > ls -l

## OUTPUT:

![m6](https://github.com/anto-richard/Metasploit-for-reconnaissance/assets/93427534/e2ce0ce4-41c5-4b53-815a-71f6b71cfeb9)



Search is a powerful command in Metasploit that you can use to find what you want to locate. msf >search name:Microsoft type:exploit

The info command provides information regarding a module or platform,

## OUTPUT
![m7](https://github.com/anto-richard/Metasploit-for-reconnaissance/assets/93427534/1a80a194-56c9-41df-a515-1c408ac47b77)



Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows: systemctl start postgresql msfdb init

## MYSQL ENUMERATION

Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port. db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

![m8](https://github.com/anto-richard/Metasploit-for-reconnaissance/assets/93427534/374db01c-16c6-4e7e-8069-ba1702ce2ba0)



Use the search option to look for an auxiliary module to scan and enumerate the MySQL database. search type:auxiliary mysql

![m9](https://github.com/anto-richard/Metasploit-for-reconnaissance/assets/93427534/44b4167c-478a-434e-b741-b39e768e938b)




use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details. use 11 Or: use auxiliary/scanner/mysql/mysql_version
![m10](https://github.com/anto-richard/Metasploit-for-reconnaissance/assets/93427534/6cf83232-66ca-49c9-945c-95c86c77edb2)




Use the set rhosts command to set the parameter and run the module, as follows:

![m12](https://github.com/anto-richard/Metasploit-for-reconnaissance/assets/93427534/505398f3-66dd-497a-9a61-47f9a94e4418)





After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.

![m13](https://github.com/anto-richard/Metasploit-for-reconnaissance/assets/93427534/2b98dd3a-689e-42de-860d-8b6c01c85fe6)






set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists: set PASS_FILE /usr/share/wordlistss/rockyou.txt Then, specify the IP address of the target machine with the RHOSTS command. set RHOSTS Set BLANK_PASSWORDS to true in case there is no password set for the root account. set BLANK_PASSWORDS true

![m14](https://github.com/anto-richard/Metasploit-for-reconnaissance/assets/93427534/c60080cb-7292-439a-af18-51cd7b53a3b4)







## RESULT:

The Metasploit framework for reconnaissance is  examined successfully
