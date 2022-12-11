---
description: Bitwise OR operand
---

# | (OR) Operand

It takes two bits at a time and perfom OR operantion.

OR (|) is binary operator. It takes two numbers and perform bitwise OR.

Result of OR is zero when bots bits are zero.

![](<.gitbook/assets/OR\_birwise (1).png>)

Code examples:

```c
#include <stdio.h>

int main()
{
	// a = 5
	// a in binary representation is : 00000101 
	// b = 9
	// b in binary       --/--       : 00001001
	unsigned char a = 5, b = 9;

	// The result is 13 (00001101)
	printf("a = %d, b = %d\n", a, b);
	puts("\n");
	puts("00000101");
	puts("00001001");
	puts("--------");
	puts("00001101");				
	puts("\n");

	printf("a|b = %d\n", a | b);

	return (0);

}
```

Exersices:

```c
(4)  10101 | 00000   
(5)  11111 | 11111    
(6)  10101 | 11111
```

Differences between bitwise  (|) and logical operators (||) !!!

```c
int main(void)
{
	// a = 1 (0000 0001)
	// b = 2 (0000 0010)
	// result of : a | b = 3 (0000 0011);
	
	int a = 1, b = 2;
	
	printf("a | b = %d\n", a | b);
	
	if (a | b)
		printf("This will be printed if a | b as both are 1 = TRUE \n");

	if (a || b)
		printf("This also will be printed as a is 1 = TRUE and b is 1 = True, then TRUE || TRUE = TRUE = 1 \n");

	// reassigning values to test 
	a = 0, b = 2;

	if (a || b)
		printf("One of both has to be 1 to evaluate TRUE, then this message will be printed!\n");
	
	// reassigning values to test 
	a = 1, b = 0;

	if (a || b)
		printf("One of both has to be 1 to evaluate TRUE, then this message will ALSO be printed!\n");
	
	// reassigning 0 values to test 
	a = 0, b = 0;

	if (a || b)
		printf("One of both has to be 1 to evaluate TRUE, then this message will NOT be printed!\n");
	
	return (0);
}
```
