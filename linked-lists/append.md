---
description: Insertion or push to head
---

# 🤟 Append

```c
/**
 * @brief 
 * insertion of a new node at the front of llst. 4 steps process !
 */

#include <stdio.h>
#include <stdlib.h>

struct Node 
{
	int data;
	struct Node *next;
};

/**
 * @brief 
 * // what we want is to change the content of our llst from outside withtout returning nothing !
 * // we use **head to acces adress of head by reference ( pointer to pointer)  and push a new node in the 
 * // front of the list !
 * @return NOTHING 
 */

void push_to_head(struct Node **head, int *new_data)
{
	// we allocate memory to the new node !

	struct Node *temp = (struct Node *)malloc(sizeof(struct Node));
	
	// we put in the data in heap
	temp->data = *new_data;

	// make next of new node as head
	temp->next = (*head);

	// move the head to point to the new node!
	(*head) = temp;
}

void print_llst_values(struct Node *lst)
{
	while (lst != NULL)
	{
		printf("%i ", lst->data);
		lst = lst->next;
	}
}

int main()
{
	struct Node *head = NULL; // starts the llst with NULL value in first position!

	// we insert 10 numbers inside our each element in llst !
	// TODO next time generate random number from a funcion
	for (int i = 20; i --> 10;)
		push_to_head(&head, &i);

	// prints out the values that we generated in the previous step with for loop
	print_llst_values(head);
	return (0);
}
```
