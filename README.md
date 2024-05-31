# Active Defense with Honey Pot and Development of a Python Tool for Brute Force Attack Detection
## Project for the Academic year : 2023/2024

## Introduction:
As part of our final year project, we have chosen to focus on setting up a honeynet to enhance
active defense capabilities against cyberattacks. A honeypot is a system designed to attract
attackers by simulating vulnerabilities or security flaws, in order to detect, analyze, and
understand their techniques and behaviors. When multiple honeypots are integrated into a
network, it is referred to as a honeynet, which allows for more extensive monitoring and
in-depth analysis of compromise attempts.
We have chosen this topic due to its growing importance in the field of cybersecurity. With
the constant increase in cyber threats, companies and organizations are seeking proactive
ways to detect and prevent attacks. Honeynets offer an effective solution to trap attackers,
gather valuable intelligence, and improve defense strategies.

## Honeypot 1 Apache-Powered Honeybot Against SQL Injection
### Description of the Honeypot Architecture:
The honeypot architecture was designed to mimic a real web server environment (an
ecommerce website) while actively luring and capturing malicious activities from potential
attackers. The architecture consists of several key components:
- Apache Server: The core component of the honeybot infrastructure is the Apache
web server. Apache was chosen for its robustness, flexibility, and widespread usage in
the industry. It serves as the frontend for the honeypot, handling incoming HTTP
requests and responses.
- Database Backend: To simulate a typical web application scenario, a backend
database was set up. This database stores dummy data that the honeybot interacts
with, giving the appearance of a functioning web application to potential attackers.
We used Mysql
