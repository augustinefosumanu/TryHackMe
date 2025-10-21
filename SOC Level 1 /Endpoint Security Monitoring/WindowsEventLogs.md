# [Windows Event Logs](https://tryhackme.com/room/windowseventlogs)

## Walkthrough

## Task 2

**What is the Event ID for the earliest recorded event?**
```shell
40961
```
**Filter on Event ID 4104. What was the 2nd command executed in the PowerShell session?**
```shell
whoami
```
**What is the Task Category for Event ID 4104?**
```shell
Execute a Remote Command
```
**Analyze the Windows PowerShell log. What is the Task Category for Event ID 800?**
```shell
Pipeline Execution Details
```

## Task 3

**How many log names are in the machine?**
```shell
wevtutil el | Measure-Object

1071
```
**What event files would be read when using the query-events command?**
```shell
wevtutil qe /?

event log, log file, structured query
```
**What option would you use to provide a path to a log file?**
```shell
/lf:true
```
**What is the VALUE for /q?**
```shell
XPath query
```
**The questions below are based on this command: wevtutil qe Application /c:3 /rd:true /f:text
What is the log name?**
```shell
Application
```
**What is the /rd option for?**
```shell
Event read direction
```
**What is the /c option for?**
```shell
Maximum number of events to read
```

## Task 4

**Execute the command from Example 1 (as is). What are the names of the logs related to OpenSSH?**
```shell
Get-WinEvent -Listlog *

OpenSSH/Admin,OpenSSH/Operational
```
**Execute the command from Example 8. Instead of the string *Policy* search for *PowerShell*. What is the name of the 3rd log provider?**
```shell
Get-WinEvent -ListProvider *PowerShell*

Microsoft-Windows-PowerShell-DesiredStateConfiguration-FileDownloadManager
```
**Execute the command from Example 9. Use Microsoft-Windows-PowerShell as the log provider. How many event ids are displayed for this event provider?**
```shell
(Get-WinEvent -ListProvider Microsoft-Windows-PowerShell).Events |
    Format-Table Id, Description | Measure-Object

192
```
**How do you specify the number of events to display?**
```shell
-MaxEvents
```
**When using the FilterHashtable parameter and filtering by level, what is the value for Informational?**
```shell
4
```

## Task 5

**Using the knowledge gained on Get-WinEvent and XPath, what is the query to find WLMS events with a System Time of 2020-12-15T01:09:08.940277500Z?**
```shell
Get-WinEvent -LogName Application -FilterXPath '*/System/Provider[@Name="WLMS"] and */System/TimeCreated[@SystemTime="2020-12-15T01:09:08.940277500Z"]'
```
**Using Get-WinEvent and XPath, what is the query to find a user named Sam with an Logon Event ID of 4720?**
```shell
Get-WinEvent -LogName Security -FilterXPath '*/EventData/Data[@Name="TargetUserName"]="Sam" and */System/EventID=4720'
```
**Based on the previous query, how many results are returned?**
```shell
2
```
**Based on the output from the question #2, what is Message?**
```shell
A user account was created
```
**Still working with Sam as the user, what time was Event ID 4724 recorded? (MM/DD/YYYY H:MM:SS [AM/PM])**
```shell
12/17/2020 1:57:14 PM
```
**What is the Provider Name?**
```shell
Microsoft-Windows-Security-Auditing
```

## Task 7

**What event ID is to detect a PowerShell downgrade attack?**
```shell
400
```
**What is the Date and Time this attack took place? (MM/DD/YYYY H:MM:SS [AM/PM])**
```shell
12/18/2020 7:50:33 AM
```
**A Log clear event was recorded. What is the 'Event Record ID'?**
```shell
27736
```
**What is the name of the computer?**
```shell
PC01.example.corp
```
**What is the name of the first variable within the PowerShell command?**
```shell
$Va5w3n8
```
**What is the Date and Time this attack took place? (MM/DD/YYYY H:MM:SS [AM/PM])**
```shell
8/25/2020 10:09:28 PM
```
**What is the Execution Process ID?**
```shell
6620
```
**What is the Group Security ID of the group she enumerated?**
```shell
cd C:\Users\Administrator

Get-WinEvent -Path .\\Desktop\\merged.evtx -FilterXPath '*/EventData/Data[@Name="CallerProcessName"]="C:\Windows\System32\net1.exe"' | Format-List

S-1-5-32-544
```
**What is the event ID?**
```shell
4799
```

