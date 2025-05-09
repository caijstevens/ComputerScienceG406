#ads 

### Hash Tables
A **hash table** consists of a bucket array and a hash function
-  **bucket array**: array A of size N, where each cell is thought as a bucket storing collection of key-value pairs
- the size N of the array is called the **capacity** of the hash table

A **hash function** h is a function mapping each key k to an integer in the range $[0, N-1]$, where N is the capacity of the hash table
- main idea is to use h(k) as index into bucket array.
- store key-value pair (k, v) in the bucket $A[h(k)]$.
- if there are two keys with same hash value h(k), then two different entries mapped to same bucket - **collision** occurs.

hash function is usually specified as composition of two functions
- hash code: keys to integers
- compression function: integers to $[0, N-1]$
- hash code is applied first, compression function applied next on result

goal: scramble keys **uniformly**
- hash function should be efficiently computable
- each table position equally likely for each key
- some compression functions:
	- **division**: take integer mod N
	- **multiply add and divide**: y maps to ay + b mod N where a and b are nonnegative integers

### Collisions
Several ways to deal with collisions.
- good hash function minimises collisions as much as possible
- four notable methods:
	1. separate chaining
	2. linear probing
	3. quadratic probing
	4. double hashing

### Separate Chaining
Each bucket A[i] stores a list holding entries (k, v) such that $h(k) = i$
- cost is proportional to length of list
- average length = N / M (N is amount of data, M is array size)
- worst case: all keys hash to same list

### Linear Probing
If we try to insert entry (k, v) into a bucket that is already occupied, where $i = h(k)$, then we try next at $A[(i+1)\mod N]$.
- if $A[(i+1)\mod N]$ is also occupied, then we try $A[(i+2)\mod N]$, and so on, until we find an empty bucket than can accept the new entry

Costs:
- insert and search cost depend on length of cluster
- average length of cluster is N/M
- worst case: all keys hash to same cluster

### Quadratic Probing
Iteratively tries buckets $A[(i + f(j)) \mod N]$, for $j = 0, 1, 2, ...,$ where $f(j) = j^2$ until finding an empty bucket.
- avoids clustering patterns occurring in linear probing, but creates secondary clustering
- may not find empty bucket even if one exists

### Double Hashing
Choose secondary hash function, $h'$, and if h maps some key k to a bucket $A[i]$ with $i = h(k)$, that is already occupied, then we iteratively try buckets $$A[(i+f(j)) \mod N]; j = 0,1,2,...; f(j) = j \cdot h'(k)$$
common choice of secondary hash function is $h'(k) = q - (k \mod q)$, for some prime number $q < N$
- secondary hash function should not evaluate to 0

### Comparison
Open addressing schemes more memory efficient than separate chaining.

Separate chaining either competitive or faster than other methods in terms of running times.

If memory space not major issue, separate chaining is method of choice.

### Deletions
Deletions from hash table must not hinder future searches
- bucket should not be left unusable
- use **tombstones**: marker left in bucket after deletion
- if tombstone encountered when searching, know to continue
- if tombstone encountered during insertion, should continue probing to avoid duplicates, but then new record can be placed where tombstone was found

Tombstone use lengthens average probe sequence distance. Remedies:
- local reorganisation: after deleting key, follow probe sequence of that key, move records into vacated bucket. (does not work for all collision resolution policies)
- or, periodically rehash table by reinserting all records into new hash table.