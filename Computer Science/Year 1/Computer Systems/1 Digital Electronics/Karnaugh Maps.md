#cs 

### Karnaugh Maps

A graphical way of representing equations to make simplification of Boolean expressions easier![[Screenshot 2025-05-04 at 15.36.58.png]]
- each cell represents minterm
- 0 or 1 depending on Y value for that minterm
- looking for terms of form $PA+P\overline{A}$
- represented by neighbouring 1s in K-map.


> [!success] K-map Method
> 1. Create map so that neighbouring terms differ in negation of one variable
> 2. Circle **exactly all ones** using as **few circles** as possible, making each circle as **large** as possible.
> 3. Each circle must span rectangular block that is **power of 2** in each dimension
> 4. Read off circled implicants

- to cross of terms, look for terms whose value changes within the circle

### 7-segment Display Driver
![[Screenshot 2025-05-04 at 16.02.18.png]]
- 4 inputs $D_3,D_2,D_1,D_0$ written $D_{3:0}$
- 7 outputs
- input represents 4-bit binary number

![[Screenshot 2025-05-04 at 16.07.56.png]]
![[Screenshot 2025-05-04 at 16.14.18.png]]
- work out which displayed decimal number each segment is lit up for
- can treat Xs as 1s or 0s depending on what is beneficial for simplifying equation
