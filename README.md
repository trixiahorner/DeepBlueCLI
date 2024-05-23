# Beyond EDR and XDR: Using DeepBlueCLI to Identify Bypass Techniques
Relying solely on Endpoint Detection and Response (EDR) and Extended Detection and Response (XDR) platforms is insufficient. While these tools provide significant protection, attackers continually develop sophisticated methods to bypass them. This lab writeup explores the use of DeepBlueCLI, a powerful command-line tool for analyzing Windows Event Logs, to detect potential security incidents that may evade EDR and XDR systems. Specifically, we will demonstrate how to use DeepBlueCLI to identify new user additions, password spray attacks, and obfuscation techniques. 

## Environment
This lab is part of Antisyphon Training's SOC Core Skills course with John Strand. Visit [Antisyphon](https://www.antisyphontraining.com/) for more information.
<br>
<br>

## Setup
1. Navigate to the DeepBlueCLI directory
2. Enter *powershell*
3. Set-ExecutionPolicy *unrestricted* so we can run the scripts without any restrictions
```
cd \tools\DeepBlueCLI-master
powershell
Set-ExecutionPolicy unrestricted
```
![set-execution](https://github.com/trixiahorner/DeepBlueCLI/blob/main/images/D1.png?raw=true)
<br>
<br>

## Methodology
### Check for *new user* add
It is very common for attackers to add additional users on to a system they have compromised. This gives them a level of persistence that they otherwise would not gain with malware. Why? There are lots and lots of tools to detect malware. By creating an extra user account it allows them to blend in.
<br>
We can check the .evtx files for adding a new user. (Choose R when prompted)
```
.\DeepBlue.ps1 .\evtx\new-user-security.evtx
```
![set-execution](https://github.com/trixiahorner/DeepBlueCLI/blob/main/images/D2.png?raw=true)
<br>
We see 2 entries where new users were added. The first entry with *'username -'* shows a user added to the local Administrators group and worth investigating. 
<br>
<br>

### Detecting password attacks
Another attack that very few SIEMs detect is password spraying. This is where an attacker takes a user list from a domain, and sprays it with the same password. Password sprays are effective because it keeps the lockout threshold below the lockout policy and many times flies under the radar simply because accounts are not getting locked out. But, this is the exact behavior that UEBA should be able to detect. 
<br>
Let's look at an event log with a password guessing attack. This is very much part of what a full UEBA(User and Entity Behavior Analytics) solution does:
```
.\DeepBlue.ps1 .\evtx\smb-password-guessing-security.evtx
```
![set-execution](https://github.com/trixiahorner/DeepBlueCLI/blob/main/images/D3.png?raw=true)
<br>

# Conclusion
Understanding these detection methods is crucial for maintaining robust security postures and highlights the importance of augmenting automated defenses with detailed log analysis.
This lab helps us to see why it is so important to go beyond automated defenses and include detailed log analysis in your security strategy.
