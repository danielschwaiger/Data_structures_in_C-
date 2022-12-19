---
description: Add a node after a given node.
---

# 👽 Insertion - after a given node

Insert a new node at a given position 5 steps process !

We are given a pointer to a node, and the new node is inserted after the given node.![](<../.gitbook/assets/Screen Shot 2022-12-16 at 4.07.45 PM.png>)

Fourth and sixth being new nodes added inside the linked list Node.\
Code example :&#x20;

```c
/**
 * @brief 
 * insert a new node at a given position 5 steps process !
 : We are given a pointer to a node, and the new node is inserted after the given node.
 */
#include <stdio.h>
#include <stdlib.h>

struct Node
{
	int data;
	struct Node *next;
};

// Using previous function to add elements to our llst.
void push_to_head(struct Node **head, int new_data)
{
	struct Node *temp = (struct Node *)malloc(sizeof(struct Node));

	temp->data = new_data;

	temp->next = (*head);

	(*head) = temp;
}

/**
 * @brief 
 * 	*Firstly, check if the given previous node is NULL or not.
	*Then, allocate a new node and
	*Assign the data to the new node
	*And then make the next of new node as the next of previous node. 
	*Finally, move the next of the previous node as a new node.
 */
void push_after(struct Node *prev_node, int new_data)
{
	if (prev_node->next == NULL)
		return ;
	
	struct Node *new_node = (struct Node *)malloc(sizeof(struct Node));

	new_node->data = new_data;

	new_node->next = prev_node->next;

	prev_node->next = new_node;
}

void print_llst_content(struct Node *lst)
{
	if (lst->next == NULL)
		return ;
	while (lst != NULL)
	{
		printf("%i ", lst->data);
		lst = lst->next;
	}
}

int main(void)
{
	struct Node *head = NULL;

	for (int i = 4; i --> 1;)
		push_to_head(&head, i);

	//print out the content inserted !
	print_llst_content(head);
	puts("\n");
	// call the function to insert the node at a given node.
	// it will only insert between second and not first node till  in the previos node and not at the end!! wich is next to NULL.
	push_after(head->next,  55);

	print_llst_content(head);
	return (0);
}
```
