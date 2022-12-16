---
description: Simple construction of a singly linked list
---

# 💀 Simple construction

```c
#include <stdio.h>
#include <stdlib.h>

struct Node
{
	int data;
	struct Node *next;
};

int ft_len_linklst(struct Node *lst)
{
	struct Node *ptr = lst;
	size_t len = 0;

	while(ptr != NULL)
	{
		ptr = ptr->next;
		len = len + 1;
	}
	return (len);
}

void print_lst_data(struct Node *element)
{
	while(element != NULL)
	{
		printf("%i\n", element->data);
		element = element->next; // will loop the entire llst.
	}
}

int main()
{
	// declare and iniciate the nodes manually.

	struct Node *head = NULL;
	struct Node *second = NULL;
	struct Node *third = NULL;

	//allocate 3 nodes in the heap manually 

	head = (struct Node*)malloc(sizeof(struct Node));
	second = (struct Node*)malloc(sizeof(struct Node));
	third = (struct Node*)malloc(sizeof(struct Node));

	/* Three blocks have been allocated dynamically.
     	We have pointers to these three blocks as head,
     	second and third
       
 	      head           second           third
        	|                |               |
        	|                |               |
    	    +---+-----+     +----+----+     +----+----+
    	    | #  | #  |     | #  | #  |     |  # |  # |
            +---+-----+     +----+----+     +----+----+
  
  	# represents any random value.
   	Data is random because we haven’t assigned
   	anything yet  */
	
	head->data = 1; // asingh data in the first node 
	head->next = second; // lings first node with the second.

	/* data has been assigned to the data part of the first
	block (block pointed by the head). And next
        pointer of first block points to second.
        So they both are linked.
  
	     head          second         third
              |              |              |
              |              |              |
    	  +---+---+     +----+----+     +-----+----+
    	  | 1  | o----->| #  | #  |     |  #  | #  |
          +---+---+     +----+----+     +-----+----+
 	*/

 	second->data = 2;
	second->next = third;
	
	/* data has been assigned to the data part of the second
	block (block pointed by second). And next
	pointer of the second block points to the third
	block. So all three blocks are linked.
	
               head         second         third
		|             |             |
		|             |             |
            +---+---+     +---+---+     +----+----+
            | 1  | o----->| 2 | o-----> |  # |  # |
   	    +---+---+     +---+---+     +----+----+      */

	third->data = 3;
	third->next = NULL;

	/* data has been assigned to data part of third
    	block (block pointed by third). And next pointer
    	of the third block is made NULL to indicate
    	that the linked list is terminated here.
  
     	We have the linked list ready.
  
            head
             |
             |
        +---+---+     +---+---+       +----+------+
        | 1  | o----->|  2  | o-----> |  3 | NULL |
        +---+---+     +---+---+       +----+------+
  
  
  	Note that only head is sufficient to represent
   	the whole list.  We can traverse the complete
   	list by following next pointers.    */


 	//function to find out size of singly linked list !
	printf("Size of lst is : %i\n", ft_len_linklst(head));
	
	//function to print out the data inside linked lists TRAVERSAL !
	print_lst_data(head);
	return (0);
}
```
