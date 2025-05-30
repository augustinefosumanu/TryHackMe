# [TShark Challenge II: Directory](https://tryhackme.com/room/tsharkchallengestwo)

## Walkthrough


## Task 2

**Investigate the DNS queries.
Investigate the domains by using VirusTotal.
According to VirusTotal, there is a domain marked as malicious/suspicious.
What is the name of the malicious/suspicious domain?
Enter your answer in a defanged format.**
![image](https://github.com/user-attachments/assets/e83f3817-7089-4a35-b4ce-cb0be1fef06d)
</br>
```shell
tshark -r directory-curiosity.pcap -T fields -e  dns.qry.name | awk NF | sort -r | uniq

jx2-bavuong.com
```
**What is the total number of HTTP requests sent to the malicious domain?**
![image](https://github.com/user-attachments/assets/e3475807-7fa3-499b-ad2a-b29c4c3ad78c)
</br>
```shell
tshark -r directory-curiosity.pcap -Y 'http.request.full_uri contains "jx2-bavuong.com"' | nl

14
```
**What is the IP address associated with the malicious domain?
Enter your answer in a defanged format.**
![image](https://github.com/user-attachments/assets/47f43af1-a323-4fec-8ec4-97b5541f32fd)
</br>
```shell
tshark -r directory-curiosity.pcap -Y 'http.request.full_uri contains "jx2-bavuong.com"' -T fields -e ip.src -e ip.dst| sort -r | uniq

141[.]164[.]41[.]174
```
**What is the server info of the suspicious domain?**
![image](https://github.com/user-attachments/assets/0affdf3a-7246-4243-adc8-8b3c69644e3f)
</br>
```shell
tshark -r directory-curiosity.pcap -T fields -e http.server | awk NF | uniq

Apache/2.2.11 (Win32) DAV/2 mod_ssl/2.2.11 OpenSSL/0.9.8i PHP/5.2.9
```
**Follow the "first TCP stream" in "ASCII".
Investigate the output carefully.
What is the number of listed files?**
![image](https://github.com/user-attachments/assets/d5d08bc3-2b02-4c54-9292-84698e1adbc1)
</br>
```shell
tshark -r directory-curiosity.pcap -z follow,tcp,ascii,0 -q 

3
```
**What is the filename of the first file?
Enter your answer in a defanged format.**
![image](https://github.com/user-attachments/assets/d5d08bc3-2b02-4c54-9292-84698e1adbc1)
</br>
```shell
123[.]php
```
**Export all HTTP traffic objects.
What is the name of the downloaded executable file?
Enter your answer in a defanged format.**
![image](https://github.com/user-attachments/assets/23de34ac-f620-4a2f-ae33-09f7d70b9dcc)
![image](https://github.com/user-attachments/assets/d5634857-ece3-48b9-9a0a-3d424b553df7)
</br>
```shell
tshark -r directory-curiosity.pcap --export-objects http,/home/ubuntu/Desktop/extracted-files -q

cd ../extracted-files/

ls -l

vlauto[.]exe
```
**What is the SHA256 value of the malicious file?**
![image](https://github.com/user-attachments/assets/54422d11-4a70-46ac-9990-9c8062c98316)
</br>
```shell
sha256sum vlauto.exe

b4851333efaf399889456f78eac0fd532e9d8791b23a86a19402c1164aed20de
```
**Search the SHA256 value of the file on VirtusTotal.
What is the "PEiD packer" value?**
![image](https://github.com/user-attachments/assets/8bf3f304-19f0-4586-9fb6-f844ed4a36c2)
</br>
```shell
.NET executable
```
**Search the SHA256 value of the file on VirtusTotal.
What does the "Lastline Sandbox" flag this as?**
![image](https://github.com/user-attachments/assets/8a3b3daf-4578-42f2-b6c1-62c43b958ca8)
</br>
```shell
 MALWARE TROJAN
```
