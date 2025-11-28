#pp 

## 🧾 Overview (Simplified)

**Coursework title:** _Surviving the Storm: Robust Dynamic Memory Allocation on Mars_  
**Due:** **Thursday, 11 December 2025, 14:00**  
**Weight:** 50% of the module mark  
**Workload:** ~20 hours  
**Submission via:** Gradescope  
**Language:** C (only)  
**Allowed AI use:** For **code only**, not for the **report**

You must build a **custom memory allocator** (your own `malloc`/`free` system) that:

- Works within a single given block of memory
    
- Detects and handles memory corruption (bit flips, partial writes)
    
- Fails safely and isolates damaged memory
    

You’ll also write a **short 4-page report** and submit your **C code + Makefile** in a **ZIP** file.

---

## 🧠 Step-by-Step Instructions

### 🧩 Step 1. Understand the Task

You are simulating the Mars rover’s memory allocator.  
You’ll create your own versions of:

`int   mm_init(uint8_t *heap, size_t heap_size); void *mm_malloc(size_t size); void  mm_free(void *ptr); int   mm_read(void *ptr, size_t offset, void *buf, size_t len); int   mm_write(void *ptr, size_t offset, const void *src, size_t len);`

Optional (bonus):

`void *mm_realloc(void *ptr, size_t new_size); void  mm_heap_stats(void);`

Everything must run **only inside the provided heap memory**, not using system malloc/free.

---

### ⚙️ Step 2. Plan Your Allocator

Decide how your memory will be structured:

- **Metadata:** how you store block size, free/used flag, and integrity info (e.g. checksum, canary).
    
- **Error detection:** how to spot corruption or double-free.
    
- **Coalescing:** how to merge adjacent free blocks.
    

Sketch a design diagram by hand for your report (you’ll need to include this).

---

### 💻 Step 3. Implement Your Code

Create these files:

`allocator.h allocator.c runme.c Makefile`

**In allocator.c/h:**  
Implement your allocator functions.

**In runme.c:**

- Allocate a test heap using one `malloc()` or `calloc()` (this is allowed).
    
- Call `mm_init(heap, size)` to set up your allocator.
    
- Run some tests (allocate/free blocks, simulate corruption, print results).
    

**Makefile:**  
Must include at least these targets:

`all: builds allocator.so and runme test: runs your program with sample inputs clean: removes build files`

---

### 🧪 Step 4. Test Your Allocator

Your `runme` program should be simple but effective:

- Try allocating, freeing, reading, and writing data.
    
- Check if corruption is detected (you can simulate bit flips).
    
- Make sure your program doesn’t crash, even under bad conditions.
    

The autograder will later test:

1. **Normal operation** (no corruption)
    
2. **Radiation storms** (random bit flips)
    
3. **Brownouts** (partial metadata updates)
    

---

### 🧰 Step 5. Package Everything for Submission

Submit **ONE ZIP file** containing (no folders):

`allocator.c allocator.h runme.c Makefile report.pdf`

✅ The Makefile must build everything with:

`make all`

✅ The executable must be called exactly:

`runme`

---

### 📝 Step 6. Write Your 4-Page Report (PDF only)

Follow the structure provided (1 page per section, ~250 words each):

1. **Summary of Approach & Solution Design**
    
    - Describe how your allocator works.
        
    - Include your **hand-drawn** diagram.
        
    - Mention key design decisions and why.
        
2. **Analysis of Solution**
    
    - Evaluate performance (speed vs memory efficiency).
        
    - Discuss trade-offs and limitations.
        
3. **Use of Generative AI / Tools**
    
    - Explain how you used AI, compilers, or testing tools.
        
    - Be honest — this section is required.
        
4. **Additional Functionality (Optional, for extra credit)**
    
    - Describe any extra features (e.g. `mm_realloc`, thread safety).
        
    - Include another hand-drawn diagram if relevant.
        

🖊️ _Tips:_

- Use minimum font size 10.
    
- Don’t change layout.
    
- Only **hand-drawn** figures — computer-drawn ones get ignored.
    

---

### 🎯 Step 7. Check the Marking Criteria

|Category|Marks|
|---|---|
|Correctness of solution|10%|
|Fault resilience (storm tests)|20%|
|Code quality & documentation|15%|
|Error handling|10%|
|Report (design, analysis, diagrams, AI use)|35%|
|Additional functionality (bonus)|up to +20%|

---

### 🚀 Step 8. Final Checks Before Submission

- ✅ All files compile with `make all`
    
- ✅ Executable name is `runme`
    
- ✅ No subfolders inside ZIP
    
- ✅ Report is **PDF**, not Word
    
- ✅ Test your program on **Linux (Ubuntu 22.04)** or the **Mira** system
    
- ✅ Submit before **11 Dec 2025, 14:00**