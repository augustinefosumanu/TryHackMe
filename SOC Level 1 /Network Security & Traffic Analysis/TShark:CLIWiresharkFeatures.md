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

****
```shell

```
****
```shell

```

## Task 6

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
