# [](https://tryhackme.com/room/)

## Walkthrough


## Task 2

**Investigate the contacted domains.
Investigate the domains by using VirusTotal.
According to VirusTotal, there is a domain marked as malicious/suspicious.
What is the full URL of the malicious/suspicious domain address?
Enter your answer in defanged format.**
![image](https://github.com/user-attachments/assets/f4e4e9f2-c311-4407-ac2a-b62c5029af9b)
![image](https://github.com/user-attachments/assets/983ed764-7de1-4340-9e95-b1b0ccf06c37)
![image](https://github.com/user-attachments/assets/d52bc147-f676-4669-bf13-4595c7483561)
</br>
```shell
tshark -r teamwork.pcap -T fields -e dns.qry.name | awk NF | sort -r | uniq -c | sort -r

hxxp[://]www[.]paypal[.]com4uswebappsresetaccountrecovery[.]timeseaways[.]com/
```
**When was the URL of the malicious/suspicious domain address first submitted to VirusTotal?**
![image](https://github.com/user-attachments/assets/ce502408-e236-4401-8f8b-fbeb4386f465)
</br>
```shell
2017-04-17 22:52:53 UTC
```
**Which known service was the domain trying to impersonate?**
```shell
PayPal
```
**What is the IP address of the malicious domain?
Enter your answer in defanged format.**
![image](https://github.com/user-attachments/assets/846281b8-7b72-43e0-a946-f4e2185f8944)
</br>
```shell
184[.]154[.]127[.]226
```
**What is the email address that was used?
Enter your answer in defanged format. (format: aaa[at]bbb[.]ccc)**
![image](https://github.com/user-attachments/assets/3982f031-e745-44a9-b9e8-7222ab6a9d3f)
</br>
```shell
tshark -r teamwork.pcap -Y 'http contains "gmail.com"' -V

johnny5alive[at]gmail[.]com
```
