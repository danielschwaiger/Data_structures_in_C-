---
description: Explained right shift operand
---

# >> Right shift Operand

![](<.gitbook/assets/Screen Shot 2022-12-12 at 4.31.41 PM.png>)



Important fact that when bits are shifted to right is that trailing positions are filled with zeros.

```c
#include <stdio.h>

int main(void)
{
	// var 3 in binary : (0000 0011) 
	// right shifted would be also [3 / 2^1] - multiplied with 2 power of 1 wich is 1.  
	// bits shifted    : (0000 0001) : Important fact when bits are shifted right is that trailing positions are filled with zeros.
	signed int var = 3, result;
	// number of shifted bits is 1.
	result = var >> 1;
	printf("var shifted right 1 bits = %d\n", result);

	// for example, if the number of bits to shift is four:
	result = var >> 4;
	// then, doing the math [3 / 2^4]
	// result is 0 as all bits are shifted to 0 (0000 0000)
	printf("var shifted right 4 bits = %d\n", result);
	

	// for example if number to shift is againg four:
	var = 32;
	result = var >> 4;
	// then, doing the math [32 / 2^4]
	// result is 2 as 32 = 2 * 2^4
	printf("var shifted right 4 bits = %d\n", result);
	
	return (0);
}
```

