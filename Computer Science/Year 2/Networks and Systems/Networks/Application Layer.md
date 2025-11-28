 #nas 

# Creating Network User Application 

Write programs that run on different end systems 
- no need to write software for network-core devices 
- can be **client-server** or **peer-to-peer**

### Client-Server 

Client:
- devices requesting info/services
- may be intermittently connected 
- can have dynamic IP
- do not communicate directly with each other 

Server:
- devices responding to request by providing data/services 
- always on
- fixed IP 
- data centres for scaling ![[Screenshot 2025-11-17 at 11.37.03.png]]
### Peer-to-Peer 

**No dedicated server**
- every device can act as both server and client 
- roles set on per request basis 
- intermittently connected and change IPs 

# Processes Communicating 

**Processes** are programs running within host 
- two processes communicate 
- processes on different hosts exchange messages 
- process analogous to house, socket analogous to door 

**Socket** is software mechanism that allows process to:
- create and send messages into network 
- receive messages from network 
- interface between application and transport layers 

# Required Transport Services for Application 

- Reliability 
- Timing (low delay)
- Security 

# Transport-layer Protocol Services 

Services provided by **TCP** protocol:
- **connection-oriented**: setup required between client and server processes 
- **reliable transport** between sending and receiving process 
- **flow control**: sender won't overwhelm receiver 
- **full-duplex connection**: connection can send messages to each other at same time 

Services provided by **UDP** protocol:
- **unreliable data transfer** 
- does not provide reliability/flow control/congestion control/security 
- **short-delay transmissions**

# Application-layer Protocols 

- Types of messages exchanged 
- Message syntax (what fields in messages)
- Message semantics (meaning of info in fields)

Open protocols:
- defined in Request for Comments 
- allow for interoperability (e.g. HTTP, SMTP)

Proprietary protocols:
- skype, zoom etc 

# HTTP Overview 

Application-layer protocol for web services 
- client-server model 
![[Screenshot 2025-11-17 at 11.45.56.png]]

Use TCP at transport layer 
- client initiates TCP connection (creates socket, port 80), server accepts 
- messages exchanged 
- TCP connection closed 
- HTTP is "stateless"
- server maintains no info about past client requests 

**Round trip time (RTT)**: time for small packet to travel from client to server and back

**Non-persistent HTTP**:
- at most one object sent over TCP connection 
- connection then closed 
- multiple object download = multiple connections 
- **response time** = 2RTT + file transmission time 
	- one RTT to initiate TCP connection 
	- one RTT for request and first few bytes of response to return 

**Persistent HTTP**:
- multiple objects sent over single TCP connection 
- connection left open after sending response 
- requests sent once referenced object encountered 
- **response time** = RTT + file transmission time