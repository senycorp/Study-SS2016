# Programmieren in C / C++
----------------------------

## What is a Von Neumann Language?

A Von Neumann Language is a conceptual guideline for application execution. It defines all given hardware parts and their purpose while execution. These languages puts every single step of a programm into the RAM (STACK). To guarantee a managed execution the actual address of running command and the next one is saved in special registers in CPU (Program/Instruction Counter). The Von Neumann Cycle defines the following steps:

1. FETCH: Command will be loaded from RAM based on the address saved in Instruction Counter
2. DECODE: Control Unit decodes command into simple instructions executable by the CPU
3. FETCH OPERANDS: Needed Operands or Parameters will be fetched out from the RAM
4. EXECUTE: Arithmetical or logical command execution based on fetched operands (Jump instructions change the Instruction Counter)
5. WRITE BACK: If necessary, the results of the execution will be transfered into RAM or Register

## What are the differences between *Operators* and *Control Structures* in *Von Neumann Language*?

Operators are simple instructions which do not change the flow of a program by manipulating the Instruction Counter but can do memory transformations. Control Structures instead are designed to manipulate the execution of a program by given conditions. Therefor they can change the Instruction Counter.

## What does a *Language Runtime* do?

A **Language Runtime** is the plattform on which programs written in these languages can run. The runtime can perform runtime checks, manages error handling and do some memory management.

## What are the differences between *HEAP* and a *Stack* in the memory managament of programs?

**[See here...](http://stackoverflow.com/questions/79923/what-and-where-are-the-stack-and-heap)**
![](Auswahl_078.png)

* Stack
  * dynamic implicit Memory Management
    * local variables or function parameters (value types)
  * LIFO
  * strongly managed
* Heap
  * dynamic explicit Memory Management 
    * Class instances have to be created wit **new** before memory is allocated (reference data types)
  * no enforced pattern to the allocation and deallocation of blocks from the heap
  * Manual Managing (delete)

## Why is memory management on the heap manual in C?

The Heap is a larger memory section to fit dynamic sized data. The programer is responsible for allocation and deallocation of memory. Unnecessary data on the heap have to be freed by an explicit call of *free()*. Otherwise we will get a *memory leak*. An interesting detail about the heap is its scope. Stored data is automatically global and accessible everywhere. The main purpose of the heap is working with pointers.



