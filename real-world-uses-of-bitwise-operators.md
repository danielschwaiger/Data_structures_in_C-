---
description: Ok, those where the basics..but where would we actually use it?
---

# Real world uses of bitwise operators

### Power of two using bitwise operands and logical operands.

```c
#include <stdio.h>

// * Power of two using bitwise operands and logical operands.

void ft_power(int a)
{
	if ( a > 0 && (a & (a - 1)) == 0)
	/*
		a > 0 is TRUE && (a & (a - 1))== 0 is TRUE -> Explanation:

		  a   = 0000 0010 same as 0b10
		a - 1 = 0000 0001 same as 0b1
		  &   = 0000 0000 same as 0b0 -> evaluated as TRUE 0b0 == 0.
	*/
		printf("Is power of two! %d\n", a);
	else
		printf("Not power of two! %d\n", a);
}

int main(void)
{
	int num = 8;

	ft_power(num);

	return (0);
}
```

### Storing Multiple Boolean Flags how to:

Given that somethimes we work on limited memory devices, there is no really affordable memory to play with and have hundreds of boolean flags assigned to variables. That, being a really inneficient way to store flags in C because Boolean value are basically a byte log. \
Solution -> We don't need an entire byte to store just a zero or a one.\
Example : \


