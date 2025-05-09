#cs 

### Microcontroller

**Microcontrollers** are integrated devices consisting of:
- microprocessor (incl. ALU, PC and registers)
- memory (Flash, SRAM)
- input/output 

Used in embedded systems:
- special purpose computer systems designed to perform dedicated functions
- program stored in Flash memory, might never change during microcontroller lifetime.

**Arduino UNO** uses ATmega328P microcontroller:
- Harvard architecture
- 8-bit processor
- 16-bit words

### Registers

32 general purpose 8-bit registers
- also mapped on SRAM memory
- other SRAM memory locations also used as "registers"

**Status register** is 8-bit register, not one of 32 general purpose registers
- 8-bits used as flags, have standard names in AVR assembly documentation![[Screenshot 2025-05-05 at 17.11.37.png]]
- one usage: arithmetic/logic instructions can update status register bits depending on operation result. Then can be used by next instruction.

### Memory

Two main memory spaces (Harvard architecture)
- **Data Memory** (SRAM and EEPROM)
- **Program Memory** (Flash)

**Data Memory (SRAM)**:
- Static Random Access Memory divided into sections used as:
	- mapping space of ALU registers
	- I/O registers (+extended)
	- internal SRAM

**EEPROM Memory**:
- 1kB of EEPROM (**E**lectrically **E**rasable **P**rogrammable **R**ead-**O**nly **M**emory)
- organised as separate space for storing data

### I/O Ports

ATmega328P's I/O pins grouped in three ports:
- **B (digital)**
- **C (analog)**
- **D (digital)**

Direction of each port pin controlled by 8-bit **Data Direction Registers**: DDRB, DDRC and DDRD.
- assembler recognises names
- better to use names than specific memory locations as can affect code compatibility with other microcontrollers.

Setting pin direction (I/O) controlled by single bit:
- bit **set** when 1 - means **OUTPUT**.
- bit **cleared** when 0 - means **INPUT**.
- can control pin direction by manipulating register value with instructions SBI (set bit) and CBI (clear bit):
```
SBI   DDRB,  4    # set PB4 (declare pin PB4 as output)
CBI   DDRD,  2    # clear PD2 (declare pin PD2 as input)
```

Assume pin declared as **input** pin; pin has certain status at given time (incoming signal or not)
- information recorded on corresponding bit of corresponding I/O register - **PINB**, **PINC**, and **PIND**.

Assume pin declared as **output** pin; pin has certain status at given time (outcoming signal or not)
- controlled by corresponding bit of I/O registers **PORTB**, **PORTC** and **PORTD**.
