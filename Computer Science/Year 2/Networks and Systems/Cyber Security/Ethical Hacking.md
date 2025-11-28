 #nas 

# Ethical Hacking Phases 

1. **Reconnaissance**:
	- surveillance, hacker gathers as much information as possible about system
	- **tools**: Nmap, Whois, Maltego
	- **techniques**: open-source intelligence (OSINT), Google Dorking, Whois Lookup, Social Engineering, Network Scanning
2. **Scanning**
	- identifies open ports, active devices and services on target network
	- **tools**: Nessus, OpenVAS, Angry IP Scanner, nmap, Wireshark
	- **techniques**: Port scanning, vulnerability scanning, network mapping, banner grabbing, ping sweeps
3. **Gaining Access** 
	- hacker uses vulnerabilities to gain unauthorised access to system
	- **tools**: Metasploit, SQLmap, Hydra
	- **techniques**: Password cracking, exploration of vulnerabilities, SQL injection, buffer overflows, XSS, privilege escalation, session hijacking, man-in-the-middle attacks
4. **Maintaining Access** 
	- hacker must maintain foothold in system to perform further actions such as data exfiltration or surveillance
	- **tools**: Netcat, Ngrok, Empire
	- **techniques**: installing backdoors, creating hidden user accounts, SSH tunnelling, Keystroke logging, Trojan horses
5. **Covering Tracks**
	- final phase ensures that hacker's presence remains undetected
	- **tools**: Ccleaner, Stealth Rootkit, Timestomp
	- **techniques**: log tampering, Steganography, file timestamp alteration, clearing command histories, encryption
# Cyber Kill Chain 

1. **Reconnaissance**:
	- scanning environment and/or harvesting information
2. **Weaponisation**:
	- pairing malicious code with exploit to create weapon (malware)
3. **Delivery**:
	- transmission of malware to target
4. **Exploitation**:
	- once delivered, weapon/malware triggered upon action which exploits vulnerability
5. **Installation**:
	- weapon installs malware on system
6. **Command and Control**:
	- command channel for remote manipulation of victim
7. **Action on Objectives**:
	- attacker can achieve objective

