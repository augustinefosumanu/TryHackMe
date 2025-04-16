# [Zeek Exercises](https://tryhackme.com/room/zeekbroexercises)

## Walkthrough


### Task 2

**Investigate the dns-tunneling.pcap file. Investigate the dns.log file. What is the number of DNS records linked to the IPv6 address?**
```shell
cd /home/ubuntu/Desktop/Exercise-Files/anomalous-dns

zeek -Cr dns-tunneling.pcap

cat  dns.log |grep AAAA |wc -l

320
```
**Investigate the conn.log file. What is the longest connection duration?**
```shell
cat conn.log |zeek-cut duration |sort |uniq 

9.420791
```
**Investigate the dns.log file. Filter all unique DNS queries. What is the number of unique domain queries?**
```shell
cat dns.log | zeek-cut query |rev | cut -d '.' -f 1-2 | rev |sort |uniq |wc -l

6
```
**There are a massive amount of DNS queries sent to the same domain. This is abnormal. Let's find out which hosts are involved in this activity. Investigate the conn.log file. What is the IP address of the source host?**
```shell
cat conn.log | grep dns

10.20.57.3
```

### Task 3

**Investigate the logs. What is the suspicious source address? Enter your answer in defanged format.**
```shell
cd /home/ubuntu/Desktop/Exercise-Files/phishing

cat conn.log

10[.]6[.]27[.]102
```
**Investigate the http.log file. Which domain address were the malicious files downloaded from? Enter your answer in defanged format.**
```shell
cat http.log|zeek-cut host uri

smart-fax[.]com
```
**Investigate the malicious document in VirusTotal. What kind of file is associated with the malicious document?**

![image](https://github.com/user-attachments/assets/9e51340a-8a53-4f3a-8b6c-9ffe9dd50f93)
</br>
```shell
zeek -Cr phishing.pcap hash-demo.zeek 

cat files.log |zeek-cut md5 mime_type

VBA
```
**Investigate the extracted malicious .exe file. What is the given file name in Virustotal?**

![image](https://github.com/user-attachments/assets/cab54458-3108-4f2e-a73a-ee2fb4b5bd11)
</br>
```shell
zeek -Cr phishing.pcap file-extract-demo.zeek 

cd extract_files/

md5sum extract-1561667899.060086-HTTP-FOghls3WpIjKpvXaEl

PleaseWaitWindow.exe
```
**Investigate the malicious .exe file in VirusTotal. What is the contacted domain name? Enter your answer in defanged format.**
```shell
hopto[.]org
```
**Investigate the http.log file. What is the request name of the downloaded malicious .exe file?**
```shell
cat http.log |zeek-cut uri resp_mime_types

knr.exe
```

### Task 4

**Investigate the log4shell.pcapng file with detection-log4j.zeek script. Investigate the signature.log file. What is the number of signature hits?**
```shell
cd /home/ubuntu/Desktop/Exercise-Files/log4j

zeek -Cr log4shell.pcapng detection-log4j.zeek 

cat signatures.log|grep Signatures|wc -l

3
```
**Investigate the http.log file. Which tool is used for scanning?**
```shell
cat http.log

Nmap
```
**Investigate the http.log file. What is the extension of the exploit file?**
```shell
cat http.log|grep Exploit

.class
```
**Investigate the log4j.log file. Decode the base64 commands. What is the name of the created file?**

![image](https://github.com/user-attachments/assets/cab1edc6-c61f-4199-800c-ee6d11eee748)
</br>
```shell
head log4j.log

pwned
```
