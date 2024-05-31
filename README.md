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

## Honeypot 1 Apache-Powered HoneyPot Against SQL Injection
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
- Logging : we used ModSecurity
- Honeypot Modules: Within the honeybot environment, various options exist for
deploying honeypot modules to emulate vulnerable components. In our
implementation, we deliberately omitted input validation and sanitization techniques
from the backend code of a deceptive search bar, making it appear susceptible to
SQL injection attacks. This tactic aimed to lure potential attackers, who could then
manipulate SQL queries and potentially extract sensitive data from the database.

![image](https://github.com/Stiegler0/Honeypot-Project/assets/145070468/bf75e8e5-9f03-44a5-9e1e-be63f9fe4d37)

### Hardening Apache:
Improving Security: The steps provided will help improve Apache’s security to a
basic level suitable for our specific project (the honeypot web server).
● We can mitigate risks discovered by whatweb tool by modifying a couple of the
Apache configuration files. The first one we can modify is the
/etc/apache2/conf-available/security.conf file which will help limit the amount of
data that is shared about the web service. We’ll modify this file by changing the value
for the ServerTokens directive from ‘OS’ to ‘Prod’ using the sed com
sed -i 's/ServerTokens OS/ServerTokens Prod/' /etc/apache2/conf-available/security.conf

![image](https://github.com/Stiegler0/Honeypot-Project/assets/145070468/00c1200c-9b93-4a40-9ea7-f3eb29132855)

● anticlickjack:
Anticlickjacking is a security measure designed to protect websites from clickjacking attacks,
where a malicious site overlays transparent or opaque frames to trick users into clicking on
elements that perform unintended actions, such as changing settings or making transactions.
We performed a sanity check by running a scan against our web server using the nikto tool
We can see anticlickjack is not present in our server:

![image](https://github.com/Stiegler0/Honeypot-Project/assets/145070468/e41f8254-96b5-4e52-b0f4-384843dfc6e5)


### Attack Scenario and Detection:
- SQL Injection Attack: An attacker discovers our ecommerce website and begins
searching for vulnerabilities. They attempt a SQL injection attack by submitting a
malicious request through a search form on the site. They can use tools like: sqlmap

![image](https://github.com/Stiegler0/Honeypot-Project/assets/145070468/8958bf68-6375-419c-93fa-3775746cf6ad)

![image](https://github.com/Stiegler0/Honeypot-Project/assets/145070468/7bcfc9ec-8176-450d-bc7a-6fa06cd6de02)

### Analysis and Response: Our administrators analyze the honeypot logs to understand
the nature of the attack. They notice repeated attempts by the attacker to exploit SQL
vulnerabilities. With the collected information, We can:
● Block the attacker's IP address on our real servers.
● Update their firewall rules to prevent similar attacks.
● Inform their development team to further secure web forms against SQL
injections.
For Analysis we used goaccess tool for visualization, GoAccess is an open source real-time
web log analyzer and interactive viewer that runs in a terminal in *nix systems or through our
browser.

![image](https://github.com/Stiegler0/Honeypot-Project/assets/145070468/5e7cd5b3-a795-4c41-9495-0ca84d19036e)

![image](https://github.com/Stiegler0/Honeypot-Project/assets/145070468/21e95bd2-f7f2-4597-87fb-b9264d3e3101)

