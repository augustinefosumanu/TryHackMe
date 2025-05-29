# [TShark: CLI Wireshark Features](https://tryhackme.com/room/tsharkcliwiresharkfeatures)

## Walkthrough


## Task 2
![image](https://github.com/user-attachments/assets/9c2dad97-df90-4009-a6bd-a215e6be7def)
</br>
**Use the "write-demo.pcap" to answer the questions.
What is the byte value of the TCP protocol?**
![image](https://github.com/user-attachments/assets/469a427b-a16e-4681-84bb-b9fe6aa8f934)
</br>
```shell
tshark -r write-demo.pcap -z io,phs,tcp -q

62
```
**In which packet lengths row is our packet listed?**
![image](https://github.com/user-attachments/assets/72258a4e-223c-4de8-94f3-32076d521f8d)
</br>
```shell
tshark -r write-demo.pcap -z plen,tree -q

40-79
```
**What is the summary of the expert info?**
![image](https://github.com/user-attachments/assets/e3f51661-39c6-4662-9801-a23d931b10b2)
</br>
```shell
tshark -r write-demo.pcap -z expert -q

Connection establish request (SYN): server port 80
```
**Use the "demo.pcapng" to answer the question.
List the communications. What is the IP address that exists in all IPv4 conversations?
Enter your answer in defanged format.**
![image](https://github.com/user-attachments/assets/a3c41a0a-0773-4d18-8023-eb7cfcb97093)
</br>
```shell
145[.]254[.]160[.]237
```

## Task 3

**Use the "demo.pcapng" to answer the questions.
Which IP address has 7 appearances?
Enter your answer in defanged format.**
![image](https://github.com/user-attachments/assets/2657ed37-e539-4e03-9c4d-3158afb7b702)
</br>
```shell
tshark -r demo.pcapng -z ip_hosts,tree -q

216[.]239[.]59[.]99
```
**What is the "destination address percentage" of the previous IP address?**
![image](https://github.com/user-attachments/assets/96dac46e-8a79-47ef-85c9-ef34491f1a0c)
</br>
```shell
tshark -r demo.pcapng -z dests,tree -q

6.98
```
**Which IP address constitutes "2.33% of the destination addresses"?
Enter your answer in defanged format.**
```shell
145[.]253[.]2[.]203
```
**What is the average "Qname Len" value?**
![image](https://github.com/user-attachments/assets/b71bdfb0-5fa6-4e5e-8b9f-0e9f214c9258)
</br>
```shell
tshark -r demo.pcapng -z dns,tree -q

29.00
```

## Task 4
![image](https://github.com/user-attachments/assets/71104540-87b6-4d05-a75b-43ff1300afae)
![image](https://github.com/user-attachments/assets/45b2e506-dec5-42da-b5d0-f46086f7bb90)
</br>
**Use the "demo.pcapng" to answer the questions.
Follow the "UDP stream 0".
What is the "Node 0" value?
Enter your answer in defanged format.**
![image](https://github.com/user-attachments/assets/38c99c1d-412c-4971-89af-27df1303c553)
</br>
```shell
tshark -r demo.pcapng -z follow,udp,ascii,0 -q

145[.]254[.]160[.]237:3009
```
**Follow the "HTTP stream 1".
What is the "Referer" value?
Enter your answer in defanged format.**
![image](https://github.com/user-attachments/assets/f0d4c435-8df9-4d4d-9c91-1f3d43242193)
</br>
```shell
tshark -r demo.pcapng -z follow,http,ascii,1 -q

hxxp[://]www[.]ethereal[.]com/download[.]html
```
**Use the "credentials.pcap" to answer the question.
What is the total number of detected credentials?**
![image](https://github.com/user-attachments/assets/9b57cfcc-12df-49f8-b654-0c254cd341bf)
</br>
```shell
tshark -r credentials.pcap -z credentials -q | nl

75
```

## Task 5
![image](https://github.com/user-attachments/assets/468eb941-2a29-40ab-8f77-e5a3790770ac)
</br>
**Use the "demo.pcapng" to answer questions.
What is the HTTP packet number that contains the keyword "CAFE"?**
![image](https://github.com/user-attachments/assets/1c8ad59a-78c1-46a5-aa5b-78d3f86d1cce)
</br>
```shell
tshark -r demo.pcapng -Y 'http contains "CAFE"'

27
```
**Filter the packets with "GET" and "POST" requests and extract the packet frame time.
What is the first time value found?**
![image](https://github.com/user-attachments/assets/56e58ab4-19b3-4f99-aef0-f98160513d14)
</br>
```shell
tshark -r demo.pcapng -Y 'http.request.method matches "(GET|POST)"' -T fields -e http.request.method -e frame.time -E header=y

May 13, 2004 10:17:08.222534000 UTC
```

## Task 6

**Use the "hostnames.pcapng" to answer the questions.
What is the total number of unique hostnames?**
![image](https://github.com/user-attachments/assets/90334ea3-7735-497a-8f6b-ef125005efcf)
</br>
```shell
tshark -r hostnames.pcapng -T fields -e dhcp.option.hostname | awk NF | sort -r | uniq -c | sort -r | nl

30
```
**What is the total appearance count of the "prus-pc" hostname?**
```shell
12
```
**Use the "dns-queries.pcap" to answer the question.
What is the total number of queries of the most common DNS query?**
![image](https://github.com/user-attachments/assets/dad1bd84-a4f6-4ff5-984e-bd02fa7a2e20)
</br>
```shell
tshark -r dns-queries.pcap -T fields -e dns.qry.name | awk NF | sort -r | uniq -c | sort -r |nl

472
```
**Use the "user-agents.pcap" to answer questions.
What is the total number of the detected "Wfuzz user agents"?**
![image](https://github.com/user-attachments/assets/a2176a10-bc66-45ab-a571-06800f838e0b)
</br>
```shell
tshark -r user-agents.pcap -T fields -e http.user_agent |awk NF |sort -r | uniq -c | sort -r

12
```
**What is the "HTTP hostname" of the nmap scans?
Enter your answer in defanged format.**
![image](https://github.com/user-attachments/assets/087b314f-28bf-4b6e-82e5-a26e4864d4a1)
</br>
```shell
tshark -r user-agents.pcap -T fields -e http.host | awk NF | sort -r | uniq -c | sort -r

172[.]16[.]172[.]129
```
