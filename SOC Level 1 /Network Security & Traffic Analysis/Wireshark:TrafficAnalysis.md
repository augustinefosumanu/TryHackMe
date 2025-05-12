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

