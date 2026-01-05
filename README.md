# Lab - Use the OWASP Web Security Testing Guide

## Disclaimer
This repository contains materials and outputs from a structured educational lab focused on ethical hacking and web application security testing. 
All activities documented here were performed in a controlled, authorized learning environment using intentionally vulnerable test applications or resources provided for educational purposes only.
No real-world systems were targeted without explicit permission. 
The content is for academic and skill-development use only and should not be applied to any system without proper authorization.

## Objectives
In this lab, I completed the following objectives:

- Part 1: Investigate the WSTG
- Part 2: Scan a Website and Investigate Vulnerability References

## Background / Scenario
The Open Worldwide Application Security Project (OWASP) nonprofit foundation developed the Web Security Testing Guide (WSTG) to test the most common web application security issues. 
The guide is useful for various stakeholders such as developers, software testers, security specialists, and project managers.
The OWASP Web Security Testing Guide is a free tool that is available to organizations and individuals.
The testing guide is also a useful tool for ethical hacking. 
Ethical hackers can use the guide to test their clients’ running web applications for common security vulnerabilities.

In this lab, I reviewed the WSTG and then scanned a web application for vulnerabilities using the OWASP Zed Attack Proxy (ZAP).
I investigated some of the vulnerabilities that were discovered and referenced one back to the WSTG.

## Required Resources
- Kali VM customized for the Ethical Hacker course
- Internet access


## Part 1: Investigate the WSTG

### Step 1: Explore the OWASP WSTG Project Site
I navigated to the OWASP Web Security Testing Guide site at https://owasp.org/www-project-web-security-testing-guide/ and reviewed the information on the main page.

Key information from the main page:

- The OWASP Web Security Testing Guide (WSTG) is a comprehensive resource for testing the security of web applications and web services.
- It is aimed at web application developers and security professionals.
- The guide provides a framework of best practices for penetration testers and organizations worldwide.
- It has been developed collaboratively by cybersecurity professionals and volunteers.

- The latest stable version is v4.2, released on 2020-12-03.
- This version introduced new testing scenarios, updates to existing chapters, and improvements to writing style and chapter layout.
- The stable version is available online, and a PDF download is provided at https://github.com/OWASP/wstg/releases/download/v4.2/wstg-v4.2.pdf.

- Testing scenarios are identified by codes in the format WSTG-<category>-<number> (e.g., WSTG-INFO-02 for Information Gathering).
- For consistency, it is recommended to reference versioned codes (e.g., WSTG-v42-INFO-02).

- The main sections are organized into categories such as Information Gathering, with versioned links available (e.g., https://owasp.org/www-project-web-security-testing-guide/v42/4-Web_Application_Security_Testing/01-Information_Gathering/02-Fingerprint_Web_Server).



## Part 2: Scan a Website and Investigate Vulnerability References
In this part of the lab, I conducted a vulnerability scan using the Zed Attack Proxy (ZAP). 
My target was an intentionally vulnerable website available on my VM. 
I then used the WSTG to learn more about a vulnerability that I discovered.

### Step 1: Open ZAP and Start a Scanning
I started the Kali VM as needed. I navigated to the Kali menu, searched for ZAP, and started the OWASP ZAP scanner.

I clicked the topmost radio button to persist the session. This means that I can return to the session at a later time.

I closed the Manage Add-ons dialog window.

In the ZAP main window, I clicked the Automated Scan button to initiate a scan.


<img width="952" height="1002" alt="11 zap page" src="https://github.com/user-attachments/assets/7ad1e88f-a330-4998-8413-5e95c920a37f" />




In the URL to Attack field, I entered `172.17.0.2/dvwa`.





<img width="957" height="998" alt="2 attack box" src="https://github.com/user-attachments/assets/683f7277-6eeb-4752-a824-293b7ddd96b9" />




I clicked the Attack button to begin the scan. The scan took less than 10 minutes to complete.




<img width="955" height="1000" alt="3 scan complete" src="https://github.com/user-attachments/assets/2be1ba84-4751-40c6-ab48-242015722dd8" />




First, ZAP used a web spider to crawl the URL to identify the resources that were available there. It then applied vulnerability scans to each resource.

## INVESTIGATE THE RESULTS

To the alerts tab, 15 alerts were returned

Locate and click the Remote Code Execution – CVE-2012-1823 alert. Scroll through the details of the alert.
Source of CVE-2012-1823 is an out-of-date PHP version
PHP code can be injected into a PHP query sting. This code can will execute at the PHP exec.


<img width="953" height="1002" alt="4 remote code execution" src="https://github.com/user-attachments/assets/a8691134-9156-4186-81a5-fef2fe7493be" />












