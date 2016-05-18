# Programmierparadigmen

<!-- toc -->

## Introduction

### Reasons for Studying Comcept of Programming Lanugages

> If all you have is a hammer, everything looks like a nail

### Implementation Methods

### Compilation, Interpretation, Hybrid implementation Systems

![enter image description here](https://lh3.googleusercontent.com/-P7aEvrWiQ60/Vzi5V39JIGI/AAAAAAAAO_Q/TZqph8p8pa8u51_u_jojzm7JOqFlDkqEwCLcB/s0/Auswahl_026.png "Auswahl_026.png")


## Programming Paradigms

### Imperative Programming

* Programming by changing states in memory through assignments
* Step-by-step processing
* Machine oriented data and program structures based on von Neumann computer architecture

![enter image description here](https://lh3.googleusercontent.com/-Twn4QGfU3kY/Vzi6A3gR-LI/AAAAAAAAO_Y/DdNtMs1GPksZNEsexHtPPDFI_RJJz_J6wCLcB/s0/Auswahl_027.png "Auswahl_027.png")

### Functional Programming

* Functions as "first-class objects"
* Functions as parameters 
* Higher-order functions
* Compositional model of function construction
  * New functions are built by combining existing ones
* Referential transparency
  * The value of a closed expression does not depend on where / when it appears

### Object-oriented Programming

* Abstract data types ("classes")
  * Encapsulation
  * Information hiding (access controll)
* Inheritance
* Polymorphism

### Declarative Programming

* Programmers specify the conditions a solution has to fulfill
* Calculation is task of machine
* No priori distinction between input and output parameters (relations approache)
* Programm execution as proof or derivation: Statements are verified / falsified
* Includes functional and logical programming 

### Logical Programming

* Based on Formal logic (Resolution calculus of First Order Predicate logic)
* Programms are sets of axioms (facts and rules)
* Programmer can ask questions by providing a goal
* The Interpreter tries to infer the goal based on axioms

![enter image description here](https://lh3.googleusercontent.com/-JhdPRlC3I5c/Vzi_1DT7K3I/AAAAAAAAO_4/bGdZ7MJ_66AR2Z5qRv1mRJ4o8E2yzH3_ACLcB/s0/Auswahl_028.png "Auswahl_028.png")


## Syntax and Semantics

### Syntax: Structure of the language

* Alphabet / Character set
* Basic elements
* Structurally well-formed programs

### Semantics: Meaning of programs

* Meaning in the sense of the programmer
* Results of the evaluation on a machine (operational semantics)
* Type restrictions and special constraints (division by zero)
* Design by contract

### Lexemes and tokens

Lexemes: Lowest level syntactic units
Tokens: categories of lexemes

![enter image description here](https://lh3.googleusercontent.com/-YSm8rcSTzsw/VzjBX8kNXnI/AAAAAAAAPAI/VED4zwfn76kYkFnuN4DtWDg__aixOursACLcB/s0/Auswahl_029.png "Auswahl_029.png")


### Definition of Syntax through a Grammar

![enter image description here](https://lh3.googleusercontent.com/-E5UnCpn7uUc/VzjBwWLnyJI/AAAAAAAAPAQ/_eCBW3nhdqYdn6F9bARyru8pwYFPLweZgCLcB/s0/Auswahl_030.png "Auswahl_030.png")

### BNF

> Formal grammars, in which the head of all producation rules contains only one nonterminal

* Introduced for describing ALGOL 58
* Modified by Peter Naur for ALGOL 60

![enter image description here](https://lh3.googleusercontent.com/-P_ONubvHP7Q/VzjC-mVdQDI/AAAAAAAAPAk/UYtjoB3YD6Ue2vp-BLfz2YNotBk-fEmOgCLcB/s0/Auswahl_031.png "Auswahl_031.png")

### Syntax Diagrams

![enter image description here](https://lh3.googleusercontent.com/-TZfApyY4clo/VzjDQFFiaYI/AAAAAAAAPAw/gFiAMopekAosufuBzKhiFC5TetmLg1XJgCLcB/s0/Auswahl_032.png "Auswahl_032.png")


### Language Recognition vs. Generation

![enter image description here](https://lh3.googleusercontent.com/-lBXhbW3jTi0/VzjDvHSKjYI/AAAAAAAAPA4/hLOkb8u_TgM_M7E2YcSL0FtJv589jqUQQCLcB/s0/Auswahl_033.png "Auswahl_033.png")

### Conditional Statements ((Un)Ambigios grammar)

![enter image description here](https://lh3.googleusercontent.com/-mN3WOceMdYc/VzjKyi9DTZI/AAAAAAAAPBs/k2mYEwtnn2sdE3lTcSh8iVERtuHYqGzGwCLcB/s0/Auswahl_034.png "Auswahl_034.png")

![enter image description here](https://lh3.googleusercontent.com/-uFgjfrx_v0c/VzjK9IOpILI/AAAAAAAAPB0/LRHnbWXCU-0d3v-lp47xjxAA6iyV-2GhwCLcB/s0/Auswahl_035.png "Auswahl_035.png")

![enter image description here](https://lh3.googleusercontent.com/-4YgEKu2vKPQ/VzjLJX6Pq7I/AAAAAAAAPB8/LY38Oqa904w7pk22rJwf1C1Srrs27FRnACLcB/s0/Auswahl_036.png "Auswahl_036.png")

## Extended Backus-Naur Form (EBNF)

* No Enhancement of descriptive power of BNF
* Increases readability and writeability
* Various verions of EBNF

![enter image description here](https://lh3.googleusercontent.com/-olWNo8L3KuA/VzjLhVXXWJI/AAAAAAAAPCI/IDecKpyIPZgIW0ZfXdMQKqxjT5tA_a-jACLcB/s0/Auswahl_037.png "Auswahl_037.png")

## Attribute Grammars

![enter image description here](https://lh3.googleusercontent.com/-IJqTGrjfzZA/VzjPHS0_C9I/AAAAAAAAPCo/GA5nqNsY_v8UxFwOrj6EWJD1meMvfN1fACLcB/s0/Auswahl_038.png "Auswahl_038.png")

* Relation between attributes through rules
* RuleSet defines agreement 
* Context-Free grammars
* Ingredients
  * Attributes (Terminals and Non-Terminals)
  * Semantic Functions
    * specify how attribute values are computed
    * associated with grammar rules
  * Predicate functions
    * state static semantic rules of language
    * associated with grammar rules
* For each grammar symbol **x** there is a set **A(x)** of attributes
* **A(x)** consists of two disjoint sets **S(x)** (synthesized) and **I(x)** (inherited)  
* Synthesized attributes pass semantic information **up** a parse tree
* Inherited attributes pass semantic information **down**  and **across** a parse tree

![enter image description here](https://lh3.googleusercontent.com/-4E7VAw-KDEQ/VzjRGvWfRmI/AAAAAAAAPDI/PXzPraZdF7oJNuwmwSqIw57v5NDHXNXvwCLcB/s0/Auswahl_039.png "Auswahl_039.png")

![enter image description here](https://lh3.googleusercontent.com/-RVZGVRsN8D8/VzjRZM0kXMI/AAAAAAAAPDQ/P0LT_N9FGv4LYTSM7PZ4pvmjiFrTEwN0ACLcB/s0/Auswahl_040.png "Auswahl_040.png")

![enter image description here](https://lh3.googleusercontent.com/-wX6M0AoGH7o/VzjRqPTi2FI/AAAAAAAAPDc/TcjuepLjz-klniJEpxHKroEmVIZW3X5gACLcB/s0/Auswahl_041.png "Auswahl_041.png")

![enter image description here](https://lh3.googleusercontent.com/-1evWliRUtjc/VzjRxqVf-5I/AAAAAAAAPDk/oyToR57ww_4tBXX02FtLYbmWLU2EWlj1wCLcB/s0/Auswahl_042.png "Auswahl_042.png")

![enter image description here](https://lh3.googleusercontent.com/-UepSlztzPgA/VzjR5f6gJCI/AAAAAAAAPDs/xrDH0Uxy-UM5UPZjPd-GRadUzC8DeOkuQCLcB/s0/Auswahl_043.png "Auswahl_043.png")

## Axiomatic Semantics

* Based on mathematical logic (predicate calculus)
* {Precondition **P**} Statement-(Sequence) **S** {Postcondition **Q**}

**Hoare Logic**:

> If the assertion (logical expressions / predicates) P is true before the execution of the statement /statement sequence S, the assertion Q will hold after successfull completion.

![enter image description here](https://lh3.googleusercontent.com/-CtN6OuS5RLA/VzrPTIdOF9I/AAAAAAAAPFw/ifGhBsmR-qMldf80pCAIc1nju0S_TqW1QCLcB/s0/Auswahl_044.png "Auswahl_044.png")

**QUIZ**
![enter image description here](https://lh3.googleusercontent.com/-Cb6xFTM2z94/VzrPo2hVJnI/AAAAAAAAPF4/c-MOGtZv8fsF9pSrmUkRqVmRbOeLHkqBwCLcB/s0/Auswahl_045.png "Auswahl_045.png")

TODO

## Functional Programming

* Based on mathematical functions
* Evaluation order of functions controlled by recursion and conditional expressions
* No side effects
  * Functions only return values without changing state
  * Result of a function call does only depend on the given input not on the calling context
  * No operations that would change values of variables in a given context  &#8594; No distinction between variables and constants
  * **No variables**

### Lambda Calculus

* Goal: Seperating definition and naming of a function
* Lambda Expressions (**Anonymous functions**)
  * Nameless functions
  * Specify parameters and mapping of functions
 
### Higher-Order Functions

* Takes functions as parameters, yield a function as result or both
* Function composition

### Haskell

![enter image description here](https://lh3.googleusercontent.com/-uRFHN8Yw8VE/VzrUgwjCfOI/AAAAAAAAPGU/M1BftE0ec9gPf0G5l150OTI0LuZGHXwGQCLcB/s0/Auswahl_046.png "Auswahl_046.png")

* No side effects
* Higher order functions
* Non strict semantics / lazy evaluation
* Strong static typing
* Pattern matching
* List comprehension
* Type classes
* Type polymorphism
* Monads

![enter image description here](https://lh3.googleusercontent.com/-QCrP7JoDxl8/VzrVkXuI7bI/AAAAAAAAPGk/udAhk7afRcsw-ABiRONwE8TyOLki7g0bACLcB/s0/Auswahl_047.png "Auswahl_047.png")







> Written with [StackEdit](https://stackedit.io/).