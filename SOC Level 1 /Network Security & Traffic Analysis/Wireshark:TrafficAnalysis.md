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


### Task 

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


### Task 

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


### Task 

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


### Task 

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


### Task 

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


### Task 
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


### Task 
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

