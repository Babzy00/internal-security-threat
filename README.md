# internal-security-threat

## Activity Overview

In this activity, you will take on the role of a cybersecurity analyst working for a company that hosts the cooking website, yummyrecipesforme.com. Visitors to the website experience a security issue when loading the main webpage. Your job is to investigate, identify, document, and recommend a solution to the security problem. 

When investigating the security event, you will review a tcpdump log. You will need to identify the network protocols used to establish the connection between the user and the website. Network protocols are the communication rules and standards networked devices use to transmit data. Unfortunately, malicious actors can also use network protocols to invade and attack private networks. Knowing how to identify the protocols commonly used in attacks will help you protect your organization’s network against these types of security events.

To complete the assignment, you will also need to document what occurred during the security incident. Then, you will recommend one security measure to implement to prevent similar security problems in the future.

Be sure to complete this activity before moving on. The next course item will provide you with a completed exemplar to compare to your own work. 


## Scenario

Review the scenario below. Then complete the step-by-step instructions.

You are a cybersecurity analyst for yummyrecipesforme.com, a website that sells recipes and cookbooks. A former employee has decided to lure users to a fake website with malware. 

The baker executed a brute force attack to gain access to the web host. They repeatedly entered several known default passwords for the administrative account until they correctly guessed the right one. After they obtained the login credentials, they were able to access the admin panel and change the website’s source code. They embedded a javascript function in the source code that prompted visitors to download and run a file upon visiting the website. After embedding the malware, the baker changed the password to the administrative account. When customers download the file, they are redirected to a fake version of the website that contains the malware. 

Several hours after the attack, multiple customers emailed yummyrecipesforme’s helpdesk. They complained that the company’s website had prompted them to download a file to access free recipes. The customers claimed that, after running the file, the address of the website changed and their personal computers began running more slowly. 

In response to this incident, the website owner tries to log in to the admin panel but is unable to, so they reach out to the website hosting provider. You and other cybersecurity analysts are tasked with investigating this security event.

To address the incident, you create a sandbox environment to observe the suspicious website behavior. You run the network protocol analyzer tcpdump, then type in the URL for the website, yummyrecipesforme.com. As soon as the website loads, you are prompted to download an executable file to update your browser. You accept the download and allow the file to run. You then observe that your browser redirects you to a different URL, greatrecipesforme.com, which contains the malware.  

The logs show the following process:

1.The browser initiates a DNS request: It requests the IP address of the yummyrecipesforme.com URL from the DNS server.

2.The DNS replies with the correct IP address. 

3.The browser initiates an HTTP request: It requests the yummyrecipesforme.com webpage using the IP address sent by the DNS server.

4.The browser initiates the download of the malware.

5.The browser initiates a DNS request for greatrecipesforme.com.

6.The DNS server responds with the IP address for greatrecipesforme.com.

7.The browser initiates an HTTP request to the IP address for greatrecipesforme.com.

A senior analyst confirms that the website was compromised. The analyst checks the source code for the website. They notice that javascript code had been added to prompt website visitors to download an executable file. Analysis of the downloaded file found a script that redirects the visitors’ browsers from yummyrecipesforme.com to greatrecipesforme.com. 

The cybersecurity team reports that the web server was impacted by a brute force attack. The disgruntled baker was able to guess the password easily because the admin password was still set to the default password. Additionally, there were no controls in place to prevent a brute force attack. 

Your job is to document the incident in detail, including identifying the network protocols used to establish the connection between the user and the website.  You should also recommend a security action to take to prevent brute force attacks in the future.
<h2>Step 1: Accessing the template </h2>

[Cybersecurity incident report.pdf](https://github.com/kalemriah/Analyzing-A-Network-Attack/files/12285915/Cybersecurity.incident.report.pdf)

-----------------------------

### Cybersecurity Incident Report - Section One

### 1. Network Protocols Involved:

- DNS (Domain Name System) Protocol: Used to resolve the domain names (yummyrecipesforme.com and greatrecipesforme.com) to their corresponding IP addresses.

- HTTP (Hypertext Transfer Protocol): Used to request and retrieve web pages from the web server.

- JavaScript Execution: Involved in the execution of malicious scripts on the webpage.

### 2. Incident Documentation: Incident Overview: 
A former employee executed a brute force attack to gain access to the administrative account of the website yummyrecipesforme.com. They used known default passwords until they found the correct one. Once logged in, they embedded malicious JavaScript code in the website's source code, prompting visitors to download and run a malware file. This file redirected users to a fake website (greatrecipesforme.com), further spreading the malware.

#### Timeline of Events:

- Initial Access: The hacker gained access to the web host using brute force attack techniques.

- Modification of Website Code: The hacker embedded a JavaScript function to prompt downloads and redirect users.

- Discovery: Multiple customers reported the issue to the helpdesk, complaining about the download prompt and slow computer performance.

- Response: The website owner attempted to log into the admin panel but was blocked. The hosting provider was contacted, and a cybersecurity investigation was launched.

#### Investigation Findings:

- DNS Requests: The browser initiated DNS requests to resolve the IP addresses of yummyrecipesforme.com and greatrecipesforme.com.

- HTTP Requests: The browser made HTTP requests to load the web pages and download the malware.

- JavaScript Injection: The JavaScript code prompted users to download an executable file that redirected them to a malicious website.

- Brute Force Attack: The initial compromise was due to a brute force attack against the admin account with the default password.

#### Impacts on the Organization:

- Customer Trust: Loss of customer trust due to malware infection and redirection to fake websites.

- Operational Disruption: Inability to access the admin panel and compromised website functionality.

- Potential Data Breach: Risk of sensitive customer data being exposed or stolen.

### 3. Remediation for Brute Force Attacks: 
To prevent similar incidents in the future, the following security measures should be implemented:

- Enforce Strong Password Policies: Require the use of strong, unique passwords that are not default or easily guessable.

- Enable Account Lockout Mechanisms: Implement account lockout policies after a certain number of failed login attempts to prevent brute force attacks.

- Use Multi-Factor Authentication (MFA): Require an additional form of verification (e.g., SMS, authenticator app) for accessing admin accounts.

- Regular Security Audits: Conduct regular security audits and vulnerability assessments to identify and mitigate potential weaknesses.

- Monitor and Log Access Attempts: Continuously monitor and log access attempts to detect and respond to suspicious activity promptly.

<h2>Step 2: Accessing supporting materials </h2>

[Wireshark TCP_HTTP log - TCP log.pdf](https://github.com/kalemriah/Analyzing-A-Network-Attack/files/12285917/Wireshark.TCP_HTTP.log.-.TCP.log.pdf)

[How to read the Wireshark TCP_HTTP log.pdf](https://github.com/kalemriah/Analyzing-A-Network-Attack/files/12285918/How.to.read.the.Wireshark.TCP_HTTP.log.pdf)


<h2>Step 3: Identify the network protocol involved in the incident </h2>

---------------------------------

##  Analysis of Network Protocols Involved in the incident
Network Protocols Identified: From the tcpdump traffic log, the following network protocols were identified during the investigation:

### 1.DNS (Domain Name System) Protocol:

- DNS queries and responses for domain names yummyrecipesforme.com and greatrecipesforme.com.

- Examples from the log:

   - 14:18:32.192571 IP your.machine.52444 > dns.google.domain: 35084+ A? yummyrecipesforme.com. (24)

   - 14:18:32.204388 IP dns.google.domain > your.machine.52444: 35084 1/0/0 A 203.0.113.22 (40)

   - 14:20:32.192571 IP your.machine.52444 > dns.google.domain: 21899+ A? greatrecipesforme.com. (24)

   - 14:20:32.204388 IP dns.google.domain > your.machine.52444: 21899 1/0/0 A 192.0.2.17 (40)

### 2.HTTP (Hypertext Transfer Protocol):

- HTTP requests and responses between the user's machine and the web servers (yummyrecipesforme.com and greatrecipesforme.com).

- Examples from the log:

   - 14:18:36.786501 IP your.machine.36086 > yummyrecipesforme.com.http: Flags [S], seq 2873951608, win 65495, options [mss 
65495,sackOK,TS val 3302576859 ecr 0,nop,wscale 7], length 0

   - 14:18:36.786517 IP yummyrecipesforme.com.http > your.machine.36086: Flags [S.], seq 3984334959, ack 2873951609, win 65483, options [mss 65495,sackOK,TS val 3302576859 ecr 3302576859,nop,wscale 7], length 0

   - 14:18:36.786589 IP your.machine.36086 > yummyrecipesforme.com.http: Flags [P.], seq 1:74, ack 1, win 512, options [nop,nop,TS val 3302576859 ecr 3302576859], length 73: HTTP: GET / HTTP/1.1

   - 14:25:29.576493 IP your.machine.56378 > greatrecipesforme.com.http: Flags [S], seq 1020702883, win 65495, options [mss 65495,sackOK,TS val 3302989649 ecr 0,nop,wscale 7], length 0

   - 14:25:29.576510 IP greatrecipesforme.com.http > your.machine.56378: Flags [S.], seq 1993648018, ack 1020702884, win 65483, options [mss 65495,sackOK,TS val 3302989649 ecr 3302989649,nop,wscale 7], length 0

   - 14:25:29.576524 IP your.machine.56378 > greatrecipesforme.com.http: Flags [P.], seq 1:74, ack 1, win 512, options [nop,nop,TS val 3302989649 ecr 3302989649], length 73: HTTP: GET / HTTP/1.1

### Incident Documentation
Attack Description: The incident involved a brute force attack executed by a former employee to gain access to the administrative account of the website yummyrecipesforme.com. After successfully guessing the password, the attacker embedded malicious JavaScript code into the website's source code. This code prompted visitors to download and run a file, which contained malware that redirected their browsers to a fake website (greatrecipesforme.com).

#### Impact on the Organization’s Network:

- Resource Exhaustion: The server hosting yummyrecipesforme.com was compromised, affecting its ability to serve legitimate content.

- Customer Trust: Customers experienced slow computer performance and potential exposure to malware, leading to a loss of trust.

- Operational Disruption: The administrative access to the website was compromised, preventing normal operations and updates.

#### Potential Consequences:

- Data Breach: Personal and sensitive customer data could be exposed.

- Reputation Damage: Trust in the brand could be significantly affected due to the malware spread.

- Financial Loss: Loss of sales and increased costs for mitigating the attack and restoring services.

  <h2>Step 4: Document the incident </h2>

  Summarize the incident in the second section of the report. Provide as many details and facts as possible in your documentation. When writing the documentation, be sure to:

- Avoid using strong emotional language (good, terrible, awful, etc.).

- Include as many facts about the issue as you can, including where the incident occurred, how it happened, whether anyone witnessed it, how it was discovered, etc.

- Indicate your sources for information and evidence.

Writing accurate and detailed documentation for cybersecurity incidents can serve as a reference point for other cybersecurity analysts. Additionally, quality documentation can be used to educate other employees about cybersecurity measures taken within the company when incidents occur and can help businesses comply with various security audits.

---------------------------

## Cybersecurity Incident Report - Section Two: Detailed Incident Summary
Incident Overview: The website yummyrecipesforme.com experienced a security breach due to a brute force attack executed by a former employee. The attacker gained access to the administrative account by repeatedly trying known default passwords until the correct one was guessed. Once logged in, the attacker embedded malicious JavaScript code into the website's source code, which prompted users to download a malware-infected file. The attacker then changed the administrative password, preventing legitimate access to the admin panel.

## Timeline of Events:

1. Initial Compromise:

- When: The exact time of the initial breach is not detailed but discovered after customers reported issues.

- How: The attacker used a brute force attack to guess the administrative password.

- What Happened: The attacker logged into the admin panel and altered the website's source code to include a JavaScript function prompting users to download malware.

2. Discovery and User Reports:

- When: Several hours after the attack.

- How: Multiple customers reported to the helpdesk that they were prompted to download a file, which led to their computers running slowly and the website address changing.

- What Happened: Customers realized something was wrong when they were redirected to greatrecipesforme.com.

3. Internal Response:

- When: Upon receiving reports from customers.

- How: The website owner tried to access the admin panel but was locked out due to the password change.

- What Happened: The website owner contacted the hosting provider for assistance, leading to an internal cybersecurity investigation.

## Investigation Findings:

Network Protocols Involved:

DNS Protocol: Used to resolve domain names to IP addresses.

   - 14:18:32.192571 IP your.machine.52444 > dns.google.domain: 35084+ A? yummyrecipesforme.com. (24)

   - 14:18:32.204388 IP dns.google.domain > your.machine.52444: 35084 1/0/0 A 203.0.113.22 (40)

   - 14:20:32.192571 IP your.machine.52444 > dns.google.domain: 21899+ A? greatrecipesforme.com. (24)

   - 14:20:32.204388 IP dns.google.domain > your.machine.52444: 21899 1/0/0 A 192.0.2.17 (40)

HTTP Protocol: Used for web page requests and file downloads.

   - 14:18:36.786501 IP your.machine.36086 > yummyrecipesforme.com.http: Flags [S], seq 2873951608, win 65495, options [mss 65495,sackOK,TS val 3302576859 ecr 0,nop,wscale 7], length 0

   - 14:18:36.786517 IP yummyrecipesforme.com.http > your.machine.36086: Flags [S.], seq 3984334959, ack 2873951609, win 65483, options [mss 65495,sackOK,TS val 3302576859 ecr 3302576859,nop,wscale 7], length 0

   - 14:18:36.786529 IP your.machine.36086 > yummyrecipesforme.com.http: Flags [.] , ack 1, win 512, options [nop,nop,TS val 3302576859 ecr 3302576859], length 0

   - 14:18:36.786589 IP your.machine.36086 > yummyrecipesforme.com.http: Flags [P.], seq 1:74, ack 1, win 512, options [nop,nop,TS val 3302576859 ecr 3302576859], length 73: HTTP: GET / HTTP/1.1

   - 14:25:29.576493 IP your.machine.56378 > greatrecipesforme.com.http: Flags [S], seq 1020702883, win 65495, options [mss 65495,sackOK,TS val 3302989649 ecr 0,nop,wscale 7], length 0

   - 14:25:29.576510 IP greatrecipesforme.com.http > your.machine.56378: Flags [S.], seq 1993648018, ack 1020702884, win 65483, options [mss 65495,sackOK,TS val 3302989649 ecr 3302989649,nop,wscale 7], length 0

   - 14:25:29.576524 IP your.machine.56378 > greatrecipesforme.com.http: Flags [.] , ack 1, win 512, options [nop,nop,TS val 3302989649 ecr 3302989649], length 0

   - 14:25:29.576590 IP your.machine.56378 > greatrecipesforme.com.http: Flags [P.], seq 1:74, ack 1, win 512, options [nop,nop,TS val 3302989649 ecr 3302989649], length 73: HTTP: GET / HTTP/1.1

## Impact on the Organization’s Network:

- Customer Impact: Customers were tricked into downloading malware, leading to potential data breaches and compromised systems.

- Operational Impact: The administrative control of the website was compromised, preventing regular maintenance and updates.

- Reputational Impact: The incident damaged the company's reputation, leading to a loss of customer trust.

## Sources of Information:

- Customer Reports: Multiple emails to the helpdesk indicating issues with downloading files and slow computer performance.

- Network Traffic Logs: Tcpdump logs showing the DNS and HTTP requests and responses.

- Internal Investigation: Analysis by the cybersecurity team and senior analyst confirming the website compromise and source code modifications.

## Recommendations for Prevention:

- Enforce Strong Password Policies: Implement policies requiring complex, unique passwords that are not default or easily guessable.

- Enable Multi-Factor Authentication (MFA): Add an additional layer of security for accessing administrative accounts.

- Implement Account Lockout Mechanisms: Lock accounts after a specific number of failed login attempts to prevent brute force attacks.

- Regular Security Audits: Conduct periodic security audits and vulnerability assessments to identify and mitigate potential weaknesses.

- Continuous Monitoring: Monitor and log access attempts to detect and respond to suspicious activities promptly.

<h2>Step 5: Recommend one remediation for brute force attacks </h2>

After documenting the incident, write one recommendation to help your organization prevent brute force attacks in the future.

Some of the common security methods used to prevent brute force attacks include:

- Requiring strong passwords

- Enforcing two-factor authentication (2FA)

- Monitoring login attempts

- Requiring more frequent password changes

- Disallowing previous passwords from being used

- Limiting the number of login attempts

Select one security measure, and explain why it is effective in section three of the security incident report template.

The more safety measures that are in place, the less likely a malicious actor will be able to access sensitive information.

-----------------------------
## Remediation for Brute Force Attacks: 
To prevent similar incidents in the future, the following security measures are recommended:

- Enforce Strong Password Policies: Implement policies requiring strong, unique passwords that are not default or easily guessable.


