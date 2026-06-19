## Week 1: Advanced Reconnaissance & Footprinting

#### ● Goal: To gather as much information as possible about the target's digital  presence.

#### ● Target: Certfied Hacker

#### ● Tasks:

○ Use Google Dorks to find sensitive files (PDFs, Log files) exposed by a target domain.

Objective: Identifying exposed sensitive files and directories on the target domain using  Google Dorks.

#### 1. Searching for PDF Files

Search Query Used: site:certifiedhacker.com filetype:pdf

Purpose:  This query identifies publicly available PDF documents on the target domain.      Observation:  Multiple PDF files indexed by Google which are publicly accessible.    Security Impact:

<img src= "https://github.com/Endlesscyber/CFSS-Cyber-Forensics-Security-Solutions/blob/445854226334a7295bc2e8759e78a98020c9f349/Week%201/Week%201_images/page_1_img_10.png">


PDF files may contain internal documents, reports, policies or confidential information that could be  useful to an attacker. 
#### 2. Finding Open Directories (Index Of)

Search Query Used: site:target.com intitle:"index of"

Purpose:  To detect open directory listing.    Observation:  Some directories publicly accessible this world file listing visible this.    Security Impact:  Open directory listing can leak backup files, configuration files, and sensitive data.

<img src="https://github.com/Endlesscyber/CFSS-Cyber-Forensics-Security-Solutions/blob/445854226334a7295bc2e8759e78a98020c9f349/Week%201/Week%201_images/page_2_img_4.png">



#### 3. Domain-Wide Search

Search Query Used: site:target.com

Purpose:  Identifying the total indexed pages of the target domain.    Observation:  Multiple URLs and subpages are indexed, which indicate the attack surface.    Security Impact:  More indexed pages means more exposure and potential misconfigurations.

<img src="https://github.com/Endlesscyber/CFSS-Cyber-Forensics-Security-Solutions/blob/445854226334a7295bc2e8759e78a98020c9f349/Week%201/Week%201_images/page_3_img_7.png">



### ○ Use theHarvester to find leaked email addresses and subdomains.

#### Objective

To identify publicly exposed email addresses, subdomains, and related information  associated with the target domain using open-source intelligence (OSINT) techniques.

Tool Used : theHarvester

theHarvester is an OSINT tool used to gather emails, subdomains, IP addresses, and host  information from public sources such as Baidu, Bing, Yahoo, LinkedIn, and other search  engines.

Command Executed : theHarvester -d target.com -b all

Command Explanation:

•  -d → Specifies the target domain

•  -b → Specifies the data source (google, bing, yahoo, all, etc.)

Information Collected

During the reconnaissance process, the following information was identified:

•  Publicly available email addresses

•  Subdomains associated with the target

•  Hostnames and related IP addresses

Findings

Email Addresses : During this scan we cant find any email by this tools but we can find it  alternative option from websites.

<img src="https://github.com/Endlesscyber/CFSS-Cyber-Forensics-Security-Solutions/blob/445854226334a7295bc2e8759e78a98020c9f349/Week%201/Week%201_images/page_4_img_17.png">

<img src="https://github.com/Endlesscyber/CFSS-Cyber-Forensics-Security-Solutions/blob/445854226334a7295bc2e8759e78a98020c9f349/Week%201/Week%201_images/page_5_img_1.png">

<img src="https://github.com/Endlesscyber/CFSS-Cyber-Forensics-Security-Solutions/blob/445854226334a7295bc2e8759e78a98020c9f349/Week%201/Week%201_images/page_5_img_2.png">


Subdomains

Multiple subdomains were identified, expanding the attack surface of the organization.  Some subdomains may host:

•  Development environments

•  Testing servers

•  Admin panels

•  Legacy systems

○ Perform Banner Grabbing to identify hidden versions of web servers and  SSH services.

### Objective: To identify the underlying web server and SSH service versions running on the  target system by performing banner grabbing techniques.

#### What is Banner Grabbing?

Banner grabbing is a reconnaissance technique used to extract service information such as:

•  Service name

•  Software version

•  Operating system details

This information helps in identifying outdated or vulnerable services.

Web Server Banner Grabbing

- Using Curl

Command: curl -I http://target.com

Analysis of Output

Server: Apache

The target is running Apache Web Server.

•  No version information was disclosed.

•  This indicates that detailed server version disclosure is disabled.

Security Positive Point  Hiding version information reduces exposure to version-specific attacks.
<!-- Page 7 -->

2. SSH Banner Grabbing

- Using Netcat

Command: nc target.com 22

<img src="https://github.com/Endlesscyber/CFSS-Cyber-Forensics-Security-Solutions/blob/445854226334a7295bc2e8759e78a98020c9f349/Week%201/Week%201_images/page_7_img_7.png">

<img src="https://github.com/Endlesscyber/CFSS-Cyber-Forensics-Security-Solutions/blob/445854226334a7295bc2e8759e78a98020c9f349/Week%201/Week%201_images/page_7_img_8.png">


#### Observation

The SSH service is running:

• OpenSSH version 8.7

Target Question: "Can you find the 'robots.txt' file of a target and identify  hidden directories that should not be indexed by search engines?

#### Methodology

The robots.txt file was manually checked by navigating to:

http://certifiedhacker.com/robots.txt

#### Findings

After accessing the URL, the following result was observed:

•  The robots.txt file was not found.

•  The server returned either:

o 404 Not Found

o Or no robots.txt response

#### Analysis

The absence of a robots.txt file indicates:

•  The website does not explicitly restrict search engine crawlers.

•  All publicly accessible directories may be indexed by default.

•  No hidden directories were disclosed through robots.txt.

<img src="https://github.com/Endlesscyber/CFSS-Cyber-Forensics-Security-Solutions/blob/445854226334a7295bc2e8759e78a98020c9f349/Week%201/Week%201_images/page_8_img_23.png">


#### Summary

I carried out an advanced reconnaissance and footprinting assessment of the  target domain in Week 1. The goal was to collect as much publicly accessible  data as possible without tampering with or abusing the system.    The following tasks were completed:

• indexed pages, open directories, and exposed PDFs using Google Dorks.  used theHarvester to enumerate emails and subdomains.  • carried out banner grabbing to find protocol support and web server  information.  • looked for hidden directories in the robots.txt file.  • I now have a better grasp of how important reconnaissance is to  penetration testing thanks to this exercise.

The significance of reducing information exposure and putting in place  appropriate security configurations is emphasized in this phase.
