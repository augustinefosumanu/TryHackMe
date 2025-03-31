# [Yara](https://tryhackme.com/room/yara)

## Walkthrough


## Task 2

**What is the name of the base-16 numbering system that Yara can detect?**
```shell
hexadecimal
```
**Would the text "Enter your Name" be a string in an application? (Yay/Nay)**
```shell
Yay
```

## Task 8

```shell
cd suspicious-files/file1
python ../..tools/Loki/loki.py -p .
```
<img width="810" alt="Screenshot 2025-03-31 at 7 53 44 AM" src="https://github.com/user-attachments/assets/e1263ee9-61fe-480b-86fd-10ea0938f92e" />
</br>
</br>
<img width="814" alt="Screenshot 2025-03-31 at 7 54 39 AM" src="https://github.com/user-attachments/assets/63931fbc-68ca-4eca-8fcc-7e95987b26ba" />
</br>
</br>

**Scan file 1. Does Loki detect this file as suspicious/malicious or benign?**
```shell
Suspicious
```
**What Yara rule did it match on?**
```shell
webshell_metaslsoft
```
**What does Loki classify this file as?**
```shell
Web Shell
```
**Based on the output, what string within the Yara rule did it match on?**
```shell
Str1
```
**What is the name and version of this hack tool?**
```shell
b374k 2.2
```
**Inspect the actual Yara file that flagged file 1. Within this rule, how many strings are there to flag this file?**
```shell
1
```

**Scan file 2. Does Loki detect this file as suspicious/malicious or benign?**

```shell
cd suspicious-files/file2
python ../..tools/Loki/loki.py -p .
```
<img width="647" alt="Screenshot 2025-03-31 at 8 15 54 AM" src="https://github.com/user-attachments/assets/59fcfcc2-2836-4327-8037-c1b7e793f155" />
</br>
</br>

```shell
Benign
```

**Inspect file 2. What is the name and version of this web shell?**

```shell
nano 1ndex.php
```
<img width="648" alt="Screenshot 2025-03-31 at 8 22 00 AM" src="https://github.com/user-attachments/assets/de6bba90-4b75-4f66-b8e6-0d5101a207f5" />
</br>
</br>

```shell
b374k 3.2.3
```

## Task 9

<img width="651" alt="Screenshot 2025-03-31 at 8 58 22 AM" src="https://github.com/user-attachments/assets/325fee4a-1f1f-4b31-a2b4-c5186c51d883" />
</br>
</br>
<img width="650" alt="Screenshot 2025-03-31 at 9 00 15 AM" src="https://github.com/user-attachments/assets/1de0ff89-e6e3-416f-acb3-236b1c8438d8" />
</br>
</br>
<img width="649" alt="Screenshot 2025-03-31 at 9 04 09 AM" src="https://github.com/user-attachments/assets/b2888301-39a1-41a1-ab59-e1a321db9070" />
</br>
</br>
<img width="650" alt="Screenshot 2025-03-31 at 9 04 59 AM" src="https://github.com/user-attachments/assets/9116a601-03bc-4cf2-b551-72bac93757db" />
</br>
</br>

**From within the root of the suspicious files directory, what command would you run to test Yara and your Yara rule against file 2?**
```shell
yara file2.yar file2/1ndex.php
```
**Did Yara rule flag file 2? (Yay/Nay)**
```shell
Yay
```
**Copy the Yara rule you created into the Loki signatures directory.**
```shell
cp file2.yar ../tools/Loki/signature-base/yara/
```
**Test the Yara rule with Loki, does it flag file 2? (Yay/Nay)**
```shell
Yay
```
**What is the name of the variable for the string that it matched on?**
```shell
Zepto
```
**Inspect the Yara rule, how many strings were generated?**
```shell
20
```
**One of the conditions to match on the Yara rule specifies file size. The file has to be less than what amount?**
```shell
700KB
```

## Task 10

```shell
cd suspicious-files/file1/
sha256sum ind3x.php

5479f8cd1375364770df36e5a18262480a8f9d311e8eedb2c2390ecb233852ad
```
<img width="970" alt="Screenshot 2025-03-31 at 1 11 24 PM" src="https://github.com/user-attachments/assets/564ff01e-a651-4882-8b25-aeba200c0dc9" />
</br>
</br>

**Enter the SHA256 hash of file 1 into Valhalla. Is this file attributed to an APT group? (Yay/Nay)**
```shell
Yay
```

```shell
cd suspicious-files/file2/
sha256sum 1ndex.php

53fe44b4753874f079a936325d1fdc9b1691956a29c3aaf8643cdbd49f5984bf
```
<img width="967" alt="Screenshot 2025-03-31 at 1 15 15 PM" src="https://github.com/user-attachments/assets/27fcebf2-5fdc-4aab-a70d-182d44c665d4" />
</br>
</br>

**Do the same for file 2. What is the name of the first Yara rule to detect file 2?**
```shell
Webshell_b374k_rule1
```

<img width="1440" alt="Screenshot 2025-03-31 at 1 17 22 PM" src="https://github.com/user-attachments/assets/1b8eb714-9488-4a44-862c-85856f6ec0ef" />
</br>
</br>

**Examine the information for file 2 from Virus Total (VT). The Yara Signature Match is from what scanner?**
```shell
THOR APT Scanner
```

<img width="1440" alt="Screenshot 2025-03-31 at 1 19 19 PM" src="https://github.com/user-attachments/assets/10044970-e4e6-4554-8ff3-ab43599cab31" />
</br>
</br>

**Enter the SHA256 hash of file 2 into Virus Total. Did every AV detect this as malicious? (Yay/Nay)**
```shell
Nay
```
**Besides .PHP, what other extension is recorded for this file?**
```shell
EXE
```
**What JavaScript library is used by file 2?**
```shell
Zepto
```
**Is this Yara rule in the default Yara file Loki uses to detect these type of hack tools? (Yay/Nay)**
```shell
Nay
```
