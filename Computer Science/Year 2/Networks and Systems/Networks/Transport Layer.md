 #nas 

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

Reliable transfer over reliable channel: rdt1.0
- separate FSMs for sender, receiver  ![[Screenshot 2025-12-22 at 13.57.29.png]]
- set up a sender, implements reliable transfer `rdt_send`, uses unreliable channel `udt_send`
- set up receiver, implements reliable receiver `rdt_rcv`
- for now, do not lose or corrupt packets

Channel with bit errors: rdt2.0
- underlying channel may flip bits in packet, checksum to detect
- **acknowledgements (ACK)**: receiver tells sender that segments received OK
- **NAK**: receiver tells sender that segments had errors 
- sender retransmits segment on receipt of NAK

rdt2.0's fatal flaw = if ACK/NAK corrupted
- sender doesn't know what happened at receiver 
- can't retransmit, possible duplicate

# ARQ (Automatic Repeat reQuest)

Using ACK and NAK is ARQ protocols 
- error detection (sender embeds extra bits in data piece)
- feedback (receiver provides sender with feedback)
- retransmission (sender retransmits erroneous data piece) ![[Screenshot 2025-12-22 at 14.12.48.png]]
Channels with errors and loss: rdt3.0 
- new assumption that underlying channel can also lose packets (data, ACKs)
- checksum, sequence numbers, ACKs, retransmissions not enough 

Approach: sender waits reasonable amount of time for ACK 
- retransmits if no ACK received in this time 
- if packet delayed, not lost:
	- retransmission duplicate but sequence numbers handles this 
	- receiver must specify sequence numbers of packets being ACKd
- requires countdown timer 
![[Screenshot 2025-12-22 at 14.17.57.png]]
![[Screenshot 2025-12-22 at 14.18.11.png]]

# Pipelined Protocols 

![[Screenshot 2025-12-22 at 14.18.48.png]]

Range of sequence numbers must be increased
- can be multiple, in-transit, unackd packets 
- unique sequence number 

Multiple packets buffering at sender\receiver 
- sender buffers packets transmitted but not yet acknowledged 
- receiver buffers correctly received packets before processing to upper layer 
- buffering requirements depend on manner in which data transfer protocol responds to lost, corrupted and overly delayed packets.

**Go-back-N** protocol:
- sender sends multiple packets without waiting for ACK 
- sender can have up to $N$ unpacked packets in pipeline 
- receiver sends cumulative ACKs
- sender has timer for oldest unpacked packet, if expires, retransmit all unpacked packets 
![[Screenshot 2025-12-22 at 14.27.30.png]]

**Selective Repeat** protocol:
- sender can have up to $N$ unpacked packets in pipeline
- receiver sends individual ACK for each packet 
- sender maintains timer for each unpacked packet 
- when timer expires, retransmit only that unpacked packet 
- receiver individually acknowledges all correctly received packets 
- sender only resends packets for which ACK not received 
- sender window of $N$ consecutive sequence numbers 
![[Screenshot 2025-12-22 at 14.28.43.png]]
Sender:
- data from above 
- timeout($n$) means resend segment $n$, restart timer
- ACK($n$) in $[sendbase, sendbase+(N-1)]$:
	- mark segment $n$ as received
	- if $n$ is smallest unACKed segment, advance window base to next unACKed sequence number 

Receiver:
- segment $n$ in $[rcvbase, rcvbase+(N-1)]$:
	- send ACK($n$)
	- out-of-order: buffer 
	- in-order: deliver, advance window to next unreceived packet 
- segment $n$ in $[rcvbase-N, rcvbase-1]$:
	- ACK($n$)
- otherwise ignore