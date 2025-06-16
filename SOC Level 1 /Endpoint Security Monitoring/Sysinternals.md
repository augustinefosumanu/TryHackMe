# [Sysinternals](https://tryhackme.com/room/btsysinternalssg)

## Walkthrough

## Task 1

**When did Microsoft acquire the Sysinternals tools?**
```shell
2006
```

## Task 2

**What is the last tool listed within the Sysinternals Suite?**
```shell
ZoomIt
```

## Task 3

**What service needs to be enabled on the local host to interact with live.sysinternals.com?**
```shell
WebClient
```

## Task 4
![image](https://github.com/user-attachments/assets/a2f6d65b-77e9-49a5-afc0-05c3dbc2e12c)
</br>
**There is a txt file on the desktop named file.txt. Using one of the three discussed tools in this task, what is the text within the ADS?**
```shell
I am hiding in the stream.
```

## Task 5

**Using WHOIS tools, what is the ISP/Organization for the remote address in the screenshots above?**
```shell
Microsoft Corporation
```

## Task 6
![image](https://github.com/user-attachments/assets/5c8e4005-f0de-4d90-ae4d-75df6a820014)
</br>
**What entry was updated?**
```shell
c:\Users\Adminstrator> autoruns
```
**What is the updated value?**
```shell
c:\tools\sysint\procexp.exe
```

## Task 9
![image](https://github.com/user-attachments/assets/a9bcd782-2a32-41ca-8c0e-eb6cc6ea9151)
</br>
**Run the Strings tool on ZoomIt.exe. What is the full path to the .pdb file?**
```shell
strings .\ZoomIt.exe | findstr /i zoom*

C:\agent\_work\112\s\Win32\Release\ZoomIt.pdb
```
