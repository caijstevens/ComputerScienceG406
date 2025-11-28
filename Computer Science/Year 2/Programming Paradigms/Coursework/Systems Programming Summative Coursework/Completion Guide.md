#pp  

# 1: Plan Allocator  

1. ✅ Understand format of memory blocks:
	- each block looks like [Header | Payload | Footer]
2. ✅ Choose Data Structures:
	- decide how to keep track of free/used blocks
	- decide how to store integrity info (canaries, checksums, duplicates)
3. ⏰ Choose Allocation Policy: 
	- decide how allocator picks free block (first/best/next fit)
4. ✅ Quarantine Plan for corrupted blocks (mark and don't allocate again)
5. ⏰ Sketch how blocks are laid out and labelled 

# 2: Implement Allocator in C

1. ✅ Create `allocator.h`
	- define public interface:![[Screenshot 2025-11-05 at 17.42.45.png]]
	- include essential headers 
2. ⏰ Create `allocator.c`
	- implement all the logic, function breakdowns:
	- `mm_init`:
		- Receives a pointer to the start of the heap (from `runme`).
		- Sets up internal data (initial free block).
		- Checks for the 5-byte unused pattern and resets if needed.
		- Returns 0 on success.
	- **`mm_malloc`**
	    - Search for a free block that fits the size (respect 40-byte alignment).
		- Split block if necessary.
		- Write metadata (header/footer) and return pointer to payload.
		- Return NULL if no space or corruption detected.
	- **`mm_free`**
	    - Mark the block as free.
	    - Detect double-free (maybe via flags or checksum).
	    - Coalesce adjacent free blocks.
	- **`mm_read` / `mm_write`**
		- Read/write safely to payload.
		- Return -1 if pointer invalid or block corrupted.
	- **Error handling:** add integrity checks whenever reading metadata 
3. ⏰ `runme.c`
	- Test driver, must do following:
		- allocate heap![[Screenshot 2025-11-05 at 17.47.02.png]]
		- call allocator functions to test behaviour ![[Screenshot 2025-11-05 at 17.47.15.png]]
		- optionally simulate corruption ![[Screenshot 2025-11-05 at 17.47.24.png]]
		- print readable messages about success/failure 
	- use command line args![[Screenshot 2025-11-05 at 17.47.33.png]]
4. ⏰ Makefile:
	- should compile everything with `make all`
	- include following:![[Screenshot 2025-11-05 at 17.48.29.png]]
# 3: Test Code 

1. ⏰ Basic Tests:
	- allocate and free small and large blocks 
	- ensure coalescing works 
	- check alignment (40-byte)
2. ⏰ Fault injection tests:
	- manually flip bit in heap, make sure corruption detected 
	- ensure no crashes occur 
	- ensure damaged blocks quarantined 
3. ⏰ Brownout simulation:
	- interrupt metadata updates mid-operation 
	- ensure allocator detects and prevents reuse of corrupted blocks
4. ⏰ Print clean messages:![[Screenshot 2025-11-05 at 17.51.11.png]]
# 4: Package For Submission

1. ⏰ Place following files in one folder:
	- allocator.c
	- allocator.h
	- runme.c
	- Makefile 
# 5: Write Report 

1. ⏰ Summary of Approach and Solution Design:
	- explain allocator structure and logic 
	- describe metadata layout and corruption detection 
	- reference specific code sections 
	- include hand-drawn diagram 
2. ⏰ Analysis of Solution 
	- compare performance vs memory efficiency 
	- mention trade-offs 
	- include table or simple graph 
3. ⏰ Use of Generative AI or Tools 
	- explain what AI/code tools you used 
	- say how they helped or limited 
	- must be honest/specific 
4. ⏰ Additional Functionality 
	- describe advanced features (multi-thread safety etc)
	- add hand-drawn diagram (MUST BE HAND-DRAWN)
![[Screenshot 2025-11-05 at 17.56.48.png]]

# 6: Check and Submit 

1. ⏰ Check following:
	- make all builds successfully 
	- runme runs correctly on linux 
	- output clean and readable 
	- report.pdf is formatted correctly 
	- all files (+ REPORT) in root of zip 
2. ⏰ Submit! 