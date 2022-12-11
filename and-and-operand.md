---
description: Bitwise AND operator
---

# & (AND) Operand

It takes two bits at a time and perform AND operation.

AND (&) is binary operator. It takes two numbers and performs bitwise AND.&#x20;

Result of AND is 1 when both bits are 1. See picture as example !&#x20;

<figure><img src=".gitbook/assets/Screen Shot 2022-12-11 at 4.21.28 PM.png" alt=""><figcaption></figcaption></figure>

Code Examples:

```c
#include <stdio.h>

int main(void)
{	
	// a = 5
	// // a in binary represented in bits: 00000101  
	// b = 9
	// b in binar      --/--             : 00001001
	unsigned char a = 5, b = 9;

	// The result is 00000001
	// a&b = 1
	printf("a = %d, b = %d\n", a, b);
	puts("\n");
	puts("00000101");
	puts("00001001");
	puts("--------");
	puts("00000001");				
	puts("\n");
	printf("a&b = %d\n", a & b);
	
	return  (0);
}
```

Exercises:

```c
(1)  10101 & 00000    
(2)  11111 & 11111    
(3)  10101 & 11111 
```

Differences between bitwise  (&) and logical operators (&&) !!!

<pre class="language-c"><code class="lang-c"><strong>#include &#x3C;stdio.h>
</strong>
int main(void)
{
	// a = 1 (0000 0001), b = 2(0000 0010)
	// Output :
	// a&#x26;b = 0 (0000 0000)
	
	int a = 1, b = 2;

	if (a &#x26; b)
		printf("This will be printed if a &#x26; b is 1 and not printed if 0");
	if (a &#x26;&#x26; b)
		printf("a &#x26;&#x26; b = This is different and will be printed as both values exist !"); 
	// Explained: a = 1 wich is TRUE, b = 2 wich is also TRUE as 1 and 2 are values treated as 1 and not as 0. So, evaluation would be -> TRUE &#x26;&#x26; TRUE = TRUE = 1; 
	
	// Re assiging values and testing... 
	a = 0, b = 0;
	if (a &#x26;&#x26; b)
		printf("This will not be printed !! ");

	// Re assiging values and testing... 
	a = 1, b = 0;
	if (a &#x26;&#x26; b)
		printf("This will not be printed !! ");


	// Re assiging values and testing... 
	a = 0, b = 2;
	if (a &#x26;&#x26; b)
		printf("This will not be printed !! ");


	return (0);
}
</code></pre>
