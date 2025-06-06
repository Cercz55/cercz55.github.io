---
title: RedLine Stealer OSINT
date: 2024-11-25
layout: post
---
Scenario:  
You are part of the Threat Intelligence team in the SOC (Security Operations Center). An  
executable file has been discovered on a colleague's computer, and it's suspected to be linked to a Command and Control (C2) server, indicating a potential malware infection.  
Your task is to investigate this executable by analyzing its hash. The goal is to gather and analyze data that is beneficial to other SOC members, including the Incident Response team, in order to efficiently respond to this suspicious behavior.
 
Tools:  
• Whois  
• VirusTotal  
• MalwareBazaar  
• ThreatFox

File involved: 
SHA256: 248FCC901AFF4E4B4C48C91E4D78A939BF681C9A1BC24ADDC3551B32768F907B

**Questions**
 
Q1. Categorizing malware allows for a quicker and easier understanding of the malware, aiding in  
understanding its distinct behaviors and attack vectors. What's the identified malware's  
category?  

*= trojan*
 
When we look for the malware hash, we instantly get its identified categories, which in most  
antivirus engines was “Trojan”.

![image](/assets/images/20241124162834-0.png)

Q2. Clear identification of the malware file name facilitates better communication among the  
SOC team. What's the file name associated with this malware?  

*= WEXTRACT*
 
Going to the Details section in VirusTotal, we can see the names seen for the file we’re  
investigating. In this case, we saw a couple but the most repeated was “WEXTRACT”

![image](/assets/images/20241124162835-1.png)

Q3. Knowing the exact time the malware was first seen can help prioritize actions. If the malware is newly detected, it may warrant more urgent containment and eradication efforts compared to older, well-known threats. Can you provide the UTC timestamp of first submission of this malware on VirusTotal?  

*= 2023-10-06 04:41:50 UTC*

![image](/assets/images/20241124162836-2.png)

Q4. Understanding the techniques used by malware helps in strategic security planning. What is the MITRE ATT&CK technique ID for the malware's data collection from the system before exfiltration?  

*= T1005*
 
Under the Behavior section in VirusTotal, we can find the MITRE ATT&CK Tactics and Techniques.

![image](/assets/images/20241124162838-3.png)

Q5. Following execution, what domain name resolution is performed by the malware?  

*= facebook[.]com*

![image](/assets/images/20241124162840-4.png)

Q6. Once the malicious IP addresses are identified, network security devices such as firewalls can be configured to block traffic to and from these addresses. Can you provide the IP address and destination port the malware communicates with?  

*= 77.91.124.55:19071*

![image](/assets/images/20241124162842-5.png)

Q7. If a hosting service is frequently used for malicious activities, security teams can implement a strict filtering rules for all traffic to and from the IPS belonging to that hosting provider. What hosting service does the identified IP belong to?  

*= YeezyHost*
 
I took the malicious IP address I identified in the last question and then looked for it WhoIs  
information, which is embedded in VirusTotal now.

![image](/assets/images/20241124162846-6.png)

Q8. YARA rules are designed to identify specific malware patterns and behaviors. What's the name of the YARA rule created by "Varp0s" that detects the identified malware?  

*= detect_Redline_Stealer*
 
MalwareBazaar is better, in my opinion, for seeing Yara signatures data.

![image](/assets/images/20241124162848-7.png)

Q9. Understanding which malware families are targeting the organization helps in strategic  
security planning for the future and prioritizing resources based on the threat. Can you provide the different malware alias associated with the malicious IP address?  

*= RECORDSTEALER*
 
I didn’t find any info related this question in the mentioned websites so I went to malpedia and the  
first thing I saw was the alias I was looking for.

![image](/assets/images/20241124162849-8.png)

Q10. By identifying the malware's imported DLLs, we can configure security tools to monitor for the loading or unusual usage of these specific DLLs. Can you provide the DLL utilized by the malware for privilege escalation?  

*= advapi32.dll*

This one is a very common dll abused for privilege escalation.
 
And that would be it.  
Thanks.
 
Author: Cesar Cruz.
