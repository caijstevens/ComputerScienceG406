#nas 

# Frames 

Sender Side:
- DLL accepts packets from Network Layer, encapsulates into frames 
- frames sent to Physical Layer 
- Physical Layer responsible for transmission of raw bit sequences 

Receiver Side:
- DLL accepts bits from Physical Layer to form frames 
- frames sent to Network Layer 
- Network Layer de-encapsulates frames to obtain packets 
![[Screenshot 2025-12-23 at 15.27.32.png]]

Framing methods:
- byte count 
- flag bytes with byte stuffing 
- flag bits with bit stuffing 

# Framing: Byte Count 

Frame begins with count of number of bytes in it.
- simple but difficult to resynchronise after error 
![[Screenshot 2025-12-23 at 15.35.24.png]]

Framing header and trailer:
- can contain data length and extra data for error checking 

# Framing: Byte Stuffing 

Flag bytes delimit frames 
- occurrences of flags in data must be stuffed/escaped
- longer, but easy to resynchronise after error 
![[Screenshot 2025-12-23 at 15.42.52.png]]

# Framing: Bit Stuffing 

Flag has 111111
- within data, 0 stuffed after each 5 consecutive 1s to void instances of flag in data ![[Screenshot 2025-12-23 at 15.47.04.png]]
# Error Detection and Correction (EDC)

Errors occur during frame transmission 
- Error correction: include enough redundant info to help receivers deduce correct data 
- Error detection: include enough info to deduce that error occurred
![[Screenshot 2025-12-23 at 15.48.07.png]]

Codewords: frame consists of $m$ data bits and $r$ redundant check bits 
- $n$-bit codewords with $n=m+r$
- hamming distance between two codewords is number of bit positions in which two codewords differ 
![[Screenshot 2025-12-23 at 15.50.08.png]]

Hamming code gives way to add check bits and correct up to single bit error 
- encoding: number data bits starting from one and skipping powers of two, powers of two reserved for parity bits 
- decoding: calculate all parities, if error add up positions of incorrect ones to find position of error 
![[Screenshot 2025-12-23 at 15.53.49.png]]
![[Screenshot 2025-12-23 at 15.54.01.png]]
![[Screenshot 2025-12-23 at 15.54.12.png]]

# Error Detection: Parity

Mod 2 sum of data bits
- equivalent to XOR, detection checks if sum wrong
- used to detect error by appending parity bit to data 

# Error Detection: Checksum 

Sender: 
- data divided into $k$ segments each of $m$ bits and summed 
- 1s complement of sum forms checksum 
- checksum segment sent along with data segments 

Receiver:
- all received segments added 
- sum complemented 
- if result zero, received data is OK

# Error Detection: CRC 

Cyclic Redundancy Check: more advanced, uses manipulations with polynomials 
- let $M_1$ be message of $n$-bits, padded with CRC code and sent 
- CRC generated using given polynomial $P_1$ agreed between sender and receiver 
- receiver gets $M_1+CRC$ and extracts $M_1$ using $P_1$
![[Screenshot 2025-12-23 at 15.58.38.png]]

![[Screenshot 2025-12-23 at 15.58.53.png]]
![[Screenshot 2025-12-23 at 15.59.02.png]]
