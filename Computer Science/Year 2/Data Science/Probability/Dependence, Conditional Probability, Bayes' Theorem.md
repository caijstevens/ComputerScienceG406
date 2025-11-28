#ds 

# Multiple Events 

Event A has probability $P(A) = \frac{|A|}{|S|}$
- Event B has probability $P(B) = \frac{|B|}{|S|}$
- probability of occurrence of **both** = $P(A\cap B)$
- probability of occurrence of $A$ or $B$ = $P(A\cup B) = P(A) + P(B) - P(A\cap B)$
- probability of occurrence of $A$ while $B$ does not happen = $P(A-B) = P(A\cap\overline{B})$

>[!success] Example 
>In the roll of a die, find probability of having 2 or 5:
>- $A$ = roll the die, get 2
>- $B$ = roll the die, get 5
>$P(A\cup B) = P(A)+P(B)-P(A\cap B)$
>Here, $P(A\cap B) = 0$ because a die roll can only be one number
>$P(A\cup B) = P(A) + P(B) = \frac{1}{6} + \frac{1}{6} = \frac{1}{3}$

### The Relationship of Events 

Events can happen **concurrently**, **after each other** or **because of each other**
- probability of each event can be calculated based on other events

# Conditional Probability 

>[!info] Conditional Probability 
>The probability that event $A$ happens if we already know that event $B$ happens.
>The probability of $A$ given $B$ is $$P(A|B) = \frac{P(A\cap B)}{P(B)}$$

The probability of $A$ and $B$ is: $$P(A\cap B)=P(B)\times P(A|B)$$
- this is the **chain rule**

>[!success] Example 
>A bit string of length 4 is randomly generated. What is the probability that it contains at least 2 consecutive 0s given that its first bit is 0?
>
>$P(\text{two consecutive 0s | first bit is 0}) = P(A|B)\newline$
>$= \frac{P(A\cap B)}{P(B)} = \frac{\frac{5}{16}}{\frac{8}{16}} = \frac{5}{8}$

### Checking for Independence 

If $P(A$ occurs, given that $B$ is true) = $P(A|B) = P(A)$, then $A$ and $B$ are **independent**

# Bayes' Theorem 

Conditional Probability represents probability of an event given a condition
- **Bayes' Theorem** computes probability of a condition, given an outcome.
$$P(A|B) = \frac{P(B|A)\times P(A)}{P(B)}$$
- $P(A)$ is the **prior**, $P(A|B)$ the **posterior**, $P(B|A)$ the **likelihood** and $P(B)$ the **evidence**:
  $$\text{Posterior} = \frac{\text{Likelihood}\times\text{Prior}}{\text{Evidence}}$$
>[!success] Example 
>Box 1 contains 3 red and 2 blue marbles. Box 2 contains 2 red and 8 blue marbles. Fair coin tossed. If heads, marble chosen from Box 1. If tails, marble chosen from Box 2.
>Coin toss result not revealed but marble revealed to be red. What is the probability that Box 1 was chosen?
>
>Let $A$ = chosen marble is red 
>$A_1$ = box 1 (2 blue, 3 red)
>$A_2$ = box 2 (8 blue, 2 red)
>
>$P(A_1|A) = \frac{P(A_1)\times P(A|A_1)}{P(A_1)\times P(A|A_1) + P(A_2)\times P(A|A_2)}$
>$P(A_1|A) = \frac{(\frac{1}{2})\times(\frac{3}{2+3})}{(\frac{1}{2}\times\frac{3}{2+3})+(\frac{1}{2}\times\frac{2}{2+8})} = \frac{3}{4}$

# Tree Diagrams

Tree consists of root, branches and leaf nodes
- branches used for each possible choice
- multiply along branches to get to desired outcome

![[Screenshot 2025-10-10 at 16.16.17.png]]
