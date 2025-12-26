# General Functionality 
- [ ] When client connects, server should print where connection is coming from (include client IP and port number)
- [ ] When client connects, display welcome message on client side. Message must be sent over socket from server.
- [ ] Allow multiple clients to connect to the same server. On each client, provide input prompt allowing client to send message.
- [ ] Use username passed to client.py to print "[username] has joined" on all connected clients 
- [ ] Allow client to leave system, print "[username] has left" on all other clients 
- [ ] Allow client to leave unexpectedly. Print as above.
- [ ] Disconnect should not cause server to crash.

# Messaging Functions 
- [ ] Client should be able to send multiple messages.
- [ ] Client should be able to broadcast messages to all other clients.
- [ ] Client should be able to unicast messages to another client individually when there are more than two clients in the system.
- [ ] Clients can join or leave named group with commands. If group does not exist, join attempt creates group. Clients can send message to other clients in group only.
- [ ] Client should be able to change between above messaging modes.

