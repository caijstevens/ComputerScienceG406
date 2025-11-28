#wip #nas 

# Protocols and Services 

Protocols:
- TCP
- UDP 

Services offered:
- **segmentation**
	- send side breaks messages into segments, passes to network layer 
	- receive side reassembles segments into messages, passes to application layer 
- provide logical communications between application processes on different hosts 

Applications on both sides use **port numbers** to set up communication 
![[Screenshot 2025-11-17 at 12.12.54.png]]

Transport layer:
- **port numbers:** logical communication between processes 
- relies on/enhances network layer services 

Network layer: 
- **IP addresses:** logical communication between hosts 

Data-link layer:
- **MAC addresses:** find destination machine

# TCP vs UDP

| TCP                                                                                                            | UDP                                                                                                   |
| -------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| Connection-oriented:<br>- three way handshake before transmission<br>- handshake both sides to terminate       | Connectionless:<br>- data sent directly without any handshakes                                        |
| Reliable transport:<br>- reorder segments<br>- retransmit loss segments <br>- ack and timer                    | Unreliable data transfer:<br>- no datagram reordering<br>- no retransmission to recover loss or error |
| Flow control:<br>- window sizes to control max number of bytes sent in one go<br>- avoid overwhelming receiver | No flow control                                                                                       |
| Full-duplex connection:<br>- connection can send messages to each other at same time                           | Also missing congestion control, security, etc                                                        |
| Segment Structure:<br>![[Screenshot 2025-11-17 at 12.18.21.png]]                                               | Segment Structure:<br>![[Screenshot 2025-11-17 at 12.18.51.png]]                                      |
| Encapsulation:<br>![[Screenshot 2025-11-17 at 12.19.11.png]]                                                   | Encapsulation:<br>![[Screenshot 2025-11-17 at 12.19.31.png]]                                          |

### UDP Application Example 

1. Client reads data from keyboard, sends to server 
2. Server receives data, converts chars to uppercase 
3. Server sends modified data to client 
4. Client receives modified data and displays on screen 
![[Screenshot 2025-11-17 at 12.20.54.png]]
![[Screenshot 2025-11-17 at 12.21.04.png]]

- Sender explicitly attaches IP dest address and port number to each packet 
- receiver extracts 

### TCP Example 

Provides reliable, in-order byte-stream transfer 
1. Server process running, creates socket that accepts connection request 
2. Client contacts server, creates TCP/IP socket, establish connection to server TCP
3. Server TCP creates new socket to communicate with client 

# Multiplexing and Demultiplexing 

When host sends UDP segment:
- all sockets have host-local port number 
- assigned automatically or via `serverSocket.bind((ip,port))`

When host receives UDP segment: 
- checks dest port number in datagram 
- directs UDP datagram to socket with that port number 

# Reliable Data Transfer 

Characteristics of unreliable channel determines complexity of RDT protocol 
![[Screenshot 2025-11-17 at 12.29.19.png]]
- reliable protocol (TCP) may be implemented on unreliable network layer (IP)
- reliable transfer over UDP requires added reliability at application layer and app-specific error recovery 
