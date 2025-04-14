# [Snort Challenge - Live Attacks](https://tryhackme.com/room/snortchallenges2)

## Walkthrough

## Task 2

**First of all, start Snort in sniffer mode and try to figure out the attack source, service and port.
Then, write an IPS rule and run Snort in IPS mode to stop the brute-force attack. Once you stop the attack properly, you will have the flag on the desktop!
Here are a few points to remember:
Create the rule and test it with "-A console" mode. 
Use "-A full" mode and the default log path to stop the attack.
Write the correct rule and run the Snort in IPS "-A full" mode.
Block the traffic at least for a minute and then the flag file will appear on your desktop.
Stop the attack and get the flag (which will appear on your Desktop)**
```shell
sudo snort -X -l .

sudo snort -Xr snort.log.1744594433

sudo nano /etc/snort/rules/local.rules

drop tcp any 22 <> any any (msg: "SSH Denied"; sid: 1000001; rev: 1;)

drop tcp any any <> any 22 (msg: "SSH Denied"; sid: 1000002; rev: 1;)

sudo snort -c /etc/snort/snort.conf -q -Q --daq afpacket -i eth0:eth1 -A full

THM{81b7fef657f8aaa6e4e200d616738254}
```
**What is the name of the service under attack?**
```shell
SSH
```
**What is the used protocol/port in the attack?**
```shell
TCP/22
```

## Task 3

**First of all, start Snort in sniffer mode and try to figure out the attack source, service and port.
Then, write an IPS rule and run Snort in IPS mode to stop the brute-force attack. Once you stop the attack properly, you will have the flag on the desktop!
Here are a few points to remember:
Create the rule and test it with "-A console" mode. 
Use "-A full" mode and the default log path to stop the attack.
Write the correct rule and run the Snort in IPS "-A full" mode.
Block the traffic at least for a minute and then the flag file will appear on your desktop.
Stop the attack and get the flag (which will appear on your Desktop)**
```shell
sudo snort -X -l .

sudo snort -Xr snort.log.1744596204

sudo nano /etc/snort/rules/local.rules

drop tcp any 4444 <> any any (msg: "SSH Denied"; sid: 1000001; rev: 1;)

drop tcp any any <> any 4444 (msg: "SSH Denied"; sid: 1000002; rev: 1;)

THM{0ead8c494861079b1b74ec2380d2cd24}
```
**What is the used protocol/port in the attack?**
```shell
TCP/4444
```
**Which tool is highly associated with this specific port number?

**
```shell
Metasploit
```
