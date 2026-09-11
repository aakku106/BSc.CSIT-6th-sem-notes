---
{"dg-publish":true,"permalink":"/cdc/old-sets/model-i/","noteIcon":"","dg-note-properties":{"Subject":"[[CDC]]"}}
---


# CDC Model I

## Section A

**Attempt any TWO questions.**

1. What is ambiguous grammar? Explain the “Dangling Else” problem with example. Show how to resolve it.

   Construct the LL(1) parsing table for the following grammar (after removing left recursion if needed):

   E → E + T | T

   T → T \* F | F

   F → (E) | id

   Parse the string **id + id \* id** using this table.

2. What is backpatching? Why is it used in code generation? Generate three-address code with backpatching for the following code:

   while (a < b) {

       if (c < d)

           x = y + z;

       else

           x = y – z;

   }

   Also show the quadruples and explain how backpatch function works.

3. Convert the following regular expression to NFA using Thompson’s construction:

   (a|b)\*a(a|b)

   Then convert this NFA to DFA using subset construction method. Finally, minimize the DFA using state minimization algorithm.

## Section B

**Attempt any EIGHT questions.**

1. What is recursive descent parsing? Write a recursive descent parser for the following grammar:

   S → aS | bA

   A → bA | c

   Show how it parses the string “aabc”.

2. Given the following DFA with states {A, B, C, D, E, F}, minimize it using state minimization algorithm:

   Start state: A

   Final states: {D, F}

   Transitions:

   δ(A, 0) = B, δ(A, 1) = C

   δ(B, 0) = D, δ(B, 1) = E

   δ(C, 0) = E, δ(C, 1) = D

   δ(D, 0) = D, δ(D, 1) = D

   δ(E, 0) = F, δ(E, 1) = F

   δ(F, 0) = F, δ(F, 1) = F

   Show all steps clearly including partition refinement.

3. Compute FIRST and FOLLOW for all non-terminals in the grammar:

   S → ACB | CbB | Ba

   A → da | BC

   B → g | ε

   C → h | ε

   Construct the LL(1) parsing table. Is this grammar LL(1)? Justify your answer.

4. What are handles in LR parsing? Explain handle pruning with example. For the grammar:

   E → E + T | T

   T → T \* F | F

   F → (E) | id

   Show the handle at each step for reducing the string: **id + id \* id**

5. What is intermediate code? Explain the advantages of three-address code. Generate three-address code, quadruples, triples, and indirect triples for:

   a = b \* (-c) + d / e

6. Write syntax-directed definitions for translating boolean expressions into three-address code using backpatching. Generate code for:

   if (a < b && c > d || e == f)

       x = 1;

   else

       x = 0;

7. Explain the following code optimization techniques with examples:
    1. a) Copy propagation  
       b) Constant folding  
       c) Dead code elimination  
       d) Strength reduction

    Apply all applicable optimizations to:

    x = 3;

    y = x;

    z = x + 5;

    a = y \* 2;

    b = 8;

    c = b / 2;

    d = a + 0;

8. What is register allocation? Explain register allocation using graph coloring algorithm. Given the following live ranges, perform register allocation with 3 registers available:

    Variables: a, b, c, d, e

    Live ranges overlap:

    – a and b overlap

    – b and c overlap

    – c and d overlap

    – d and e overlap

    – a and c don’t overlap

    – b and e overlap

    Draw the interference graph and assign registers.

9. Write short notes on:

    a) Error recovery in parsing (panic mode, phrase-level recovery)  
    b) Parameter passing mechanisms (call by value, call by reference, call by name)
