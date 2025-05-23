# Red-Team-Phishing-Simulation-Fake-Twitter-Login-Attack
Objective


This project simulates a phishing attack scenario as part of a red team operation. The purpose is to demonstrate how an attacker could gather intelligence using open-source techniques, craft a tailored phishing page, and extract sensitive user and device information—all without raising suspicion.

Disclaimer: This was performed in a local lab environment for ethical hacking training purposes only.


1. Reconnaissance (OSINT Phase)

Through open-source intelligence (OSINT), I conducted a realistic reconnaissance process:

•  Target was identified via LinkedIn.

•  Public posts and company structure revealed typical employee activity hours.
	
•  Social media profiles confirmed that the target frequently uses Twitter during work hours.
	
•  Email address format was deduced from company patterns and public data leaks.

2. Phishing Page Development

A cloned Twitter login page was created using HTML, CSS, and JavaScript to resemble the real interface.
	
<img width="743" alt="Screenshot 2025-05-22 at 23 58 41" src="https://github.com/user-attachments/assets/887c9abb-7211-4bd2-a88d-62d85f98294a" />

•  index.html simulates the Twitter login screen.

•  The JavaScript payload immediately collects victim metadata when the page is accessed—even before credentials are submitted.
<img width="732" alt="testing proejct 1" src="https://github.com/user-attachments/assets/b32fc403-4d44-4550-b1fa-5ba5960ab205" />



•  Upon clicking the “Log in” button:
	
 •	It captures the username, password
	
 •	Queries ipinfo.io to extract:
	
    1.	IP address
	
    2.	City, Region, Country
	
    3.	ISP (Org)
	
 •	It also logs:
	
   .	Browser (User-Agent)

   .	Operating System (Platform)
	
 •	Data is sent via a POST request to log_device.php.

 3. Backend Logging (log_device.php)

The PHP script receives the JSON POST request and writes the captured data to device_logs.txt.

Captured Fields:
	
•    Username
	
•    Password
	
•    IP Address
	
•    City, Region, Country

•    ISP (Org)

•    Browser

•    Platform

•    Timestamp

<img width="845" alt="Screenshot 2025-05-22 at 23 58 12" src="https://github.com/user-attachments/assets/b550efb9-bce3-405a-abf4-59b480c2a8da" />



4. Redirection Flow

After the credentials and metadata are captured:

•    The victim is immediately redirected to the official Twitter login page (https://twitter.com/login).

•    This makes it appear as though they simply mistyped their credentials or encountered a session timeout.

•    The seamless redirection adds credibility to the phishing attempt and helps avoid suspicion, increasing the likelihood that the user won’t realize their data was harvested.


5. Delivery Method

This simulation assumes the phishing link was delivered through a spoofed or compromised email:
	
•    Custom-crafted phishing email

•    Clickable link directed user to the hosted fake Twitter login

6. Environment
	
 •	Kali Linux (local Apache2 server)

 •	PHP 8.1

 •	VS Code

 •	ipinfo.io API (for geolocation data)

 •	Firefox for testing user-agent logging

 •	Custom JavaScript and PHP

 7. Future Improvements

To enhance realism and deployability:
	
 •	Host the phishing site on a VPS for public accessibility beyond LAN

 •	Add HTTPS encryption with self-signed or Let’s Encrypt certificates

 •	Implement webhooks for real-time alerts when credentials are captured

 •	Log device fingerprinting details for better victim profiling

 •	Package into a toolkit for ethical simulation demos

8. Screenshots

(Screenshots showing the login page, captured log files, terminal logs)

<img width="1222" alt="Screenshot 2025-05-23 at 00 08 40" src="https://github.com/user-attachments/assets/5e8096ca-9fc7-40f2-adb6-8f5409c3c33e" />

<img width="1157" alt="testing project" src="https://github.com/user-attachments/assets/d0988cd0-380e-44e3-b5bb-0f3e2f3f4077" />




9. Disclaimer

This is a red team simulation exercise designed for ethical hacking and educational purposes only.
No real users were targeted or harmed. All actions were performed within a controlled lab environment.
