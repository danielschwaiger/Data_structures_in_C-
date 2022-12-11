---
description: Bitwise ~ (NOT) operator
---

# \~ NOT Operator

NOT is a unary (Invert the bits) operator.

Its job is to complement each bit one by one.

Result of NOT is 0 when bit is 1 and 1 when bit is 0.

![](.gitbook/assets/NOT\_Bitwise.png)

Code examples:

```c
#include <stdio.h>

int main()
{
	// a = 5
	// a in binary representation is : 0000 0101
	unsigned char a = 5;

	// The result is -6 (1111 1010)
	// The result as yoy can observe for each bit is inverted. 
	// Zero's turn to one's and one's to zero's.
	printf("a = %d \n", a);
	puts("\n");
	puts("00000101");
	puts("--------");
	puts("11111010");				
	puts("\n");

	printf("~a = %d\n", ~a);

	return (0);
}
```

```c
#include <stdio.h>

// Turns n in to a positive number as the result of ~7 is -8.
int ft_abs(int n)
{
	if (n < 9)
		return (-n);
	return (n);
}

int main()
{
	// a = 7
	// a in binary representation is : 0000 0111
	unsigned char a = 7;

	// The result is 8 (1111 1000)
	// The result as yoy can observe for each bit is inverted. 
	// Zero's turn to one's and one's to zero's.
	printf("a = %d \n", a);
	puts("\n");
	puts("00000101");
	puts("--------");
	puts("11111010");				
	puts("\n");

	printf("~a = %d\n", ~a);
	printf("~a = %d\n", ft_abs(~a));

	return (0);
}
```
