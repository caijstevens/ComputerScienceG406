#nas 

# SSL/TLS 

A cryptographic protocol between transport and application layers of TCP/IP model
- certificate contains info from entity (incl. identity and public key) signed by known certification authority
- modelled as $CA, \{S,KS\}_{kCA}$

Client ($A$) and server  ($S$) agree on cryptographic preferences ($PA$ and $PS$)
- server sends signed public key, client sends **Pre-Master-Key (PMS)** encrypted by public key
- session key derived from $PMS$ using Pseudo-Random Function ($PRF$)
![[Screenshot 2025-10-20 at 12.35.01.png]]

### Client Authentication 
![[Screenshot 2025-10-20 at 12.35.34.png]]
- by default no authentication, server not sure to talk to $A$

### Attacks 

BEAST
- Browser Exploit Against SSL/TLS

POODLE
- attack leveraging padding in SSL 3.0

HeartBleed:
- buffer over-read attack, allows to get more content than expected
- included session keys, passwords etc
- over 500,000 vulnerable servers

# IPsec

New network layer design for security-ignorant applications 
- symmetric key cryptography and hashing 

**Security Association**: parameters describing parties' preferences and session key

**ISAKMP** (Internet Security Association and Key Management Protocol)
- establishes security association between parties

Headers: **Authentication Header** and **Encapsulating Security Payload**
- AH only provides authentication and integrity
- ESP provides confidentiality and integrity (optional auth)

Header usage modes:
- **Transport**: header introduced between IP and transport headers
- **Tunnel**: header stacked before IP header

# Network Management 

Existing problems despite cryptography:
- denial of service 
- modification of encrypted messages
- capture and brute force of encrypted messages
- inefficiencies in computation and space 

### Firewall

System between two networks, able to block packets
- implements rules describing acceptance/denial 

Reference monitor, therefore should be NEAT
- Non-bypassable (no other connection)
- Evaluable (rules analysed for anomalies)
- Always invoked (never switched off, never ignore connections)
- Tamperproof (rules cannot be modified without authorisation)

**Packet filtering**: decision to accept/deny packets based on packet structure
- used to create virtual networks (no traffic from specific machine to outside)

**Stateful**: current state of connection taken into account
- protect against SYN flood

**Application-aware**: data relevant to application layer taken into account
- filter out specific string e.g code injection or keywords

#### Policy Configuration 

Given packet, firewall checks top rule
- if satisfied, action applied, otherwise move to second rule etc 

**Shadowing**: Rule $R$ shadowed by previous rule $R'$ with different action when $R'$ matches all packets that match $R$

**Correlation**: $R$ and $R'$ correlated if have different actions, and $R$ matches some packets that match $R'$ and vice versa

**Generalisation**: $R$ is generalisation of previous rule if they have different actions, and if first rule can match all packets that match second rule

**Redundancy**: $R$ redundant if rule exists with same action such that if $R$ is removed, policy is same 

#### Limitations

- policy configuration complex, prone to errors
- hard to inspect encrypted content, data can be tunnelled e.g. SSH
- only in/out traffic monitored, vulnerable to insider attacks
- single point of failure 

### Network Intrusion Detection Systems (NIDS)

Monitors network and detects suspicious flows
- **Signature-based**: matches flows with signatures of known attacks
- **Anomaly-based**: NIDS records normal behaviour, detects deviating flows

### Host Intrusion Detection System 

Installed on single machine and analyses logs
- combined with malicious code detection
- can detect insider attacks

HIDS and NIDS complementary, ideal solution uses range of techniques:
- detect malice on single machine, on network, across Networks
- known attacks and abnormal behaviour
- allow correct behaviour, block malicious activity