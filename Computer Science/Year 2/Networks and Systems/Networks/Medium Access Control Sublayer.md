#nas
# MAC Sublayer Functions

>[!info] MAC Layer 
>Responsible for determining who transmits next, i.e. who gets next access to the channel 

Key issue:
- single physical layer medium for network communications but multiple connected devices 
- all want to use it at once 
- if two nodes transmit at the same time, interference and corruption 

# Static Channel Allocations 

Time Division Multiplexing (TDM)
- each user gets entire transmission capacity for fixed time interval
![[Screenshot 2025-12-22 at 15.09.15.png]]

Frequency Division Multiplexing (FDM)
- each user gets portion of transmission capacity for the whole time 
![[Screenshot 2025-12-22 at 15.09.49.png]]

Static Channel Allocations:
- works only for fixed number of users 
- data traffic often bursty: long time no data, short time high data 
- if many users do not use allocated channel capacity, channels will be idle most of the time

# Dynamic Channel Allocations

Dynamic Channel Allocations:
- no user assigned fixed frequency/time slot 
- all users dynamically assigned frequency/time slot, depending upon user requirements
![[Screenshot 2025-12-22 at 15.18.17.png]]

Random Access Protocols: 
- any station can send data at any time 
- station can make decision on whether or not to send data 
- no scheduled transmission time, can transmit in any order 
- no rule that decides which station should send next 
- if two stations transmit at same time, collision occurs, frames lost 
- e.g. ALOHA, CSMA, CSMA/CD, CSMA/CA

### ALOHA

Pure ALOHA: stations transmit frames whenever they have data to send 
- collision if simultaneous transmission, channel occupation or frame overlap
- collision requires full retransmission 

Slotted ALOHA: time divided to frame-size slots
- station can send frame only at beginning of slot, only one frame per slot 
- if any station not able to place frame onto channel, has to wait to next slot 
- collision if two stations try to send at beginning of same slot 

### CSMA

CSMA (Carrier Sense Multiple Access) designed to minimise collision chances
- station senses carrier or channel before transmission (checks if idle or busy)
- chances of collision reduce greatly if station checks channel before use 
- still chance of collision because of propagation delay 
- CSMA can be greedy, non-persistent or p-persistent 

1-persistent (greedy) CSMA:
- station continuously sense channel status
- if idle, station transmits with probability 1
- if busy, station waits 
- if detects idle channel, immediately transmits frame 
- when collision occurs, the station waits random time and starts again 

Non-persistent CSMA:
- station that has frame to send senses channel 
- if channel idle, sends immediately
- if channel busy, waits random time and senses again
- reduces collision chance because stations wait for random amount of time 
- introduces longer delays 

p-Persistent CSMA:
- used in slotted channels 
- if channel busy, wait until next time slot and start over 
- if idle, transmit with probability $p$ and with probability $(1-p)$ defer until next slot and start over.

CSMA/CD: Carrier Sense Multiple Access with Collision Detection 
- station senses channel while data being transmitted 
- if collision detected, transmission aborted, wait random time to retry
- jam signal sent, alerts other stations, no other stations transmit immediately after 

### CAP

Controlled Access Protocol (CAP): stations consult each other to find which has right to send 
- collision-free 
- cannot send without authorisation
- e.g. bitmap, token passing, binary countdown 

Bitmap: before sending data, all stations state if they have data 
- sent one by one in order 
![[Screenshot 2025-12-23 at 15.08.04.png]]

Token passing:
- tokens sent round ring defines sending order 
- station may send frame before passing token
![[Screenshot 2025-12-23 at 15.08.35.png]]

Binary countdown: improved bitmap
- stations send address in contention slot
- channel ORs bits, give up when send 0 but see 1
- station that sees full address is next to send 
