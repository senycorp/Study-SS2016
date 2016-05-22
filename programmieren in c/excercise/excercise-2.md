# Programmierung in C / C++: Übung 2

## Preprocessor

Makros werden ausgewertet und dann im Text gesucht und ersetzt. Parametrisierte Makros sind gefährlich und müssen vorsichtig behandelt werden.

**preprocessor.h**

```c
#define PI 2.0
#define CIRCLE_AREA(r) (PI*(r)*(r))
#define MAX(a,b) ((a) < (b) ? (b) : (a))
```

**preprocessor.c**

```c
#include <stdio.h>
#include "preprocessor.h"

int main(int argc, char* argv[]) {
	
	printf("%f", CIRCLE_AREA(4));

	int x = 5;
	int y = 10;
	int z = MAX( x++, y++);

	printf("MAX %d / %d : %d", x, y, z);
	return 0;
}
```

**Output**

```bash
 ~/tmp  gcc preprocessor.c && ./a.out
MAX 6 / 12 : 11%  
```