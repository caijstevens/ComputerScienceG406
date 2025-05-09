#ads 

### Recursive Algorithms
A **recursive** algorithm is an algorithm that calls itself to do part of its work.
- must have a **base case**
- must **change its state** and move towards the base case
- must **call itself**, recursively

Storing the result of a computation so that it can be subsequently retrieved without repeating the computation is called **memoization**
- hash tables are a good choice of data structure for implementing memoization

### Backtracking
A technique for problems with many **candidate** solutions but too many to try
- general idea: build up solution one step at a time, **backtracking** when unable to continue

Example: Knight's Tour:
- (partial) solution: a list of squares in the order they are visited
- solution valid if no squares visited more than once, and knight has not left chessboard
- complete: if every square visited (64 unique items in list)

