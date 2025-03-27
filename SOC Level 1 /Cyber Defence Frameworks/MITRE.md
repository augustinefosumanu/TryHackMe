# [MITRE](https://tryhackme.com/room/mitre)

## Walkthrough

## Task 3

**Besides Blue teamers, who else will use the ATT&CK Matrix? (Red Teamers, Purpe Teamers, SOC Managers?)**
```shell
Red Teamers
```
**What is the ID for this technique?**
```shell
T1566
```
**Based on this technique, what mitigation covers identifying social engineering techniques?**
```shell
User Training
```
**What are the data sources for Detection? (format: source1,source2,source3 with no spaces after commas)**
```shell
Application Log,File,Network Traffic
```
**Which are the first two groups to have used spear-phishing in their campaigns? (format: group1,group2)**
```shell
Axiom,Gold SOUTHFIELD
```
**Based on the information for the first group, what are their associated groups?**
```shell
Group 72
```
**What software is associated with this group that lists phishing as a technique?**
```shell
Hikit
```
**What is the description for this software?**
```shell
Hikit is malware that has been used by Axiom for late-stage persistence and exfiltration after the initial compromise.
```
**This group overlaps (slightly) with which other group?**
```shell
Winnti Group
```
**How many techniques are attributed to this group?**
```shell
15
```

## Task 4

**What tactic has an ID of TA0003?**
```shell
Persistence
```
**What is the name of the library that is a collection of Zeek (BRO) scripts?**
```shell
BZAR
```
**What is the name of the technique for running executables with the same hash and different names?**
```shell
Masquerading
```
**Examine CAR-2013-05-004, besides Implementations, what additional information is provided to analysts to ensure coverage for this technique?**
```shell
Unit Tests
```

## Task 5

**Under Prepare, what is ID SAC0002?**
```shell
Persona Creation
```
**What is the name of the resource to aid you with the engagement activity from the previous question?**
```shell
Persona Profile Worksheet
```
**Which engagement activity baits a specific response from the adversary?**
```shell
Lures
```
**What is the definition of Threat Model?**
```shell
A risk assessment that models organizational strengths and weaknesses
```

## Task 6

**What is the first MITRE ATT&CK technique listed in the ATT&CK Lookup dropdown?**
```shell
Data Obfuscation
```
**In D3FEND Inferred Relationships, what does the ATT&CK technique from the previous question produce?**
```shell
Outbound Internet Network Traffic
```

## Task 7

**In Phase 1 for the APT3 Emulation Plan, what is listed first?**
```shell
C2 Setup
```
**Under Persistence, what binary was replaced with cmd.exe?**
```shell
sethc.exe
```
**Examining APT29, what  C2 frameworks are listed in Scenario 1 Infrastructure? (format: tool1,tool2)**
```shell
Pupy,Metasploit Framework
```
**What C2 framework is listed in Scenario 2 Infrastructure?**
```shell
PoshC2
```
**Examine the emulation plan for Sandworm. What webshell is used for Scenario 1? Check MITRE ATT&CK for the Software ID for the webshell. What is the id? (format: webshell,id)**
```shell
P.A.S.,S0598
```

## Task 8

**What is a group that targets your sector who has been in operation since at least 2013?**
```shell
APT33
```
**As your organization is migrating to the cloud, is there anything attributed to this APT group that you should focus on? If so, what is it?**
```shell
Cloud Accounts
```
**What tool is associated with the technique from the previous question?**
```shell
Ruler
```
**Referring to the technique from question 2, what mitigation method suggests using SMS messages as an alternative for its implementation?**
```shell
Multi-factor Authentication
```
**What platforms does the technique from question #2 affect?**
```shell
IaaS, Identity Provider, Office Suite, SaaS
```
