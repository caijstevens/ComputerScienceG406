 #nas 

# Bandwidth 

Two senses of bandwidth:
1. synonymous with bit rate 
2. width of range of frequences 

>[!info] Baseband 
>A range running from 0 to some maximum frequency, typically applicable to wired media.

>[!info] Passband
>Signals occupying range of frequencies, as would pass through corresponding frequency filters

# Digital Signals 

Obtained from analog signal, transmitted by varying some physical property
- 0 or 1 can be many different values in analog 

Digital signals are encoded by low/high voltage. Digital Encoding schemes:
- Non-Return-to-Zero (NRZ)
- Non-Return-to-Zero-Inverted (NRZ-I)
- Bipolar encoding/Alternate Mark Inversion (AMI)
- Manchester encoding

NRZ encoding:
- high voltage is 1, low 0
- voltage does not return to zero, changes only when bit value changes 
- relies on sender and receiver having synced clocks
- transitions used to correct small deviations 
- problem: long runs of consecutive bits, constant signal values cannot sync devices

NRZ-I:
- 0 encoded as no change in level 
- 1 encoded depending on current line state 
	- if CS low voltage, 1 encoded as high voltage 
	- if CS high voltage, 1 encoded low voltage ![[Screenshot 2025-12-23 at 17.04.38.png]]
Bipolar:
- 0 is zero voltage 
- 1 either high or low 
- chosen voltage inverted from last transmission of 1 
![[Screenshot 2025-12-23 at 17.05.20.png]]

Manchester:
- merge explicit clock signal with data signal, use XOR to merge 
- low-to-high: 1, high-to-low: 0
- achieves sync, guaranteed transitions, twice bandwidth of NRZ required 
![[Screenshot 2025-12-23 at 17.06.22.png]]

# Multiplexing 

Frequency Division Multiplexing:
![[Screenshot 2025-12-23 at 17.07.04.png]]

Wavelength Division Multiplexing:
![[Screenshot 2025-12-23 at 17.07.21.png]]

Time Division Multiplexing:
![[Screenshot 2025-12-23 at 17.07.35.png]]

Code Division Multiplexing:
- allows every transmitted to use entire channel all the time 
- transmissions extracted by receiver using coding theory 
- channel merges transmissions 
- each transmitter station has 4-bit chip vector ![[Screenshot 2025-12-23 at 17.08.41.png]]
- chips all orthogonal to each other ($A\cdot B=0$ etc)
- two binary states -1 and +1
- transmit chip sequence to transmit 1, negation to transmit -1 