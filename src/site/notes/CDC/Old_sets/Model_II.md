---
{"dg-publish":true,"permalink":"/cdc/old-sets/model-ii/","dg-note-properties":{"Subject":"[[CDC]]"}}
---


# CDC Model II

## Section A

**Attempt any TWO questions.**

1. What is the difference between LR(0), SLR(1), and LR(1) parsing? Explain with examples when each would fail or succeed.

   Compute the LR(1) items and construct the LR(1) parsing table for:

   S’ → S

   S → AA

   A → aA | b

   Show the parsing actions for the input string “aab”.

2. Explain the role of lexical analyzer in compiler design. What is input buffering? Describe the buffer-pair scheme with sentinels and explain why it is efficient.

   Design a lexical analyzer using transition diagram that recognizes:
   - Identifiers (letter followed by letters/digits)
   - Integer constants
   - Operators: +, -, \*, /, <, <=, >, >=, = =, =
   - Keywords: if, then, else, while

   Show the transition diagram and write pseudocode for the nextToken() function.

3. What is L-attributed definition? Differentiate between S-attributed and L-attributed definitions with examples.

   Write an L-attributed syntax-directed definition for the following grammar that builds a syntax tree:

   E → E₁ + T

   E → T

   T → T₁ \* F

   T → F

   F → (E)

   F → id

   Draw the annotated parse tree showing all attribute values for the input: **id₁ + id₂ \* id₃**

## Section B

**Attempt any EIGHT questions.**

1. Draw the detailed block diagram of a compiler showing all phases with inputs and outputs of each phase. Explain how symbol table and error handler interact with different phases of compilation.

2. What is a macro? Differentiate between macro and procedure. Explain macro expansion with example.

   Show the complete macro expansion for:

   #define SQUARE(x) ((x) \* (x))

   #define MAX(a, b) ((a) > (b) ? (a) : (b))

   #define CUBE(x) (SQUARE(x) \* (x))

   result = MAX(SQUARE(3), CUBE(2));

3. What are closure and goto operations in LR parsing? Compute the closure of the following LR(0) item set:

   I₀ = {[S’ → •S, $]}

   Grammar:

   S → AB

   A → aA | b

   B → c

   Then compute GOTO(I₀, a) showing all steps.

4. Construct the operator-precedence relations (⋖, ≐, ⋗) for the following grammar:

   E → E + T | T

   T → T \* F | F

   F → (E) | idBuild the complete operator-precedence table. Parse the string **id + id \* id** using this table showing all stack operations.

5. What is a symbol table? Compare different data structures for implementing symbol table:
   - Linear list
   - Hash table
   - Binary search tree

   Which is most efficient and why?

   Show hash table implementation for storing the following identifiers using hash function h(x) = (sum of ASCII values) mod 7:

   Identifiers: {sum, count, avg, total, temp}

   Use chaining for collision resolution.

6. Draw and explain the complete structure of an activation record with all components (return value, actual parameters, control link, access link, saved machine status, local data, temporaries).

   Show the activation tree and activation record contents for the following code at the point when factorial(1) is executing:

   int factorial(int n) {

       if (n <= 1)

           return 1;

       return n \* factorial(n-1);

   }

   int main() {

       int x = factorial(3);

   }

7. What is peephole optimization? Explain the following peephole optimization techniques with examples:
    - Redundant load/store elimination
    - Constant folding
    - Strength reduction
    - Use of machine idioms

    Apply these optimizations to the following assembly code:

    MOV R0, a

    MOV b, R0

    MOV R0, b

    ADD R0, R0, #0

    MUL R0, R0, #2

    MOV R1, #10

    ADD R1, R1, #5

    MOV R2, #0

    ADD R2, R2, R1

8. Construct the flow graph for the following code and identify all basic blocks:
    1. read x
    2. i = 1
    3. sum = 0
    4. prod = 1
    5. if i > x goto 13
    6. square = i \* i
    7. sum = sum + square
    8. prod = prod \* i
    9. i = i + 1
    10. if i <= x goto 6
    11. write sum
    12. write prod
    13. halt

    Identify loop invariant code that can be moved out of the loop, if any.

9. Write short notes on:

    a) Type checking: Static vs Dynamic type checking with examples  
    b) Synthesized vs Inherited attributes with expression evaluation example
