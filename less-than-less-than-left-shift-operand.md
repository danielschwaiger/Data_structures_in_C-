---
description: Explained left shift operand
---

# << Left shift Operand

![](<.gitbook/assets/Screen Shot 2022-12-12 at 3.53.13 PM.png>)

Important fact when bits are shifted left is that trailing positions are filled with zeros.

```c
#include <stdio.h>

int main(void)
{
	// var 3 in binary : (0000 0011) 
	// left shifted would be also [3 * 2^1] - multiplied with 2 power of 1 wich is 6.  
	// bits shifted    : (0000 0110) : Important fact when bits are shifted left is that trailing positions are filled with zeros.
	signed int var = 3, result;
	// number of bits to shift in this example is one.
	result = var << 1;
	printf("var shifted left is = %d\n", result);
	
	 
	// for example, if the number of bits to shift is four:
	result = var << 4;
	// then, doing the math [3 * 2^4]
	// result is 48
	printf("var shifted left 4 bits = %d\n", result);

	return (0);
}
 
```
