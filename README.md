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


# Conclusion
Understanding these detection methods is crucial for maintaining robust security postures and highlights the importance of augmenting automated defenses with detailed log analysis.
This lab helps us to see why it is so important to go beyond automated defenses and include detailed log analysis in your security strategy.
