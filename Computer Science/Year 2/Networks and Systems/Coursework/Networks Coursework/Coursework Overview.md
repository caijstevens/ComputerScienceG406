#nas 
# Part 1: Implement an instant messenger (50 marks)  
Note that all code should be written in Python 3.13 and must be stored in files named  
server.py and client.py. 
- All code must run in Windows. Code must be stored in files named server.py and client.py. You must use the “socket” library directly (i.e., not via any other Python module) for network communications.  
- You are required to implement a client-server system, which implements an instant messenger allowing users to chat with each other. Please use TCP to implement 1) and 2). For 3), a client should be able to select protocols (TCP or UDP) to support file downloading. This instant messenger will consist of a client and a server program. You should be able to invoke server and client as follows:  
	- python server.py [port]  
	- python client.py [username] [hostname] [port]  
	- For example, python client.py John 127.0.0.1 12000 would enable a client using the username “John” to connect to 127.0.0.1 (i.e., the local system) via port number 12000.
### 1) The server and clients should implement the following functionality (8 marks):  

- When a Client connects, on the Server, print where the connection is coming from (including the IP address and the port number of the Client).  
- When a Client connects, on the Client, display a simple welcome message from the server. Note that this message must be sent over a network socket and should not be hardcoded on the client side.  
- Allow multiple Clients to connect to the same Server. On each Client, provide an input prompt allowing the Client to send messages.  
- Use the username passed to client.py to print “[username] has joined” on all connected Clients whenever a client connects to the Server.  
- Allow Client to leave the system by implementing a command. Use the username passed to client.py to print “[username] has left” on all other connected Clients.  
- Allow Client to leave the system unexpectedly. Use the username passed to client.py to print “[username] has left” on all other connected Clients.  
- One of the connected clients disconnecting should not cause the server to crash.
### 2) Messaging functions (15 marks):  

- Client should be able to send multiple messages.  
- Client should be able to broadcast messages to all other clients. Broadcast means that a message is sent to all other clients excluding the one that sends the message.  
- Client should be able to unicast messages to another client individually when there are more than two clients in the system. Unicast means to send messages to a single client.  
- Clients can join or leave a named group with commands. If a group does not exist, the attempt to join will create the group. Clients can send a message to all other clients in the group only. This is to develop multicast where a message can be sent to multiple (i.e., within the same group) but not all receivers.  
- Client should be able to change between the above messaging modes

### 3) File downloading functions (20 marks):  

- Server has a “SharedFiles” folder. Clients should be able to access this folder by implementing a command. You may consider using the environment variable SERVER_SHARED_FILES to find this folder. Server replies with a successful access message (including the number of files in the folder) via the connection socket (not hardcoded) that can display on a Client prompt.  
- Once Clients access this “SharedFiles” folder, a list of files in this folder will be displayed on Client prompt.  
- Client can download any files (text, image, audio, video) from the “SharedFiles” folder. Downloaded files should be put in a folder named by the username of Client. (Note that the file itself must be sent over a network socket and should not be hardcoded on the client side.) 
- Client should be able to select protocols (TCP or UDP) to support file downloading. The protocol selection should be on client terminals by implementing a command.  
- Display the size (in bytes) for each downloaded file on Client prompt. Note that this must be sent over a network socket and should not be hardcoded on the client side.  

### 4) Documentation (7 marks):  

Please submit a README.txt file to include clear and easy-to-follow instructions on how to  
implement the above functions with your code.  

Hints for Part 1:  
1. Be sure to build up the functionality of your application step by step, for example, do not attempt to write the entire server before starting the client.  
2. If you are unsure of how to start, I suggest you to have a look at the lab assignments 2 & 3.  
3. I also suggest using a dictionary to store all current connections. Ensure that when a client drops out, that connection is removed from the dictionary.  
4. You may find it useful to look at non-blocking sockets and select(), to ensure that all messages can be received. E.g. (note the format of the if statement):  
```python
r,w,e=select.select([client.connection],[],[client.connection])  
	if client.connection in r: [...] 
```
5. It is ok to send all messages directly as fixed length byte arrays over the sockets.  

# Part 2: Analyse a wired and wireless integrated network (35 marks)  

Refer to the following network scenario.  
A wired and wireless integrated network has the following devices (note that the switch and all  
the devices are cold-started).  
- A wireless access point (denoted as X) with the MAC address XX-XX-XX-XX-XX-XX  
- Two wireless user devices (denoted as A and B respectively) with MAC addresses AA-AA-AA-AA-AA-AA and BB-BB-BB-BB-BB-BB respectively  
- A layer-2 8-port switch (denoted as S)  
- A wired user device (denoted as C) with the MAC address CC-CC-CC-CC-CC-CC  

Assume that, in this network, devices A and B can hear each other’s transmissions and X’s transmissions. X can hear A and B also. The communications between A, B, and X adopt the CSMA/CA scheme without acknowledging whether a frame is received or not. The wireless access point X connects to the switch S via a cable through port 1. The user device C connects to the switch S via a cable through port 8. Suppose:  
- At time 0 μs, C is sending a frame to the switch and the destination is some other wireless node covered by X. Assume it takes 30 μs for C’s frame to arrive at X and then 20 μs from X to the destination.  
- At time 20 μs, a frame becomes available for transmission at A to C. A needs 60 μs to send this frame to X.  
- At time 40 μs, a frame become available for transmission at B to C. B needs 80 μs to send its frame to X.  
- Let the value of the backoff timer for A be 8 μs, the value of the backoff timer for B be 11 μs, and the value of the backoff timer for X be 9 μs. (Suppose these backoff timers are fixed.) DIFS and SIFS are 5 us for A, B, and X.  

Answer the following questions.  
1) Sketch a topology to accurately reflect the connections of the network described above. Your topology should include all devices mentioned and their connections. As for wireless devices, you may use coverage to show connections. You may use tools such as Word, Paint, Visio, etc. to complete this topology. (10 marks)  
2) Which wireless user devices above can receive the frame sent by C? Why? (4 marks)  
3) At what time does A start sending its frame (i.e., putting the frame on the transmission medium) to X? At what time does B start sending its frame to X? At what time does C’s frame arrives at the destination? Explain. (8 marks)  
4) Give the switching table of S at 84 us. Explain. (8 marks)  
5) If you connect a computer to port 2 of S, which frame(s) can you receive from all the above processes? Explain. (5 marks)  
### How to submit?  
You will submit four files:  
- server.py  
- client.py  
- readme.txt  
- a .pdf file. 

In this file, you present your answers for Part 2. A template for the .pdf file is in the “Assignment” folder of the Networks sub-module on Blackboard Ultra. Please compress all files into a single .zip file, and name your .zip file as “YourName_YourID.pdf” (make sure to replace “YourName” with your own name and “YourID” with the ID given to you by the University. For example, JohnDavidson_cgab36.pdf). Please upload your compressed file to Blackboard Ultra for submission.  

The submission deadline is 2pm Thursday January 8th 2026