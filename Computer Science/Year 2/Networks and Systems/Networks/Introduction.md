 #nas 

# Computer Network 

A **computer network** is a group of devices that are connected to one another in order to exchange info or share resources 
- **end devices** form interface between users and network
- **intermediary devices** interconnect end devices (switch, router)
- **transmission media** provides channels over which messages travel as signals (copper cables, optic fibres)

### Transmission Media 

**Wired Media**:
- copper cables: coaxial cable, shielded twisted-pair cable, unshielded twisted-pair cable
	- transmit electric signal pulse 
	- transmit rates: up to 10Mbit/s, up to 100Mbit/s, up to 1000Mbit/s
- optic fibres: single mode or multimode
	- transmit light pulses 
	- transmit rate: up to 100Gbit/s
	- low error rate (immune to EM noise)

**Wireless media**:
- radio frequencies
	- signal carried in EM spectrum 
	- no physical wires 
	- environmental effects on propagation (reflection, obstruction, interference)
- satellite radio channels
	- geostationary (~36000km above earth)
	- LEO (closer to earth)

# Networking Protocols 

>[!info] Definition 
>**Network protocols** define the format and order of messages sent and received among network entities, and actions taken on message transmission and receipt

Must have:
- identified sender/receiver 
- common language and grammar 
- speed/timing of delivery 
- confirmation or acknowledgment of requirements 
![[Screenshot 2025-11-10 at 10.59.56.png]]

# Access Networks 

**Digital Subscriber Line**:
- use existing telephone line to central office 
- asymmetric access - upstream/downstream rates different 

**Cable network**:
- HFC: hybrid fiber coax (asymmetric)
- network of cable, fiber attaches homes to ISP router 

**Enterprise access networks - Ethernet**:
- common for companies, universities
- up to 10Gbps 

**Wireless access networks**:
- wireless LANs (home use, up to 1300Mbps)
- wide-area wireless access (up to 10Mbps)

# Network Security 

### Packet Sniffing 

Network interface reads/records all packets passing by
- wireshark is open source packet-sniffer 
