# [Zeek](https://tryhackme.com/room/zeekbro)

## Walkthrough


## Task 2

**What is the installed Zeek instance version number?**
```shell
zeek -v

4.2.1
```
**What is the version of the ZeekControl module?**
```shell
zeekctl

2.4.0
```

**Investigate the "sample.pcap" file. What is the number of generated alert files?**
```shell
cd /home/ubuntu/Desktop/Exercise-Files/TASK-2

zeek -C -r sample.pcap

ls -l

8
```

## Task 3

**Investigate the sample.pcap file. Investigate the dhcp.log file. What is the available hostname?**
```shell
cd /home/ubuntu/Desktop/Exercise-Files/TASK-3

zeek -C -r sample.pcap

cat dhcp.log |zeek-cut host_name

Microknoppix
```
**Investigate the dns.log file. What is the number of unique DNS queries?**
```shell
cat dns.log |zeek-cut query |sort |uniq

2
```
**Investigate the conn.log file. What is the longest connection duration?**
```shell
cat conn.log |zeek-cut duration |sort -nr |uniq

332.319364
```

## Task 5

**Investigate the http.pcap file. Create the  HTTP signature shown in the task and investigate the pcap. What is the source IP of the first event?**
```shell
cd /home/ubuntu/Desktop/Exercise-Files/TASK-5/http

nano http-password.sig

signature http-password {
  ip-proto == tcp
  dst-port == 80
  payload /.*password.*/
  event "Cleartext Password Found!"

zeek -C -r http.pcap -s http-password.sig

cat notice.log |zeek-cut id.orig_h |sort

10.10.57.178
```
**What is the source port of the second event?**
```shell
cat notice.log | zeek-cut id.orig_p

38718
```
**Investigate the conn.log.
What is the total number of the sent and received packets from source port 38706?**
```shell
cat conn.log | zeek-cut id.orig_p orig_pkts resp_pkts

20
```
**Create the global rule shown in the task and investigate the ftp.pcap file.
Investigate the notice.log. What is the number of unique events?**
```shell
cd /home/ubuntu/Desktop/Exercise-Files/TASK-5/ftp

nano ftp-bruteforce.sig

signature ftp-username {
    ip-proto == tcp
    ftp /.*USER.*/
    event "FTP Username Input Found!"
}

signature ftp-brute {
    ip-proto == tcp
    payload /.*530.*Login.*incorrect.*/
    event "FTP Brute-force Attempt!"
}

zeek -C -r ftp.pcap -s ftp-bruteforce.sig

cat notice.log |zeek-cut uid |sort | uniq |wc -l

1413
```
**What is the number of ftp-brute signature matches?**
```shell
cat signatures.log | grep brute |wc -l

1410
```

## Task 6

**Investigate the smallFlows.pcap file. Investigate the dhcp.log file. What is the domain value of the "vinlap01" host?**
```shell
cd /home/ubuntu/Desktop/Exercise-Files/TASK-6/smallflow

zeek -C -r smallFlows.pcap

cat dhcp.log |zeek-cut host_name domain

astaro_vineyard
```
**Investigate the bigFlows.pcap file. Investigate the dhcp.log file. What is the number of identified unique hostnames?**
```shell
cd /home/ubuntu/Desktop/Exercise-Files/TASK-6/bigflow

zeek -C -r bigFlows.pcap

cat dhcp.log |zeek-cut host_name |sort |uniq 

17
```
**Investigate the dhcp.log file. What is the identified domain value?**
```shell
cat dhcp.log |zeek-cut domain |sort |uniq

jaalam.net
```

## Task 7

****
```shell
cd /home/ubuntu/Desktop/Exercise-Files/TASK-7/101

zeek -C -r sample.pcap 103.zeek |grep Connection | wc

87
```
****
```shell
cd /home/ubuntu/Desktop/Exercise-Files/TASK-7/201

zeek -C -r ftp.pcap -s ftp-admin.sig 201.zeek |wc -l

1401
```
****
```shell
cat signatures.log |grep administrator |wc -l

731
```
****
```shell
head loaded_scripts.log

tail loaded_scripts.log

cat loaded_scripts.log | wc -l

498
```
****
```shell
cd /home/ubuntu/Desktop/Exercise-Files/TASK-7/202

zeek -C -r ftp-brute.pcap /opt/zeek/share/zeek/policy/protocols/ftp/detect-bruteforcing.zeek 

cat notice.log | grep Brute |wc -l

2
```

## Task 8

**Investigate the case1.pcap file with intelligence-demo.zeek script. Investigate the intel.log file. Look at the second finding, where was the intel info found?**
```shell
cd /home/ubuntu/Desktop/Exercise-Files/TASK-8

zeek -C -r case1.pcap intelligence-demo.zeek 

cat intel.log -n 2

IN_HOST_HEADER
```
**Investigate the http.log file. What is the name of the downloaded .exe file?**
```shell
cat http.log | grep .exe

knr.exe
```
**Investigate the case1.pcap file with hash-demo.zeek script. Investigate the files.log file. What is the MD5 hash of the downloaded .exe file?**
```shell
zeek -C -r case1.pcap hash-demo.zeek

cat files.log | grep .exe

cc28e40b46237ab6d5282199ef78c464
```
**Investigate the case1.pcap file with file-extract-demo.zeek script. Investigate the "extract_files" folder. Review the contents of the text file. What is written in the file?**
```shell
zeek -C -r case1.pcap file-extract-demo.zeek 

cd extract_files/

less extract-1561667874.743959-HTTP-Fpgan59p6uvNzLFja

Microsoft NCSI
```

## Task 9

**Investigate the http.pcap file with the zeek-sniffpass module. Investigate the notice.log file. Which username has more module hits?**
```shell
cd /home/ubuntu/Desktop/Exercise-Files/TASK-9/cleartext-pass

zeek -Cr http.pcap /opt/zeek/share/zeek/site/zeek-sniffpass

cat notice.log |zeek-cut msg

BroZeek
```
**Investigate the case2.pcap file with geoip-conn module. Investigate the conn.log file. What is the name of the identified City?**
```shell
cd /home/ubuntu/Desktop/Exercise-Files/TASK-9/geoip-conn

zeek -Cr case2.pcap geoip-conn

cat conn.log |zeek-cut geo.resp.city

Chicago
```
**Which IP address is associated with the identified City?**
```shell
cat conn.log |zeek-cut id.resp_h

23.77.86.54
```
**Investigate the case2.pcap file with sumstats-counttable.zeek script. How many types of status codes are there in the given traffic capture?**
```shell
zeek -Cr case2.pcap sumstats-counttable.zeek 

4
```
