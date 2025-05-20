# [Wireshark: Traffic Analysis](https://tryhackme.com/room/wiresharktrafficanalysis)

## Walkthrough


### Task 2
![image](https://github.com/user-attachments/assets/6a6703c2-6d21-42c2-a3e9-30b152ef325e)
</br>
**Use the "Desktop/exercise-pcaps/nmap/Exercise.pcapng" file.
What is the total number of the "TCP Connect" scans?**
![image](https://github.com/user-attachments/assets/af24ac84-c48b-40f7-9296-cfa03c19cf08)
</br>
```shell
tcp.flags.syn==1 and tcp.flags.ack==0 and tcp.window_size>1024

1000
```
**Which scan type is used to scan the TCP port 80?**
![image](https://github.com/user-attachments/assets/0bbc4a5d-c667-4cbc-9a03-64bf20e0644b)
</br>
```shell
tcp.port==80

TCP Connect
```
**How many "UDP close port" messages are there?**
![image](https://github.com/user-attachments/assets/28353feb-bfa6-4e11-b2a1-3050c4dbaa09)
</br>
```shell
icmp.type==3 and icmp.code==3

1083
```
**Which UDP port in the 55-70 port range is open?**
![image](https://github.com/user-attachments/assets/acf3bed9-70a9-4c88-958d-17daed759517)
</br>
```shell
udp.port>=55 and udp.port<=70

68
```

### Task 3
![image](https://github.com/user-attachments/assets/a0d17be1-0b54-4432-96f3-a22f36baa792)
</br>
**Use the "Desktop/exercise-pcaps/arp/Exercise.pcapng" file.
What is the number of ARP requests crafted by the attacker?**
![image](https://github.com/user-attachments/assets/b1ee56d4-b539-4efa-9e57-fdc333915fe8)
</br>
```shell
eth.src == 00:0c:29:e2:18:b4 and arp.opcode==1

284
```
**What is the number of HTTP packets received by the attacker?**
![image](https://github.com/user-attachments/assets/1765279a-66b6-4e2b-8943-d2602f299388)
</br>
```shell
eth.dst == 00:0c:29:e2:18:b4 and http

90
```
**What is the number of sniffed username&password entries?**
![image](https://github.com/user-attachments/assets/2fc3d492-a89b-4b8a-a574-2e82741461db)
![image](https://github.com/user-attachments/assets/656307ef-c1fa-4092-b862-ff3cbf8492a4)
![image](https://github.com/user-attachments/assets/d2aa6403-2b43-4e35-be31-8bb0bb89eae8)
</br>
```shell
tcp.stream eq 4

http.host == testphp.vulnweb.com and http.request.method ==POST

6
```
**What is the password of the "Client986"?**
![image](https://github.com/user-attachments/assets/d75f98e2-b6b9-40c6-a277-21b2cfab0334)

```shell
http.host == testphp.vulnweb.com and http.request.method ==POST

clientnothere!
```
**What is the comment provided by the "Client354"?**
![image](https://github.com/user-attachments/assets/a5ae15ff-7d60-407c-8e24-4d6d26a3e43f)
</br>
```shell
Nice work!
```

### Task 4
![image](https://github.com/user-attachments/assets/5e9b5a62-0c8a-431b-830c-a546ccc581e9)
</br>
**Use the "Desktop/exercise-pcaps/dhcp-netbios-kerberos/dhcp-netbios.pcap" file.
What is the MAC address of the host "Galaxy A30"?**
![image](https://github.com/user-attachments/assets/c5a63192-02a6-4837-af86-3b5ee07312e9)
</br>
```shell
dhcp.option.hostname matches "Galaxy"

9a:81:41:cb:96:6c
```
![image](https://github.com/user-attachments/assets/00434dd6-3ef0-4dd1-83cf-875f23068025)
</br>
**How many NetBIOS registration requests does the "LIVALJM" workstation have?**
```shell
nbns.name contains "LIVALJM"

16
```
**Which host requested the IP address "172.16.13.85"?**
![image](https://github.com/user-attachments/assets/34bc8bce-6fd2-4dd0-9240-938723441202)
</br>
```shell
dhcp.option.requested_ip_address == 172.16.13.85

Galaxy-A12
```
![image](https://github.com/user-attachments/assets/bc315bfd-6810-4d11-a6e5-8d6db3b09ac5)
</br>
**Use the "Desktop/exercise-pcaps/dhcp-netbios-kerberos/kerberos.pcap" file.
What is the IP address of the user "u5"? (Enter the address in defanged format.)**
![image](https://github.com/user-attachments/assets/2c0f7bf7-9fef-4f21-ba43-66555612b3b3)
</br>
```shell
kerberos.CNameString contains u5

10[.]1[.]12[.]2
```
**What is the hostname of the available host in the Kerberos packets?**
![image](https://github.com/user-attachments/assets/2709427d-fbf6-4c43-8319-3b0ba6897b40)
</br>
```shell
kerberos.CNameString contains "$"

xp1$
```

### Task 5
![image](https://github.com/user-attachments/assets/a1a71f1f-8fd7-4230-b6d6-bf94b44f7816)
</br>
![image](https://github.com/user-attachments/assets/43f5f587-bbb4-480c-8628-1a6a330754f7)
</br>
**Use the "Desktop/exercise-pcaps/dns-icmp/icmp-tunnel.pcap" file.
Investigate the anomalous packets. Which protocol is used in ICMP tunnelling?**
![image](https://github.com/user-attachments/assets/c4c7f509-8d3c-4010-a010-e21bf95742e0)
</br>
```shell
data.len > 64 and icmp

SSH
```
**Use the "Desktop/exercise-pcaps/dns-icmp/dns.pcap" file.
Investigate the anomalous packets. What is the suspicious main domain address that receives anomalous DNS queries? (Enter the address in defanged format.)**
![image](https://github.com/user-attachments/assets/e79c24ab-503c-4021-99d5-c598235a62b2)
</br>
```shell
dns.qry.name.len > 15 and !mdns 

dataexfil[.]com
```

### Task 6
![image](https://github.com/user-attachments/assets/21405db9-4524-455a-a9ec-f9eace43a929)
![image](https://github.com/user-attachments/assets/bba0ceb0-1b62-4f6f-811b-ca6710914b80)
</br>
**Use the "Desktop/exercise-pcaps/ftp/ftp.pcap" file.
How many incorrect login attempts are there?**
![image](https://github.com/user-attachments/assets/bf17f04c-6be2-41e6-88f7-7714b8106217)
</br>
```shell
ftp.response.code == 530

737
```
**What is the size of the file accessed by the "ftp" account?**
![image](https://github.com/user-attachments/assets/fca4a30f-91ea-4483-9731-768668433309)
</br>
```shell
ftp.response.code == 213

39424
```
**The adversary uploaded a document to the FTP server. What is the filename?**
![image](https://github.com/user-attachments/assets/73a07224-0a6b-4b8e-9f33-217430112b35)
![image](https://github.com/user-attachments/assets/ee19d63d-bb91-49b3-9563-9d2eaf4d1af4)
</br>
```shell
tcp.stream eq 714

resume.doc
```
**The adversary tried to assign special flags to change the executing permissions of the uploaded file. What is the command used by the adversary?**
![image](https://github.com/user-attachments/assets/557678b4-4eca-4d54-8c15-2fbac5855b41)
</br>
```shell
CHMOD 777
```

### Task 7
![image](https://github.com/user-attachments/assets/b0309c40-b8aa-4506-a36c-b4a78ab07b24)
![image](https://github.com/user-attachments/assets/1a24b9dc-69fc-4257-8340-9a13380585c0)
![image](https://github.com/user-attachments/assets/680f687c-93b0-4d6b-8d86-066092f9d0e2)
![image](https://github.com/user-attachments/assets/4f60fd2c-29fd-4eec-8cd4-b5b30bb9e1fc)
</br>
**Use the "Desktop/exercise-pcaps/http/user-agent.cap" file.
Investigate the user agents. What is the number of anomalous  "user-agent" types?**
![image](https://github.com/user-attachments/assets/b3f906a8-ad61-4b58-aae6-2261b7a0d182)
</br>
```shell
http.user_agent

6
```
**What is the packet number with a subtle spelling difference in the user agent field?**
![image](https://github.com/user-attachments/assets/14865c6c-1df4-4e42-b424-2a5a6bc4a1a4)
</br>
```shell
52
```
**Use the "Desktop/exercise-pcaps/http/http.pcapng" file.
Locate the "Log4j" attack starting phase. What is the packet number?**
![image](https://github.com/user-attachments/assets/7f42cbe1-191d-40aa-8988-5d1a1c94287a)
</br>
```shell
http.request.method == POST or frame contains "jindi"

444
```
**Locate the "Log4j" attack starting phase and decode the base64 command. What is the IP address contacted by the adversary? (Enter the address in defanged format and exclude "{}".)**
![image](https://github.com/user-attachments/assets/1c436954-52a3-49f8-b561-4d4cd9595c66)
</br>
```shell
62[.]210[.]130[.]250
```

### Task 8
![image](https://github.com/user-attachments/assets/21fe1350-9d2d-4ea3-b3ef-0b201783d465)
</br>
**Use the "Desktop/exercise-pcaps/https/Exercise.pcap" file.
What is the frame number of the "Client Hello" message sent to "accounts.google.com"?**
![image](https://github.com/user-attachments/assets/80a95626-aa45-46b2-a03c-6a3276bc5642)
</br>
```shell
(http.request or tls.handshake.type == 1) and !(ssdp)

16
```
**Decrypt the traffic with the "KeysLogFile.txt" file. What is the number of HTTP2 packets?**
![image](https://github.com/user-attachments/assets/d4597bb6-5bbc-461d-b071-db6a069e3828)
</br>
```shell
http2

115
```
**Go to Frame 322. What is the authority header of the HTTP2 packet? (Enter the address in defanged format.)**
![image](https://github.com/user-attachments/assets/1576bc35-ccc4-4e27-becd-6c040e3c93ab)
</br>
```shell
safebrowsing[.]googleapis[.]com
```
**Investigate the decrypted packets and find the flag! What is the flag?**
![image](https://github.com/user-attachments/assets/c1a978c0-e227-4816-a6af-ad3f7937115a)
![image](https://github.com/user-attachments/assets/db42a6b6-f9c2-4152-b921-ad292600d50e)
</br>
```shell
FLAG{THM-PACKETMASTER}
```

### Task 9

**Use the "Desktop/exercise-pcaps/bonus/Bonus-exercise.pcap" file.
What is the packet number of the credentials using "HTTP Basic Auth"?**
![image](https://github.com/user-attachments/assets/65c7c80d-e212-4cdf-862d-f432c2aad7aa)
</br>
```shell
237
```
**What is the packet number where "empty password" was submitted?**
![image](https://github.com/user-attachments/assets/b7814f43-6963-4a79-ac42-36ea43a07b21)
</br>
```shell
170
```

### Task 10

**Use the "Desktop/exercise-pcaps/bonus/Bonus-exercise.pcap" file.
Select packet number 99. Create a rule for "IPFirewall (ipfw)". What is the rule for "denying source IPv4 address"?**
![image](https://github.com/user-attachments/assets/2e198eac-d156-47a1-837a-4014a290cf03)
</br>
```shell
add deny ip from 10.121.70.151 to any in
```
**Select packet number 231. Create "IPFirewall" rules. What is the rule for "allowing destination MAC address"?**
![image](https://github.com/user-attachments/assets/30c38a8d-9521-495a-aaa4-46b9cdf1b6fa)
</br>
```shell
add allow MAC 00:d0:59:aa:af:80 any in
```
