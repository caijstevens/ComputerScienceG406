 #nas 

# Data Transformation 

>[!success] Types:
>1. **Encoding**: Data is transformed  from one format to another. Fully reversible, no secrecy.
>2. **Hashing**: Data is transformed into a smaller, fixed size
>3. **Encryption**: Data is transformed using a secret key

Encoding is used to make data more universally readable for many systems (e.g base-64 to base-32, ASCII)

Hashing:
- message $m$ hashed to $h = H(m)$
- $h$ retrieved and check if $h = H(m')$
- scheme is **one-way** if no way to compute $m$ from $h$, **collision resistant** if $H(m)=H(m')$ implies $m=m'$ 

Hashing algorithms:
- **MD5** always outputs 128 bit hash (32 hex string)
- **SHA-3** and SHA-2 (256 bits and 512 bits) are usually considered to be secure

Collisions can occur when different documents have same hash fingerprint
- can be exploited for collision attacks
- can affect HTTPS cert, version control and backups

# Cryptography

Example:
- message $m$ and encryption key $k$
- encrypted message sent is $c=E(m,k)$
- decryption key $k$ used to decrypt message as $m'=D(c,k)$
- scheme valid if $m=m'$, secure if $m'$ can only be obtained from $c$ using $k$

### Caesar Cipher

Alphabet shifted by $k$ number of characters
- e.g VUHUHU with $k=6$ becomes BANANA

### Simple Substitution Cipher

Match alphabet with a complex permutation of itself
- decrypt using **frequency analysis**: each letter always mapped to same

### Navajo Code 

Used during World War II to exchange communications
- Navajo is actual language that very few speak
- alphabet based on first letter of translated word in English
- several words for each letter to make frequency analysis harder![[Screenshot 2025-10-06 at 12.50.50.png]]

### Vigenere Cipher

Solution to break frequency, have sliding password so same letter can be coded differently
- take first letter of text and first letter of password and find matching letter in table
- repeat for second letter, repeat password if needed
- attack: guess key length and try all possibilities with freq analysis

### One Time Pad

Select key as long as message that can be used only once
- requires sync between encryption and decryption
- text converted to binary, XORed with key
- provably secure

### Rail Fence 

Permutation cipher: original letters not changed to others, but just permutated
- easy to implement, easy to break 
![[Screenshot 2025-10-06 at 12.54.30.png]]

