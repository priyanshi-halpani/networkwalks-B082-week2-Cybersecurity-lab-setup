# Penetration Testing Report
## Footprinting & Network Scanning Phases

**W2-PM-FINAL | Cybersecurity | Networkwalks**

---

## Project Information

| Field | Details |
|---|---|
| **Pentester Name** | Priyanshi Halpani |
| **Program / Batch** | B082 - Networkwalks |
| **Date** | 20 August 2026 |
| **Program** | Cybersecurity & Ethical Hacking |
| **Modules Completed** | W2-PM1 - Multiple Kali Tools |
| | W2-PM3 - Footprinting with Maltego |
| | W2-PM5 - Zenmap Scanning |
| **Client / Target** | Networkwalks (`networkwalks.com`) |
| **Network Target** | My own local LAN |
| **Authorization** | Yes |
| **Phases Covered** | Phase 1: Reconnaissance & Footprinting |
| | Phase 2: Scanning & Network Discovery |
| **Phases 3-5** | In Progress |

---

# 1. Liability Disclaimer

I have performed these activities only on systems and devices for which I had proper authorization or that I personally own. These activities were carried out strictly for educational and research purposes as part of my cybersecurity training.

The information and techniques presented in this report should not be used for unauthorized access, testing, or any illegal activity. I take full responsibility for the activities performed and the use of the knowledge gained from this practical work.

Any reconnaissance, scanning, or security testing should always be conducted within an authorized scope and with appropriate permission. Unauthorized access or testing of computer systems and networks may have legal and professional consequences.

---

# 2. Introduction

This report covers footprinting and reconnaissance of the `networkwalks.com` domain using multiple Kali Linux tools and Maltego, along with network scanning of my own local network using Nmap/Zenmap.

The activities cover the footprinting and scanning phases, demonstrating how publicly available information can be collected and correlated before identifying live hosts and services on a network.

This report documents the Week 2 activities completed as part of my ongoing Cybersecurity & Ethical Hacking internship program at Networkwalks.

The footprinting activities were performed using Kali Linux, while network scanning was conducted using Zenmap/Nmap on a Windows PC.

The tools were used to collect domain, web technology, DNS, WAF, email and network information. Maltego was additionally used to visualize relationships between the domain and publicly available information.

Each activity includes the command or procedure used, the observed result, supporting evidence, and a brief explanation of the security relevance of the finding.

---

# 3. Tools Used

| Tool | Purpose |
|---|---|
| **Kali Linux** | Operating system used for footprinting and reconnaissance activities |
| **WHOIS** | Obtain domain registration information, registrar details, dates and name servers |
| **WhatWeb** | Identify web technologies, CMS, plugins, server information and other technologies |
| **Nslookup** | Resolve a domain name to its IP address using DNS |
| **Curl** | Inspect HTTP response headers and web server information |
| **Wafw00f** | Identify whether a Web Application Firewall protects the website |
| **DNSRecon** | Enumerate DNS records such as NS, MX, SPF, TXT and SRV records |
| **Maltego** | Visualize relationships between domains, email addresses and other publicly available entities |
| **Zenmap / Nmap** | Discover live hosts, open ports and basic network information |
| **Windows CMD** | Identify local IP address, subnet and MAC address information using commands such as `ipconfig` |

---

# 4. Activities Performed

## 4.1 Footprinting & Reconnaissance

I performed reconnaissance on `networkwalks.com` using six Kali Linux tools:

- WHOIS
- WhatWeb
- Nslookup
- Curl
- Wafw00f
- DNSRecon

I also used **Maltego** to visualize relationships between the domain and publicly available email information.

### 4.1.1 WHOIS

WHOIS was used to obtain publicly available domain registration information.

The results provided information including:

- Registrar
- Domain registration date
- Domain expiration date
- Domain status
- Name servers
- Registration information

The domain was registered through **GoDaddy.com, LLC**.

---

### 4.1.2 WhatWeb

WhatWeb was used to identify technologies used by the website.

The results identified:

- Apache
- WordPress 7.0.4
- WordPress Download Manager 3.3.58
- jQuery 3.7.1
- Bootstrap
- Google Tag Manager
- HTML5

The website resolved to:
192.232.216.135

###  Maltego

Finally, Maltego was used to visually correlate and represent publicly available information associated with the networkwalks.com domain.

The Maltego graph represented the relationship between the domain and publicly available email information.

This helped me understand how individual pieces of publicly available information can be correlated during reconnaissance and represented as a connected graph.

All activities were conducted for authorized information gathering and analysis, with no exploitation or unauthorized access performed.

## 4.2 Network Scanning with Nmap / Zenmap

For the second activity, I used Nmap through Zenmap to perform network discovery on my own local network.

The practical required me to identify my local IP address and subnet, discover live hosts, identify their IP and MAC addresses, identify open ports and services, and generate a network topology.

I first used the Windows ipconfig command to identify my local IP address and LAN subnet.

The Nmap scan covered:

256 IP addresses

The scan identified:

3 hosts up
Host 1 - 192.168.201.1

The first active host identified was:

192.168.201.1

Result:

Host is up (0.13s latency).


Not shown: 99 closed tcp ports (reset)


PORT   STATE SERVICE
80/tcp open  http


MAC Address:
00:1E:A6:95:0F:C8


MAC Vendor:
Best IT World (India) Pvt.

The host had port 80/tcp open, providing an HTTP service.

Host 2 - 192.168.201.100

The second active host identified was:

192.168.201.100

Result:

Host is up (0.46s latency).


All 100 scanned ports on 192.168.201.100 are in ignored states.


Not shown: 100 closed tcp ports (reset)


MAC Address:
B4:C4:FC:CB:53:29


MAC Vendor:
Xiaomi Communications

The host was active, but all 100 scanned TCP ports were reported as closed.

Host 3 - 192.168.201.103

The third active host identified was:

192.168.201.103

Result:

Host is up (0.0018s latency).


Not shown: 96 closed tcp ports (reset)


PORT     STATE SERVICE
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
9999/tcp open  abyss

The host exposed four open TCP ports:

Port	Service
135/tcp	MSRPC
139/tcp	NetBIOS
445/tcp	Microsoft-DS
9999/tcp	Abyss
Nmap Scan Summary

The final Nmap output showed:

Nmap done: 256 IP addresses (3 hosts up) scanned in 18.63 seconds
IP Address	Status	Open Ports	Service
192.168.201.1	Host Up	80/tcp	HTTP
192.168.201.100	Host Up	None of the 100 scanned ports	All scanned ports closed
192.168.201.103	Host Up	135/tcp, 139/tcp, 445/tcp, 9999/tcp	MSRPC, NetBIOS, Microsoft-DS, Abyss
5. Risk Analysis / Impact

Based on the information collected during the footprinting and network scanning activities, I identified the following potential risks.

---

## 5.	Risk / Finding	Evidence / Observation	Potential Impact	Risk Level
- 1	Web technology information exposed	WhatWeb identified WordPress 7.0.4, WordPress Download Manager 3.3.58, Apache and jQuery 3.7.1	Attackers may use exposed technology/version information to identify software requiring further security review	● Medium 
- 2	Server IP address identifiable	Nslookup resolved the domain to 192.232.216.135	Provides information about the network location of the web service	● Low 
- 3	HTTP technical information exposed	Curl returned HTTP response headers and exposed /wp-json/	May assist technology fingerprinting and further enumeration	● Low 
- 4	WordPress REST API endpoint exposed	Curl identified /wp-json/	May provide publicly accessible information about the WordPress installation	● Low 
- 5	WAF technology identifiable	Wafw00f identified ModSecurity (SpiderLabs)	Reveals information about the web application's security architecture	● Low
- 6	DNS infrastructure information exposed	DNSRecon identified DNS, mail and service-related records	DNS information can help build a broader infrastructure profile	● Medium
- 7	DNS software information exposed	DNSRecon identified Bind 9.16.23-RH	Software information may assist further reconnaissance	● Medium
- 8	Multiple live hosts visible on local network	Nmap identified three live hosts in the local network	Unknown or unauthorized devices may potentially be present on a network	● Medium
- 9	Multiple services exposed on internal host	Nmap identified ports 135, 139, 445 and 9999 on 192.168.201.103	Multiple exposed services increase the attack surface and should be reviewed	● Medium
- 10	HTTP service exposed on internal host	Nmap identified port 80/tcp on 192.168.201.1	May expose a web or management service requiring security review	● Low
- Risk Level Key

● Critical
● Medium
● Low

- The risks above are observations from the footprinting, reconnaissance and network-scanning exercises and should not be interpreted as confirmed vulnerabilities.

- The activities primarily involved passive/public information gathering, service identification and network discovery. Although several technologies, services and versions were identified, the results alone do not confirm that any of them are vulnerable.

- For example, the identification of WordPress 7.0.4, Apache, Bind 9.16.23-RH or the open ports discovered by Nmap indicates technologies or services that are present. Further authorized vulnerability assessment would be required to determine whether these components contain exploitable security weaknesses.

- The Nmap scan identified three active hosts within the scanned 256-address range. The host 192.168.201.103 exposed ports 135, 139, 445 and 9999, while 192.168.201.1 exposed port 80.

- These findings represent an increased attack surface but do not by themselves demonstrate successful exploitation.
- 
---
## 6. Recommendations

Based on the observations from the footprinting, reconnaissance and network-scanning activities, I recommend the following security improvements:

- 1. Review Publicly Exposed Technology Information

Organizations should regularly review publicly visible information about their web server, CMS, plugins and JavaScript libraries. Where possible, unnecessary version information should not be exposed.

- 2. Keep Web Technologies Updated

WordPress, WordPress Download Manager, Apache, jQuery and other components should be regularly updated and reviewed against current security advisories.

- 3. Review HTTP Response Headers

HTTP response headers should be reviewed to determine whether unnecessary technical information is being disclosed. Security-related headers should also be configured appropriately.

- 4. Review the WordPress REST API Exposure

The /wp-json/ endpoint should be reviewed to determine what information is publicly accessible and whether unnecessary information is exposed.

- 5. Review DNS Records Regularly

DNS records should be periodically reviewed to ensure that only required records and services are publicly exposed.

- 6. Review DNS Server Configuration

The identified DNS infrastructure and software versions should be reviewed and kept updated. Unnecessary information disclosure should be minimized.

- 7. Properly Configure and Monitor the WAF

ModSecurity should remain enabled and properly configured. WAF rules and logs should be monitored to identify suspicious or repeated requests.

- 8. Review Open Ports on Internal Hosts

The services exposed on 192.168.201.103, particularly ports 135, 139, 445 and 9999, should be reviewed to determine whether they are required.

- 9. Restrict Unnecessary Network Services

Firewalls and access-control mechanisms should be used to restrict services such as SMB-related ports to trusted systems where they are required.

- 10. Perform Regular Internal Network Discovery

Authorized network scans should be performed periodically to identify active devices, newly exposed services and unexpected changes in the network.

- 11. Investigate Unknown Devices

Any unidentified or unauthorized host discovered during network scanning should be investigated and verified.

- 12. Maintain Network Documentation

IP addresses, devices, services and network topology should be documented and regularly updated.

- 13. Perform Further Security Testing with Authorization

Any vulnerability assessment or exploitation attempt should only be performed against systems for which appropriate authorization has been obtained.

---

## 7. Conclusion

- During Week 2 of my Cybersecurity & Ethical Hacking internship, I completed practical activities covering footprinting, reconnaissance and network scanning.

In the footprinting and reconnaissance activity, I used multiple Kali Linux tools to collect information about the networkwalks.com domain. WHOIS provided domain registration information, including the registrar, registration dates and domain status. WhatWeb identified technologies such as Apache, WordPress 7.0.4, WordPress Download Manager 3.3.58 and jQuery 3.7.1.

- Using Nslookup, I resolved networkwalks.com to the IP address 192.232.216.135. Curl was then used to inspect the HTTP response headers and identify additional technical information, including the Apache server and the WordPress REST API endpoint.

- Wafw00f identified ModSecurity (SpiderLabs) as the Web Application Firewall protecting the website. DNSRecon provided additional information about the DNS infrastructure, including SOA, NS, MX, A, TXT and SRV records, as well as DNS server software information.

I also used Maltego to visualize and correlate the relationship between the networkwalks.com domain and publicly available email information, helping me understand how reconnaissance data can be connected and represented graphically.

- For the network-scanning activity, I used Nmap through Zenmap to scan a local network containing 256 IP addresses. The scan identified three active hosts:

- 192.168.201.1
- 192.168.201.100
- 192.168.201.103

- The scan showed that 192.168.201.1 had port 80/tcp open, while 192.168.201.103 had ports 135/tcp, 139/tcp, 445/tcp and 9999/tcp open. The host 192.168.201.100 was identified as active, but all 100 scanned TCP ports were reported as closed.

- Through these activities, I learned how reconnaissance can be used to collect and correlate information about a web application's technologies, DNS infrastructure, server configuration and network environment. I also learned how Maltego can help visualize relationships between different pieces of publicly available information.

The exercises demonstrated the importance of distinguishing between a security observation and a confirmed vulnerability. Identifying a software version, DNS record or open port does not automatically mean that the system is vulnerable. Further authorized testing would be required to validate any potential security weakness.

- Finally, I learned that reconnaissance and network scanning must always be performed within an authorized scope. The activities documented in this report were performed as part of the assigned educational cybersecurity practical.
