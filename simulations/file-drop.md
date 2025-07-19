\#  Simulation: Suspicious File Drop in Public Folder



\##  Overview



This simulation demonstrates how an attacker might drop a suspicious executable (`evil.exe`) into a publicly accessible folder (`C:\\Users\\Public\\`). This behavior is commonly used during malware delivery, lateral movement, or persistence strategies.



\##  Objective



Mimic an attacker placing a malicious `.exe` file in a shared folder and verify its presence. Later, we'll hunt for this file using Velociraptor.



\##  MITRE ATT\&CK Mapping



| Tactic             | Technique                            |

|--------------------|---------------------------------------|

| Execution, Defense Evasion | \[T1204.002 - Malicious File](https://attack.mitre.org/techniques/T1204/002/) |

| Collection         | \[T1005 - Data from Local System](https://attack.mitre.org/techniques/T1005/) |



\##  Tools Used



\- \*\*Windows 11 Enterprise Evaluation VM\*\*

\- \*\*Velociraptor agent installed\*\*

\- \*\*PowerShell 7.5.2 (Administrator)\*\*



---



\##  Simulation Steps (Attacker Behavior)



1\. \*\*Log in to the Windows VM as Administrator.\*\*

2\. \*\*Open PowerShell 7.5.2\*\* with administrative privileges.

3\. \*\*Run the following commands:\*\*



```powershell

\# Step 1: Copy a legitimate binary (Notepad) as fake malware

Copy-Item "C:\\Windows\\System32\\notepad.exe" "C:\\Users\\Public\\evil.exe"



\# Step 2: Confirm the drop

Get-Item "C:\\Users\\Public\\evil.exe"





&nbsp;Output Example



Directory: C:\\Users\\Public



Mode                LastWriteTime         Length Name

----                -------------         ------ ----

-a----        7/14/2025   9:44 PM         360448 evil.exe



This simulates a real-world attacker who places a renamed executable in a shared directory that others (or malware) can access and execute later.



