# [Snort Challenge - The Basics](https://tryhackme.com/room/snortchallenges1)

## Walkthrough

## Task 2

**Navigate to the task folder and use the given pcap file.
Write a rule to detect all TCP packets from or to port 80.
What is the number of detected packets you got?
Note: You must answer this question correctly before answering the rest of the questions.**
```shell
cd Desktop/Exercise-Files/'TASK-2 (HTTP)'

sudo nano local.rules

alert tcp any 80 <> any any (msg: "src-port 80 packets found"; sid: 1000001; rev: 1;)
alert tcp any any <> any 80 (msg: "des-port 80 packets found"; sid: 1000001; rev: 1;)

164
```
**Investigate the log file.
What is the destination address of packet 63?**
```shell
sudo snort -Xr snort.log.1744575245 -n 126

216.239.59.99
```
**Investigate the log file.
What is the ACK number of packet 64?**
```shell
sudo snort -Xr snort.log.1744575245 -n 128

0x2E6B5384
```
**Investigate the log file.
What is the SEQ number of packet 62?**
```shell
sudo snort -Xr snort.log.1744575245 -n 124

0x36C21E28
```
**Investigate the log file.
What is the TTL of packet 65?**
```shell
sudo snort -Xr snort.log.1744575245 -n 130

128
```
**Investigate the log file.
What is the source IP of packet 65?**
```shell
sudo snort -Xr snort.log.1744575245 -n 130

145.254.160.237
```
**Investigate the log file.
What is the source port of packet 65?**
```shell
sudo snort -Xr snort.log.1744575245 -n 130

3372
```

## Task 3

**Navigate to the task folder.
Use the given pcap file.
Write a single rule to detect "all TCP port 21"  traffic in the given pcap.
What is the number of detected packets?**
```shell
cd Desktop/Exercise-Files/'TASK-3 (FTP)'

sudo nano local.rules

alert tcp any any <> any 21 (msg: "ftp packets detected"; sid: 1000001; rev: 1;)

sudo snort -c local.rules -A full -l . -r ftp-png-gif.pcap

307
```
**Investigate the log file.
What is the FTP service name?**
```shell
sudo snort -Xr snort.log.1744576391

Microsoft FTP Service
```
**Clear the previous log and alarm files.
Deactivate/comment on the old rules.
Write a rule to detect failed FTP login attempts in the given pcap.
What is the number of detected packets?**
```shell
alert any any <> any 21 (msg: "Failed Login Detected"; content: "530 User"; sid: 1000001; rev: 1;)

sudo snort -c local.rules -A full -l . -r ftp-png-gif.pcap

41
```
**Clear the previous log and alarm files.
Deactivate/comment on the old rule.
Write a rule to detect successful FTP logins in the given pcap.
What is the number of detected packets?**
```shell
alert any any <> any 21 (msg: "Successful Login Detected"; content: "230 User"; sid: 1000001; rev: 1;)

sudo snort -c local.rules -A full -l . -r ftp-png-gif.pcap

1
```
**Clear the previous log and alarm files.
Deactivate/comment on the old rule.
Write a rule to detect FTP login attempts with a valid username but no password entered yet.
What is the number of detected packets?**
```shell
alert any any <> any 21 (msg: "Failed Login Detected"; content: "331 Password"; sid: 1000001; rev: 1;)

sudo snort -c local.rules -A full -l . -r ftp-png-gif.pcap

42
```
**Clear the previous log and alarm files.
Deactivate/comment on the old rule.
Write a rule to detect FTP login attempts with the "Administrator" username but no password entered yet.
What is the number of detected packets?**
```shell
alert any any <> any 21 (msg: "Failed Login Detected"; content: "Administrator"; content: "331 Password"; sid: 1000001; rev: 1;)

sudo snort -c local.rules -A full -l . -r ftp-png-gif.pcap

7
```

## Task 

****
```shell

```
****
```shell

```
****
```shell

```
****
```shell

```
****
```shell

```
****
```shell

```
****
```shell

```
****
```shell

```

