\#  Threat Hunt: Suspicious File Drop - `evil.exe`



\##  Objective



Detect the presence of a suspicious `.exe` file named `evil.exe` dropped into a publicly accessible folder (`C:\\Users\\Public\\`) — a common tactic for lateral movement or execution.



---



\##  Setup



This hunt is performed on a Windows 11 VM (`windows-wazuh-a`) with Velociraptor agent already installed and connected to the server.



\### MITRE ATT\&CK Mapping



\- \*\*T1105 – Ingress Tool Transfer\*\*

\- \*\*T1204.002 – User Execution: Malicious File\*\*

\- \*\*T1036 – Masquerading\*\*



---



\##  Velociraptor Hunt Configuration



\###  Artifact Selected



\- `Windows.Search.FileFinder`



\###  Hunt Target



\- Path: `C:\\Users\\Public\\`

\- Match: Any `.exe` file (especially `evil.exe`)



---



\###  Parameters Used



| Parameter        | Value                         |

|------------------|-------------------------------|

| path             | `C:\\Users\\Public`             |

| max\_depth        | `1`                           |

| filename\_glob    | `\*.exe`                       |

| accessor         | `ntfs`                        |



---



\##  Expected Detection



We expect the hunt to return a result showing:



\- A file named `evil.exe`

\- Located at: `C:\\Users\\Public\\evil.exe`

\- File metadata such as size (~360KB), creation timestamp, etc.



---



\##  Next Steps



\- Flag or delete `evil.exe`

\- Investigate who/what created the file

\- Correlate with PowerShell logs or user activity



---



\##  Related Simulation



Refer to the simulation steps in \[`file-drop.md`](../simulations/file-drop.md) for how the `evil.exe` file was created.





