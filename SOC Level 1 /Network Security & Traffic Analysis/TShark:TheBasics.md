# [TShark: The Basics](https://tryhackme.com/room//tsharkthebasics)

## Walkthrough


## Task 2

**View the details of the demo.pcapng file with "capinfos".
What is the "RIPEMD160" value?**
![image](https://github.com/user-attachments/assets/d3c969e9-e7d9-4de8-8425-6e8cdf70f71a)
</br>
```shell
capinfos demo.pcapng

6ef5f0c165a1db4a3cad3116b0c5bcc0cf6b9ab7
```

## Task 3
![image](https://github.com/user-attachments/assets/315e6e31-bf56-4f4a-82e5-3e96a90ec4f6)
</br>
**What is the installed TShark version in the given VM?**
![image](https://github.com/user-attachments/assets/3b9cc91a-d892-4375-8f78-e0758b0bee39)
</br>
```shell
tshark -v

3.2.3
```
**List the available interfaces with TShark.
What is the number of available interfaces in the given VM?**
![image](https://github.com/user-attachments/assets/60359d6d-163b-4eed-88c0-011a10578c39)
</br>
```shell
tshark -D

12
```

## Task 4
![image](https://github.com/user-attachments/assets/c9cde668-1c9f-43b4-b982-4909c4bdd7da)
</br>
**Read the "demo.pcapng" file with TShark.
What are the assigned TCP flags in the 29th packet?**
![image](https://github.com/user-attachments/assets/a21cbdd8-aada-46b0-976c-9cf04c8b1b1d)
</br>
```shell
tshark -r demo.pcapng -c 29

PSH,ACK
```
**What is the "Ack" value of the 25th packet?**
![image](https://github.com/user-attachments/assets/f09bc48b-cc2f-42ff-b241-2fe27185cb93)
</br>
```shell
tshark -r demo.pcapng -c 25

12421
```
**What is the "Window size value" of the 9th packet?**
![image](https://github.com/user-attachments/assets/9c8fa480-95a1-4f10-bf60-4c1a32d5c3a4)
</br>
```shell
tshark -r demo.pcapng -c 9

9660
```

## Task 5
![image](https://github.com/user-attachments/assets/8e2ea799-0c6e-43f4-8e07-90ddaea0396d)
</br>
**Which parameter can help analysts to create a continuous capture dump?**
```shell
-b
```
**Can we combine autostop and ring buffer parameters with TShark? y/n**
```shell
y
```

## Task 6
![image](https://github.com/user-attachments/assets/d25a2fbc-a44f-450d-bbb1-a94a8d843fe4)
</br>
**Which parameter is used to set "Capture Filters"?**
```shell
-f
```
**Which parameter is used to set "Display Filters"?**
```shell
-Y
```

## Task 7
![image](https://github.com/user-attachments/assets/510c6028-455b-4723-92e4-b80d46890ead)
</br>
**What is the number of packets with SYN bytes?**
![image](https://github.com/user-attachments/assets/1011d26f-d767-4a9f-8e10-9030371ef0ea)
</br>
```shell
tshark -f "host 10.10.10.10"

curl -v 10.10.10.10

2
```
**What is the number of packets sent to the IP address "10.10.10.10"?**
```shell
7
```
**What is the number of packets with ACK bytes?**
```shell
8
```

## Task 8
![image](https://github.com/user-attachments/assets/fd03a685-7d05-462b-9cdc-34dea30939c6)
</br>
**What is the number of packets with a "65.208.228.223" IP address?**
![image](https://github.com/user-attachments/assets/75db93d0-536b-40b6-ac56-714f60cdfaca)
</br>
```shell
tshark -r demo.pcapng -Y 'ip.addr == 65.208.228.223' | nl

34
```
**What is the number of packets with a "TCP port 3371"?**
![image](https://github.com/user-attachments/assets/ab070b1b-fca1-44bd-8429-57c409459225)
</br>
```shell
tshark -r demo.pcapng -Y 'tcp.port == 3371' | nl

7
```
**What is the number of packets with a "145.254.160.237" IP address as a source address?**
![image](https://github.com/user-attachments/assets/2f0505c9-9d5d-448c-9a12-d60b03a214e5)
</br>
```shell
tshark -r demo.pcapng -Y 'ip.src == 145.254.160.237' | nl

20
```
**Rerun the previous query and look at the output.
What is the packet number of the "Duplicate" packet?**
![image](https://github.com/user-attachments/assets/3ef6d15d-2ae1-4b35-addd-578d0eb7e854)
</br>
```shell
37
```
