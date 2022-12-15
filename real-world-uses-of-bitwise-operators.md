---
description: Ok, those where the basics..but where would we actually use them?
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


```c
// * Flags implementation for memory optimization when we work with low hardware requirements example and C98 (no <stdbool.h>).

#include <stdlib.h>
#include <stdio.h>

#define SECURITY_CHECK_FLAG 0b1         // 0000 0001
#define TWO_FACTOR_AUTH_CHECK_FLAG 0b10 // 0000 0010
#define DEFAULT_FLAG 0b100     		// 0000 0100


int main(void)
{
	/*
		Bulky way of doing this usually when available <stdbool.h> :
		Memory usage: 3 * sizeof(bool) = 3 bytes.
	*/

	/*
		The optimized way:
		Memory usage: sizeof(unigned short int) = 2bytes. 
	*/
	unsigned short int flags = 0;

	puts("--------------------------------------------------------");
	// Enabling and printing flags:
	flags = flags | TWO_FACTOR_AUTH_CHECK_FLAG;
	printf("TWO_FACTOR_AUTH is enabled  : %d\n", flags);            //    0000 0010
	flags = flags | DEFAULT_FLAG;                                  //     0000 0100
	printf("DEFAULT_FLAG flag is enabled: %d\n", flags);          //  6 = 0000 0110
	puts("--------------------------------------------------------\n");
	// Check if DEFAULT_FLAG is enabled!
	if (flags & DEFAULT_FLAG)
		// flags        0000 0110
		// DEFAULT_FLAG 0000 0100
		// &            0000 0110
		printf("Check if DEFAULT_FLAG is enabled!\n"); //FLAG IS ENABLED AS WE DID PREVIOUSLY.
	
	// Check if others flags are enabled!
	if (flags & SECURITY_CHECK_FLAG)
		printf("SECURITY_CHECK_FLAG is enabled\n"); // FALSE !

 	if (flags & TWO_FACTOR_AUTH_CHECK_FLAG)
		printf("TWO_FACTOR_AUTH_CHECK_FLAG is enabled\n"); // TRUE !
	puts("--------------------------------------------------------\n");
	printf("Disabling TWO_FACTOR_AUTH_CHECK_FLAG...\n");
	// Disabling flags. How to!
	flags ^= TWO_FACTOR_AUTH_CHECK_FLAG;
	printf("TWO_FACTOR_AUTH_CHECK_FLAG status:  %d\n", flags);
	//also posible to disable flags with & and ~ bitwise operands!
	flags &= ~DEFAULT_FLAG;
	printf("DEFAULT_FLAG status:  %d\n", flags);
	puts("--------------------------------------------------------\n");
	// Check !
 	if (flags & DEFAULT_FLAG)
		printf("DEFAULT_FLAG is still enabled\n");
	if (flags & TWO_FACTOR_AUTH_CHECK_FLAG)
		printf("DEFAULT_FLAG is still enabled\n");
	if (flags & SECURITY_CHECK_FLAG)
		printf("SECURITY_CHECK_FLAG is still enabled\n");
	puts("--------------------------------------------------------\n");
	// Enabling Default flag!
	if(!(flags & DEFAULT_FLAG))
	{
		flags |= DEFAULT_FLAG;
		printf("Status of DEFAULT_FLAG changed to enabled! %d\n", flags);
	}
	//Swiching OFF.
	flags &= ~DEFAULT_FLAG;
	printf("ALL STATUS DISSABLED %d\n", flags);
	return (0);
}
```

Easier example of flags implementation after the previous one :D

```c
// * Easy flags implementation for memory optimization.

#include <stdlib.h>
#include <stdio.h>

#define FIRST_FEATURE_FLAG 0b1               // 0000 0001
#define SECOND_FEATURE_FLAG 0b10             // 0000 0010
#define THIRD_FEATURE_FLAG 0b10000000        // 1000 0000


int main(void)
{
	// As we did learned before in the previous example we can use less memory to store our flag status and only one variable!
	// With this example we understand that also can be declared till 31 states of flags to play with!
	unsigned int flags = FIRST_FEATURE_FLAG | SECOND_FEATURE_FLAG | THIRD_FEATURE_FLAG;

	puts("--------------------------------------------------------");

	// disabling FIRST_FEATURE_FLAG;
	flags &= ~FIRST_FEATURE_FLAG;
	// or also we can use this ^ operand to disable a flag!
	flags ^= THIRD_FEATURE_FLAG;

	// All states back on!
	flags |= FIRST_FEATURE_FLAG;
	flags |= THIRD_FEATURE_FLAG;

	// Play with all the options!
	puts("--------------------------------------------------------\n");

	// Check !
 	if (flags & FIRST_FEATURE_FLAG)
		printf("FIRST_FEATURE_FLAG is enabled\n");
	if (flags & SECOND_FEATURE_FLAG)
		printf("SECOND_FEATURE_FLAG is enabled\n");
	if (flags & THIRD_FEATURE_FLAG)
		printf("THIRD_FEATURE_FLAG is enabled\n");
	puts("--------------------------------------------------------\n");
	
	return (0);
}
```

Turning any char to binary ? Here is how to !

```c
#include <stdio.h>

void to_binary(int n)
{ 
	/*
	    n = 2;
	    i = 1 << 7 = 128 same as 0b10000000 same as 0000 0000 1000 0000
      	    i /= 128..64..32..16..8..4..2..1 while i > 0 !
	    (n & i)  = 0 False
	               0 False 
		       0 False
	               0 False
	               0 False
		       0 False
		       0 True
		       0 False
	         
	The only case that's True and prints a 1:

	    &    0000 0010
	         0000 0010
	Output : 0000 0010 = (prints 1) True
		
	*/
	
	for(unsigned char i = 1 << 7; i > 0; i = i / 2)
		(n & i) ? printf("1") : printf("0");
}

int main(void)
{
	unsigned int i = 2;

	to_binary(i);

	return (0);
}
```
