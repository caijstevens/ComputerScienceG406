#nas 

# Network Security 

Focuses on security of info exchange between entities
- **Confidentiality**: no observer knows exchange content
- **Integrity**: outside modification impossible
- **Availability**: communication always possible 

# TCP/IP Problems 

No confidentiality
- info plain-text by default 
No integrity 
- info can be modified in packets (IP spoofing)
No availability 
- easy to flood network or disrupt packets
- SYN flood attack
![[Screenshot 2025-10-20 at 11.45.31.png]]

# Routing Protocol 

**ARP (Address Resolution Protocol)**
- associates each ethernet address with IP address 
**BGP (Border Gateway Protocol)**
- routing between different autonomous systems 

On the Internet, messages can be intercepted and modified
- routing point broadcasts address request on network if address of destination entity unknown
- easy to spoof addresses

![[Screenshot 2025-10-20 at 11.47.05.png]]
![[Screenshot 2025-10-20 at 11.47.58.png]]
- C is intercepting messages from A

# Key Exchange 

Possible to exchange key without entities meeting or trusting
- Diffie-Hellman Key Exchange 
- Cryptographic scheme 
- instead of padlocks, use exponentiation ($(x^y)^z=(x^z)^y$)

![[Screenshot 2025-10-20 at 11.56.18.png]]
- E intercepts and reads all network content
- E knows A,B and K
- knows {hello world}$_k$
- so can decrypt that, **no confidentiality**

# Man in the Middle Attack 

An attacker intercepts every message between two entities
- victims think they are directly talking together
- avoided by using **explicit identities** that cannot be forged

# Replay Attack 

Happens when adversary can copy and send message to fool recipient, even if contents not readable
- a **nonce** is element which is supposedly unique and randomly generated. Used to defend against replay and MITM attacks

# Needham-Schroeder

Symmetric key protocol
- $A\rightarrow S: A, B, NA$
- $S\rightarrow A: \{NA, K, B, \{K, A\}_{KBS}\}_{KBS}$
- $A\rightarrow B: \{K, A\}_{KBS}$
- $B\rightarrow A: \{NB\}_K$
- $A\rightarrow B: \{NB-1\}_K$

- last two steps are a handshake for B to ensure that A has received key
- vulnerable to replay attack, attacker can replay $\{K, A\}_{KBS}$ if $K$ compromised
- fixed in **kerberos** using timestamps 

# Protocols with Public Keys 

Sometimes agents have public keys
- anyone can encrypt with $KA$ but only $A$ can decrypt

$A\rightarrow B: \{K\}_{KB}$
- to prove to B that it comes from A, A can sign key with key SA: $A\rightarrow B: \{\{K\}_{SA}\}_{KB}$
