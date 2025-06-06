# [Core Windows Processes](https://tryhackme.com/room/btwindowsinternals)

## Walkthrough

![image](https://github.com/user-attachments/assets/7e6a66ba-e336-45e8-9fd6-6cb0a9fa0cce)
</br>

## Task 3

**What PID should System always be?**
```shell
4
```

## Task 4

**Aside from csrss.exe, what process does smss.exe spawn in Session 1?**
```shell
winlogon.exe
```

## Task 5

**What was the process which had PID 384 and PID 488?**
```shell
smss.exe
```

## Task 6

![image](https://github.com/user-attachments/assets/3f9c7d49-a2bd-46c7-b953-692508d066c7)
</br>
**Which process might you not see running if Credential Guard is not enabled?**
```shell
lsaiso.exe
```

## Task 7

**How many instances of services.exe should be running on a Windows system?**
```shell
1
```

## Task 8

**What single letter parameter should always be visible in the Command line or Binary path?**
```shell
k
```

## Task 9

**What is the parent process for LSASS?**
```shell
wininit.exe
```

## Task 10

**What is the non-existent parent process for winlogon.exe?**
```shell
smss.exe
```

## Task 11

**What is the non-existent process for explorer.exe?**
```shell
userinit.exe
```
