# [Wireshark: Packet Operations](https://tryhackme.com/room//wiresharkpacketoperations)

## Walkthrough


### Task 2

![image](https://github.com/user-attachments/assets/77c4f066-3745-4db3-82cd-c832863b8395)
</br>
**Investigate the resolved addresses. What is the IP address of the hostname starts with "bbc"?**
```shell
199.232.24.81
```

![image](https://github.com/user-attachments/assets/5d956fb5-352e-4d9c-b536-3f8c4ce86bb2)
</br>
**What is the number of IPv4 conversations?**
```shell
435
```

![image](https://github.com/user-attachments/assets/b30fe923-6111-4801-9aa5-b01aaf37be6f)
</br>
**How many bytes (k) were transferred from the "Micro-St" MAC address?**
```shell
7474
```

![image](https://github.com/user-attachments/assets/30e681d8-64de-4da5-9904-3b0180289c4b)
</br>
**What is the number of IP addresses linked with "Kansas City"?**
```shell
4
```

![image](https://github.com/user-attachments/assets/253e8e9d-f2a7-42eb-af66-bb1879205ba3)
</br>
**Which IP address is linked with "Blicnet" AS Organisation?**
```shell
188.246.82.7
```

### Task 3

![image](https://github.com/user-attachments/assets/74eee56a-0fd1-44f7-9d00-2526e9452131)
</br>
**What is the most used IPv4 destination address?**
```shell
10.100.1.33
```

![image](https://github.com/user-attachments/assets/75b865b4-e6ad-4c4c-8889-b24ef14758f5)
</br>
**What is the max service request-response time of the DNS packets?**
```shell
0.467897
```

![image](https://github.com/user-attachments/assets/d28477b0-69e1-42b9-b321-bd31003b9028)
</br>
**What is the number of HTTP Requests accomplished by "rad[.]msn[.]com?**
```shell
39
```

![image](https://github.com/user-attachments/assets/b8d35268-37e3-4c71-9f4a-c50f51b6a526)
![image](https://github.com/user-attachments/assets/fc21e437-ab2b-4131-a379-3b5a64700145)
![image](https://github.com/user-attachments/assets/1121403c-f826-42af-acd8-543a85f48884)
![image](https://github.com/user-attachments/assets/e1a44a6d-ab9c-4b99-8355-cca4d0046148)
![image](https://github.com/user-attachments/assets/953f12cd-e672-4853-9423-227d4245219c)
</br>

### Task 5

![image](https://github.com/user-attachments/assets/5d4f04af-4f76-4f8b-bda8-1e6eeae7a51e)
</br>
**What is the number of IP packets?**
```shell
ip

81420
```

![image](https://github.com/user-attachments/assets/374abb15-d327-44fb-a111-1ffba4177998)
</br>
**What is the number of packets with a "TTL value less than 10"?**
```shell
ip.ttl < 10
66
```

![image](https://github.com/user-attachments/assets/5e71af94-6c8a-413d-8614-51e249f738f3)
</br>
**What is the number of packets which uses "TCP port 4444"?**
```shell
tcp.port == 4444

632
```

![image](https://github.com/user-attachments/assets/f7a9ca2c-b210-4e05-8288-1c363329eb88)
</br>
**What is the number of "HTTP GET" requests sent to port "80"?**
```shell
hhtp.request.method == GET && tcp.port == 80

527
```

![image](https://github.com/user-attachments/assets/b572efdc-8358-4e67-9c3b-d6e7e20550aa)
</br>
**What is the number of "type A DNS Queries"?**
```shell
dns.qry.type == 1 && dns.flags.response == 1

51
```

### Task 6

![image](https://github.com/user-attachments/assets/1b21c000-3065-4371-b332-ca300d29a471)
</br>
**Find all Microsoft IIS servers. What is the number of packets that did not originate from "port 80"?**
```shell
!(tcp.port == 80) && http.server contains "Microsoft"

21
```

![image](https://github.com/user-attachments/assets/c2f49970-34b5-4b15-a453-d476d30b91d5)
</br>
**Find all Microsoft IIS servers. What is the number of packets that have "version 7.5"?**
```shell
http.server contains "Microsoft" && http.server contains "7.5"

71
```

![image](https://github.com/user-attachments/assets/4f4c5753-47fd-42c7-a7c2-6be9b279e62c)
</br>
**What is the total number of packets that use ports 3333, 4444 or 9999?**
```shell
tcp.port in {3333 4444 9999}

2235
```

![image](https://github.com/user-attachments/assets/3fe5b6b1-b44b-474f-b70b-a725eedb900d)
</br>
**What is the number of packets with "even TTL numbers"?**
```shell
string(ip.ttl) matches "[02468]$"

77289
```

![image](https://github.com/user-attachments/assets/7418ce18-b42d-4948-a2db-c07e2d451a38)
</br>
**Change the profile to "Checksum Control". What is the number of "Bad TCP Checksum" packets?**
```shell
34185
```

![image](https://github.com/user-attachments/assets/47112330-3c49-40b7-b230-c72f82a02cf6)
</br>
**Use the existing filtering button to filter the traffic. What is the number of displayed packets?**
```shell
261
```
