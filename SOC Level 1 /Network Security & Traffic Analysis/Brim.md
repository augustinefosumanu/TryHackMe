# [Brim](https://tryhackme.com/room/brim)

## Walkthrough

### Task 3

![image](https://github.com/user-attachments/assets/d6b404cb-e476-40c2-8500-7de840f16046)
</br>
**Process the "sample.pcap" file and look at the details of the first DNS log that appear on the dashboard. What is the "qclass_name"?**
```shell
C_INTERNET
```

![image](https://github.com/user-attachments/assets/cd7ab57d-d47f-44f8-b6cc-af2db0f023ab)
</br>
**Look at the details of the first NTP log that appear on the dashboard. What is the "duration" value?**
```shell
0.005
```

![image](https://github.com/user-attachments/assets/eebe3102-fc90-4409-b2b5-1b3190358938)
</br>
**Look at the details of the STATS packet log that is visible on the dashboard. What is the "reassem_tcp_size"?**
```shell
540
```

### Task 4

![image](https://github.com/user-attachments/assets/f0046a94-23dc-45bf-a9ce-343d57813284)
</br>
**Investigate the files. What is the name of the detected GIF file?**
```shell
cat01_with_hidden_text.gif
```

![image](https://github.com/user-attachments/assets/657ad07c-5347-449e-a600-064500f0d753)
</br>
**Investigate the conn logfile. What is the number of the identified city names?**
```shell
_path=="conn" | cut geo.resp.city

2
```

![image](https://github.com/user-attachments/assets/d0738c0f-fb14-4944-aef3-674a51b3bddc)
</br>
**Investigate the Suricata alerts. What is the Signature id of the alert category "Potential Corporate Privacy Violation"?**
```shell
2,012,887
```

![image](https://github.com/user-attachments/assets/b97358e7-b3cf-486a-ae6b-f64038cebdb8)
![image](https://github.com/user-attachments/assets/d4754126-41fc-420b-b338-5f5603050280)
![image](https://github.com/user-attachments/assets/7e648c23-e5f9-4170-868b-58f533edac37)
![image](https://github.com/user-attachments/assets/28309862-aaef-400f-8ce0-b056a4eb463a)
</br>

### Task 6

![image](https://github.com/user-attachments/assets/016ef339-8cc5-4436-b293-2d815f4b5512)
</br>
****
```shell
4564.exe
```

![image](https://github.com/user-attachments/assets/b3a14e35-952b-4d53-a18d-29b60edfbe7b)
</br>
**What is the number of CobaltStrike connections using port 443?**
```shell
328
```

![image](https://github.com/user-attachments/assets/03cfa5c3-9f67-427b-a16b-340d5291bb21)
</br>
**There is an additional C2 channel in used the given case. What is the name of the secondary C2 channel?**
```shell
IcedID
```

### Task 7

![image](https://github.com/user-attachments/assets/7f2770a7-99a2-4c88-893e-96d0bf4d0b5b)
</br>
****
```shell
_path=="conn" id.resp_p==19999 | put total_bytes := orig_bytes + resp_bytes | sort -r total_bytes | cut uid, id, orig_bytes, resp_bytes, total_bytes|count()

22
```

![image](https://github.com/user-attachments/assets/c0356677-acce-4d10-a46a-cdc7099d1bcd)
</br>
**What is the name of the service used by port 6666?**
```shell
irc
```

![image](https://github.com/user-attachments/assets/e2e9ff00-d7a2-4cd7-9153-e21702778a52)
</br>
**What is the amount of transferred total bytes to "101.201.172.235:8888"?**
```shell
3,729
```

![image](https://github.com/user-attachments/assets/0c5c3882-991f-473f-90d1-6cbdb7fa4573)
</br>
****
```shell
TA0040
```
