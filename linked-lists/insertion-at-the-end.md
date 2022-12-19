---
description: Insertion of node at the end of a singly linked list
---

# 🧐 Insertion - at the end

Insertion of a node at the end ( 6 steps process ).

![](<../.gitbook/assets/Screen Shot 2022-12-16 at 4.42.32 PM.png>)

```c
#include <stdio.h>
#include <stdlib.h>

struct Node
{
	int data;
	struct Node *next;
};

/**
 * @brief 
 * fills the lls with given data 
 */

void push_to_head(struct Node **head, int new_data)
{
	struct Node *new_node = (struct Node *)malloc(sizeof(struct Node));
	new_node->data = new_data;
	new_node->next = (*head);
	(*head) = new_node;
}

/**
 * @brief 
 * prints the content of lls
 */
void prints_lls_content(struct Node *lst)
{
	while (lst != NULL)
	{
		printf("%i ", lst->data);
		lst = lst->next;
	}
}

/**
 * @brief 
 * example if the given Linked List is 5->10->15->20->25 
 * and we add an item 30 at the end,
 * then the Linked List becomes 5->10->15->20->25->30.
 
* Since a lls is tipically represented bt the head of it, we have to 
traverse the list till the end of and then change the next to the last to a new node. 

	* Allocate memory for the new node and also create a pointer as *last_node pointing to *head_reaf
	* set the new_node->data to new_data
	* set the next node to NULL
	* if the linked list is empty, then make the new node as head!
	* Traverse the list until null is encountered. That will leave the last node available as working with i to iterate a string.
	* from last position of last_node now we point the next and take the element as new_node.
	
*/
void append(struct Node **head_ref, int new_data)
{
	/*1 allocate the node */
	struct Node *new_node = (struct Node *)malloc(sizeof(struct Node));
	      /* used in step 5 */
	struct Node *last_node = *head_ref;
	/*2 put  in the data */
	new_node->data = new_data;
	/*3 as we set te new node to be the last, point next to NULL */
	new_node->next = NULL;
	/*4 if the linked list is empty set the new node as head*/
	if (*head_ref == NULL)
	{
		*head_ref = new_node;
		return ;
	}
	/*5 else traverse till the last node */
	while (last_node->next != NULL)
		last_node = last_node->next;
	/*6 change the next of last node */
	last_node->next = new_node;
}

int main(void)
{
	struct Node *head = NULL;
	int array[] = {25, 20, 15, 10, 5};

	// push array to lls function !
	for (int i = 0; i < 5; i++)
		push_to_head(&head, array[i]);
	// print lls content !
	prints_lls_content(head);
	// add at the end of the lls item 30
	append(&head, 30); puts("\n");
	// print lls content !
	prints_lls_content(head); 
	
	free(head);
	return (0);
}
```
