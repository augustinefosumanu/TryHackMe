# [Osquery: The Basics](https://tryhackme.com/room/osqueryf8)

## Walkthrough

## Task 3

**How many tables are returned when we query "table process" in the interactive mode of Osquery?**
```shell
.table process

3
```
**Looking at the schema of the processes table, which column displays the process id for the particular process?**
```shell
.schema processes

pid
```
**Examine the .help command, how many output display modes are available for the .mode command?**
```shell
.help

5
```

## Task 

**In Osquery version 5.5.1, how many common tables are returned, when we select both Linux and Window Operating system?**
```shell
56
```
**In Osquery version 5.5.1, how many tables for MAC OS are available?**
```shell
180
```
**In the Windows Operating system, which table is used to display the installed programs?**
```shell
programs
```
**In Windows Operating system, which column contains the registry value within the registry table?**
```shell
data
```

## Task 5

**Using Osquery, how many programs are installed on this host?**
```shell
Select count(*) from programs;

19
```
**Using Osquery, what is the description for the user James?**
```shell
select * from users where username='James';

Creative Artist
```
**When we run the following search query, what is the full SID of the user with RID '1009'?
Query: select path, key, name from registry where key = 'HKEY_USERS';**
```shell
 S-1-5-21-1966530601-3185510712-10604624-1009
```
**When we run the following search query, what is the Internet Explorer browser extension installed on this machine?
Query: select * from ie_extensions;**
```shell
C:\Windows\System32\ieframe.dll
```
**After running the following query, what is the full name of the program returned?
Query: select name,install_location from programs where name LIKE '%wireshark%';**
```shell
Wireshark 4.4.9 x64
```

## Task 6

**Which table stores the evidence of process execution in Windows OS?**
```shell
userassist
```
**One of the users seems to have executed a program to remove traces from the disk; what is the name of that program?**
```shell
select * from userassist;

DiskWipe.exe
```
**Create a search query to identify the VPN installed on this host. What is name of the software?**
```shell
select * from programs where name like '%vpn%';

ProtonVPN
```
**How many services are running on this host?**
```shell
select count(*) from services;

215
```
**A table autoexec contains the list of executables that are automatically executed on the target machine. There seems to be a batch file that runs automatically. What is the name of that batch file (with the extension .bat)?**
```shell
select * from autoexec where name like '%.bat%';

batstartup.bat
```
**What is the full path of the batch file found in the above question? (Last in the List)**
```shell
C:\Users\James\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup\batstartup.bat
```
