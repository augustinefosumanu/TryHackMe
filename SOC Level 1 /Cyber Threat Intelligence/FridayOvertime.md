# [Friday Overtime](https://tryhackme.com/room/fridayovertime)

## Walkthrough

## Task 1

**Who shared the malware samples?**
```shell
Oliver Bennett
```
**What is the SHA1 hash of the file "pRsm.dll" inside samples.zip?**
```shell
cd ~/Downloads

unzip samples.zip
Password: Panda321!

sha1sum pRsm.dll

9d1ecbbe8637fed0d89fca1af35ea821277ad2e8
```
**Which malware framework utilizes these DLLs as add-on modules?**
```shell
MgBot
```
**Which MITRE ATT&CK Technique is linked to using pRsm.dll in this malware framework?**
```shell
T1123
```
**What is the CyberChef defanged URL of the malicious download location first seen on 2020-11-02?**
```shell
hxxp[://]update[.]browser[.]qq[.]com/qmbs/QQ/QQUrlMgr_QQ88_4296[.]exe
```
**What is the CyberChef defanged IP address of the C&C server first detected on 2020-09-14 using these modules?**
```shell
122[.]10[.]90[.]12
```
**What is the SHA1 hash of the spyagent family spyware hosted on the same IP targeting Android devices on November 16, 2022?**
```shell
1c1fe906e822012f6235fcc53f601d006d15d7be
```
