# Programmierung in C / C++: Übung 3

## Data types and Variables
-----------------------
## What is the value range relationship between "char", "short", "int", "long" and "long long". What is defined about their type size/value range? What about unsigned types?
-----------------------
The standard tooks this different types and their supported ranges only in relationship and defines minimum boundaries.

> sizeof(char) ≤ sizeof(short) ≤ sizeof(int) ≤ sizeof(long) ≤ sizeof(long long)

* char min. 8bit 
* short min. 16bit
* long min. 32bit
* long long min. 64bit
-----------------------
## Give 3 examples of integer data types that have a fixed size? In what standard were they introduced?
-----------------------
* C99 Standard
* defines optional fixed size integers
* int8_t, uint16_t, int16_t [See here...](http://en.cppreference.com/w/c/types/integer)
-----------------------
## What is the difference between the data type *char* in C and in Java
-----------------------
* Characters in C are simple integer constants
* No unicode support in old *C*
* Java has his own data type for characters

```c
// This is possible
int i = 'M'; 
```

-----------------------
## Why is C a weakly typed programming language? Provide an explanation
-----------------------

* For example: Addition of *int* and *float*
* C does not check for compatibility of the given operands
* It tries to calculate a result

```c
#include <stdio.h>
#include "preprocessor.h"

int main(int argc, char* argv[]) {
	int x = 5;
	float y = 5.5;
	int z = x+y;

	// Implicit conversion of result to float
	printf("%f \n", (x+y));

	// Floating part will  discarded
	printf("%d \n", z);
}
```

**Output**

```bash
$ gcc preprocessor.c && ./a.out
10.500000 
10 

```

-----------------------
## What is the difference between declaration, definition and initialization of a variable?
-----------------------
**Declaration:** Defines identifier and type. Value not given

* Static name and type binding
* Eases parsing

```c

int i;
```

**Definition:** Allocates memory for variable

* Allocates memory
* Looks exactly the same as abow
* Declaring without defining via Linkage

```c

int i;
```


**Initialization:** Define, Declare and set initial value of variable


```c
// Not necessarily static

int i = a + b;

// But can...
int i = 5;
```

-----------------------
## What is the scope of a variable? What are possible problems with variable scopes?
-----------------------
* Default Scope is Block Scope
* Variables defined outside a function are in FileScope and therefor globally accessible.
* Scopes are cascading each other
* Variables refer to the next near scope. A local variable will hide a global one which is named equal.

-----------------------
## Name all possible variable scopes and their differences.
-----------------------

* FileScope
  * Defined outside of a function
  * Accessible everywhere in application : **extern int a; // Load global variable into local file*
* FunctionScope
  * Can only be referenced inside defining function
  * Usage for labels "case:"
  * Not for variables et al.
* BlockScope
  * { BLOCK-START        BLOCK-END }
  * Local variables and function parameters
* Function-prototype Scope
  * Parameter list of prototype
  * Names of parameters in prototype are not considered by the compiler
  * Prototype- and Implementation-Parameter namings can be different













