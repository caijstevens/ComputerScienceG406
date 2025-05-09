#wip #cs 

### Overflow

If an answer doesn't fit in the register:
- triggers overflow error
- should trigger flag in **status register** but can cause errors

### Negative numbers

Signed Magnitude Representation:
- add a single-bit flag: 0 for positive or 1 for negative
- 0000 0110 = 6, 1000 0110 = -6
- has two values for 0: 1000 0000 or 0000 0000
- makes binary arithmetic messy

Ones-complement:
- negative number represented by flipping each bit 
- 0 can be 00000000 or 11111111

Twos-complement
- obtained by flipping each bit and adding 1
- higher order bit still indicates sign of number
- 0 is only 00000000