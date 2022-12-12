---
description: Exclusive OR (XOR) operand explained
---

# XOR Operand

![](<.gitbook/assets/Screen Shot 2022-12-12 at 4.46.07 PM.png>)

Code examples:

```c
#include <stdio.h>

/* void ft_swap(int *a, int *b)
{
	*a = *a ^ *b;
	*b = *b ^ *a;
	*a = *a ^ *b;
} */

void ft_swap(int *a, int *b)
{
	*a ^= *b;
	*b ^= *a;
	*a ^= *b;
}

int main(void)
{
	signed int a, b;

	/*
	Truth table XOR 
 	0 0 0
	1 0 1
	0 1 1
	1 1 0
	*/

	// 1 (0000 0001) 
	// 2 (0000 0010)
	// Given the ft_swap function:
	// *a ^= *b wich a is 1 and b is 2 will turn in to 0000 0011 that is 3:
	// *b ^= *a wich b is 2 and a is 3 will turn in to 0000 0001 that is 1;
	// *a ^= *b wich a is 3 and b is 1 will turn in to 0000 0010 that is 2;
	// turns that a now is 2 and b is 1;

	a = 1 ,b = 2;

	printf("Before swap a and b		= %d, %d\n  ", a, b);
	ft_swap(&a, &b);
	printf("Swaped values of a and b		=  %d, %d\n", a, b);

	return (0);
}
```

