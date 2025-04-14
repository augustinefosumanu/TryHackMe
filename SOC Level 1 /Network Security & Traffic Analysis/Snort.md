# [Snort](https://tryhackme.com/room/snort)

## Walkthrough

## Task 2

**Navigate to the Task-Exercises folder and run the command "./.easy.sh" and write the output**
```shell
Too Easy!
```

## Task 3

**Which IDS or IPS type can help you stop the threats on a local machine?**
```shell
HIPS
```
**Which IDS or IPS type can help you detect threats on a local network?**
```shell
NIDS
```
**Which IDS or IPS type can help you detect the threats on a local machine?**
```shell
HIDS
```
**Which IDS or IPS type can help you stop the threats on a local network?**
```shell
NIPS
```
**Which described solution works by detecting anomalies in the network?**
```shell
NBA
```
**According to the official description of the snort, what kind of NIPS is it?**
```shell
full-blown
```
**NBA training period is also known as ...**
```shell
baselining
```

## Task 4

**Run the Snort instance and check the build number.**
```shell
sudo snort -V

149
```
**Test the current instance with "/etc/snort/snort.conf" file and check how many rules are loaded with the current build.**
```shell
sudo snort -c /etc/snort/snort.conf -T

4151
```
**Test the current instance with "/etc/snort/snortv2.conf" file and check how many rules are loaded with the current build.**
```shell
sudo snort -c /etc/snort/snortv2.conf -T

1
```

## Task 6

**Investigate the traffic with the default configuration file with ASCII mode.
sudo snort -dev -K ASCII -l .
Execute the traffic generator script and choose "TASK-6 Exercise". Wait until the traffic ends, then stop the Snort instance. Now analyse the output summary and answer the question.
sudo ./traffic-generator.sh
Now, you should have the logs in the current directory. Navigate to folder "145.254.160.237". What is the source port used to connect port 53?**
```shell
cd Desktop/Task-Exercises/Exercise-Files/TASK-6

sudo ls 145.254.160.237/

3009
```
**Use snort.log.1640048004 
Read the snort.log file with Snort; what is the IP ID of the 10th packet?
snort -r snort.log.1640048004 -n 10**
```shell
sudo snort -r snort.log.1640048004 -n 10

49313
```
**Read the "snort.log.1640048004" file with Snort; what is the referer of the 4th packet?**
```shell
sudo snort -Xr snort.log.1640048004 -n 10

http://www.ethereal.com/development.html
```
**Read the "snort.log.1640048004" file with Snort; what is the Ack number of the 8th packet?**
```shell
sudo snort -r snort.log.1640048004 -n 8

0x38AFFFF3
```
**Read the "snort.log.1640048004" file with Snort; what is the number of the "TCP port 80" packets?**
```shell
sudo snort -r snort.log.1640048004 'tcp and port 80'

41
```

## Task 7

**Investigate the traffic with the default configuration file.
sudo snort -c /etc/snort/snort.conf -A full -l .
Execute the traffic generator script and choose "TASK-7 Exercise". Wait until the traffic stops, then stop the Snort instance. Now analyse the output summary and answer the question.
sudo ./traffic-generator.sh
What is the number of the detected HTTP GET methods?**
```shell
2
```

## Task 8

**Investigate the mx-1.pcap file with the default configuration file.
sudo snort -c /etc/snort/snort.conf -A full -l . -r mx-1.pcap
What is the number of the generated alerts?**
```shell
170
```
**Keep reading the output. How many TCP Segments are Queued?**
```shell
18
```
**Keep reading the output.How many "HTTP response headers" were extracted?**
```shell
3
```
**Investigate the mx-1.pcap file with the second configuration file.
sudo snort -c /etc/snort/snortv2.conf -A full -l . -r mx-1.pcap
What is the number of the generated alerts?**
```shell
68
```
**Investigate the mx-2.pcap file with the default configuration file.
sudo snort -c /etc/snort/snort.conf -A full -l . -r mx-2.pcap
What is the number of the generated alerts?**
```shell
340
```
**Keep reading the output. What is the number of the detected TCP packets?**
```shell
82
```
**Investigate the mx-2.pcap and mx-3.pcap files with the default configuration file.
sudo snort -c /etc/snort/snort.conf -A full -l . --pcap-list="mx-2.pcap mx-3.pcap"
What is the number of the generated alerts?**
```shell
1020
```

## Task 9

![image](https://github.com/user-attachments/assets/55e0c159-b22d-448d-9cfc-77d0fb155bd5)
![image](https://github.com/user-attachments/assets/ba744f78-38ff-416f-b7ac-d24f5ee81959)
![image](https://github.com/user-attachments/assets/4b76233d-3fba-4de0-b135-a87574e8e090)
![image](https://github.com/user-attachments/assets/26b9fbdd-11b8-4a98-93b8-30595775c5d3)
![image](https://github.com/user-attachments/assets/c9366723-825e-4164-82e7-c3ea6e10c2ac)
![image](https://github.com/user-attachments/assets/dc460e8b-316c-46c2-9e09-21408f5fdfdb)
</br>

**Use "task9.pcap". Write a rule to filter IP ID "35369" and run it against the given pcap file. What is the request name of the detected packet? You may use this command: "snort -c local.rules -A full -l . -r task9.pcap"**
```shell
alert icmp any any <> any any (msg: "ID Found"; id:35369; sid:1000002; rev:1;)

TIMESTAMP REQUEST
```
**Clear the previous alert file and comment out the old rules. Create a rule to filter packets with Syn flag and run it against the given pcap file. What is the number of detected packets?**
```shell
alert tcp any any <> any any (msg: "SYN Flag"; flags:S; sid: 1000003; rev:1;)

1
```
**Clear the previous alert file and comment out the old rules. Write a rule to filter packets with Push-Ack flags and run it against the given pcap file. What is the number of detected packets?**
```shell
alert tcp any any <> any any (msg: "Push-Ack"; flags: P,A; sid: 1000004; rev:1;)

216
```
**Clear the previous alert file and comment out the old rules. Create a rule to filter UDP packets with the same source and destination IP and run it against the given pcap file. What is the number of packets that show the same source and destination address?**
```shell
alert udp any any <> any any (msg: "Same IP Address"; sameip;  sid: 1000005; rev:1;)

7
```
**Case Example - An analyst modified an existing rule successfully. Which rule option must the analyst change after the implementation?**
```shell
rev
```
