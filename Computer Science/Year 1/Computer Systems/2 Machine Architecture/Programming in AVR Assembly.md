#cs 

### C++ Shell

C++ shell file useful when programming in AVR assembly through Arduino IDE
- create separate linked file for assembly code
- in `setup()` function, define I/O
- `loop()` function repeats forever (desirable for embedded system)
```c++
//-----------------------------------  
// C Code: LED blinking  
//-----------------------------------  
extern "C"  
{  
	void start();  
	void btnLED();  
}  
//-----------------------  
void setup()  
{  
	start();  
}  
//-----------------------  
void loop()  
{  
	btnLED();  
}
```

### Directives

Assembly code contains some **directives**.
- do not correspond to assembly instructions
- assembler will take them into account when compiling to machine language
- can be used for defining constants
- makes assembly code easier to develop and maintain
- in AVR assembly, directive preceded by a dot.

$equ$ directive assigns value to label, label can be used in later expressions.
- label assigned value by $equ$ is a constant, cannot be redefined.
- e.g. `equ delayVal, 10000`
- directives $.global \space start$ and $.global\space btnLED$ declare functions start and btnLED as global

### Reading values from Input Pin

```
btnLED:  
	SBIC PIND,  2   ;skip next statement if button not pressed  
	RJMP blink      ;jump to label blink  
	RJMP btnLED     ;return to label btnLED
```
- status of input pin PD4 recorded on register PIND.
- **SBIC** instruction (**s**kip if **b**it in I/O register **i**s **c**leared) checks bit in PIND. If 0 (cleared) skips one instruction.
- if bit cleared, skip blink instruction and go to jump to beginning of function again.
- otherwise, jump to function that blinks LED three times.

### Controlling the Output Pin

```
blink:
	LDI     R21,    3       ;initialise register R21

blinkOnce:
	SBI     PORTB,  4       ;turn ON LED
	RCALL   myDelay         ;call subroutine myDelay
	CBI     PORTB,  4       ;turn OFF LED
	RCALL   myDelay         ;call subroutine myDelay
	SUBI    R21,    1       ;decrement counter by 1
	BRNE    blinkOnce       ;loop if counter not zero
	RJMP    btnLED          ;return to label btnLED
```
- LDI initialises counter R21 to 3, so blinks 3 times.
- PB4 declared as output pin. Behaviour controlled by bit 4 of PORTB
- when value of bit PORTB,4 is 1 (set), signal sent through PB4 and LED is on. When cleared (0), no signal sent, light off.
- value of PORTB,4 controlled with SBI and CBI
- program calls myDelay which does some computations to waste time, otherwise blinking too rapid to see.
- counter decremented with SUBI, subtracts immediate of 1.
- SUBI also checks result and updates status register
- if result = 0, value of Z bit of SR becomes 1 (set).![[Screenshot 2025-05-05 at 18.49.45.png]]
### Conditional Branching

```
blink:
	LDI     R21,    3       ;initialise register R21

blinkOnce:
	SBI     PORTB,  4       ;turn ON LED
	RCALL   myDelay         ;call subroutine myDelay
	CBI     PORTB,  4       ;turn OFF LED
	RCALL   myDelay         ;call subroutine myDelay
	SUBI    R21,    1       ;decrement counter by 1
	BRNE    blinkOnce       ;loop if counter not zero
	RJMP    btnLED          ;return to label btnLED
```

The **BRNE** (branch if not equal) instruction branches to blinkOnce at the top of the loop iff the $Z$ bit of the status counter is 0.
- **does not compare numbers**. Only checks the $Z$ bit in the status register. This represents the result of a comparison done by SUBI.

Finally, RJMP at exit of blink loop, branches back to the btnLED, so the microcontroller waits again for an input signal.

### myDelay Function

```
.equ delayVal, 10000         ;equate delayVal with initial count value
myDelay:  
	 LDI  R20, 100           ;initial count value for outer loop  
outerLoop:  
	 LDI  R30, lo8(delayVal) ;low byte of delayVal in R30  
	 LDI  R31, hi8(delayVal) ;high byte of delayVal in R31  
innerLoop:  
	 SBIW R30, 1             ;subtract 1 from 16-bit value in R31, R30
	 BRNE innerLoop          ;jump if countVal not equal to 0
	  
	 SUBI R20, 1             ;subtract 1 from R20  
	 BRNE outerLoop          ;jump if R20 not equal to 0  
	 RET
```
- two nested loops counting down from 10000 and 100 respectively
- SUBI and SBIW (subtract immediate from word) instructions will be called $10000 \times 100=1000000$ times in total.

Iterations split as $10000\times 100$ instead of $1000^2$.
- this means outerLoop counter can be stored in a word, while innerLoop counter can be stored in a byte.
- assembly programming affords these optimisations.