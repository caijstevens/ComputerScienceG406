 #nas 

# Packet Switching vs Circuit Switching 

### Circuit Switching 

Two network nodes establish **dedicated communication channel** (circuit) before nodes may communicate 
- users remain connected and have full channel bandwidth until session terminated 
- used in traditional phone networks ![[Screenshot 2025-11-10 at 11.25.30.png]]
### Packet Switching 

Two network nodes do **not** establish dedicated communication channel. Transmission links **shared** by multiple users 
- end devices break application data into small pieces for transmissions 
- uses links more efficiently
- different pieces can take different paths
![[Screenshot 2025-11-10 at 11.26.28.png]]

# OSI Reference Model 

**Open Systems Interconnection Model**

| Layer              | Role                                                                        |
| ------------------ | --------------------------------------------------------------------------- |
| Application Layer  | Emails, web browser, file transfer                                          |
| Presentation Layer | Translate data formats, data encryption/decryption                          |
| Session Layer      | Establish/terminate session, sync communication nodes                       |
| Transport Layer    | Support communications between diverse applications across diverse networks |
| Network Layer      | Determine best path through network                                         |
| Data-link Layer    | Define frames, detect and manage collisions, error detection                |
| Physical Layer     | Manage physical media and signal transmissions                              |
Advantages:
- preventing technology/capability changes in layer from affecting other layers 
- provides common language to describe functions and capabilities 
- assists in protocol design 

### Protocol Encapsulation

| Layer              | Contents                                                       | Protocol Data Unit            |
| ------------------ | -------------------------------------------------------------- | ----------------------------- |
| Application Layer  | Data                                                           | data                          |
| Presentation Layer |                                                                |                               |
| Session Layer      |                                                                |                               |
| Transport Layer    | TCP header, Data                                               | segment (TCP), datagram (UDP) |
| Network Layer      | IP header, TCP header, Data                                    | packet                        |
| Data-link Layer    | Ethernet header, IP header, TCP header, Data, Ethernet trailer | frame                         |
| Physical Layer     | Binary                                                         | bit                           |
- reverse for **de-encapsulation**

# TCP/IP Model 

![[Screenshot 2025-11-10 at 11.33.29.png]]

# Network Structure 

**Network edge**:
- end devices: clients, servers
- client: various traditional and modern smart user devices 
- server: in data centre 

**Network core**:
- interconnected routers 
- packets travel between routers across links 
- packet switching allows multiple edges to share core 

# Routing and Forwarding 

**Routing**: routers determine next hop on which to send piece of data
- routing algorithms select best paths for packet movement 
- accounts for delays, error rates, energy use etc
- routers record next hops and associated interfaces ![[Screenshot 2025-11-10 at 11.35.57.png]]
**Forwarding**: intermediary devices move piece of data between interfaces 
- Switch operations:
	- form switching tables based on source MAC address 
	- forward frame: check destination MAC address of frame ![[Screenshot 2025-11-10 at 11.36.46.png]]
- switch checks if source address is in table. If not, add source address and port 
- inspect destination address. If no associated port, forward to all ports 
- only real destination processes packet 

**Store and Forward**: intermediary device keeps info and sends at later time to destination or other intermediary device 
- nodal processing delay (time spent on error checks and determining output link)
- queuing delay (happens at routers)

# Delays 

**Queuing delay**:
- if data input rate exceeds output rate, packets will queue
- can fill buffer/memory and causes packets to be lost
- lost packet can be retransmitted, but not always 

**Transmission delay**:
- time required to push all bits in piece of data onto wire 
- entire data piece must arrive at router before transmission to next link 
- takes $\frac{L}{R}$ seconds to transmit $L$-bit into link at $R$ bps
- end-to-end delay: $2\frac{L}{R}$

**Propagation delay**:
- time required to travel through medium
- for link length $d$ and propagation speed $s$, delay = $\frac{d}{s}$

**Nodal processing delay**:
- checking bit errors and determining output link
- typically $<msec$ 

**TOTAL DELAY**: $$d_P=d_{proc}+d_{queue}+d_{trans}+d_{prop}$$
### Internet Delay/Loss 

**Traceroute program**:
- provides delay measurement along end-end Internet path 
- sends three packets to router $i$ on path
- router $i$ return packets to sender 
- sender calculates time between transmission and reply 