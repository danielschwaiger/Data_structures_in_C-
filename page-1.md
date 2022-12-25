---
description: Deletion of a node at the start of a linked list.
---

# 😩 Deletion - the first node (head).



Code example:

```c
/**
 * @brief 
 * deletion 
 * 
 * from the start 
 */
#include <stdio.h>
#include <stdlib.h>

typedef struct node
{
	int data;
	struct node *next;
}		   node_t;

void	initialize_head(node_t **head);
void	print_content(node_t *lst);
void	delete_head(node_t **lst);
void	insert_after(node_t *prev_node, int new_data);
void	append(node_t **head_ref, int new_data);
void	push(node_t **head, int new_data);

/**
 * @brief 
 * 1) Delete from Beginning:
	Point head to the next node i.e. second node
    	temp = head
    	head = head->next
    
	Make sure to free unused memory
    	free(temp); or delete temp;

	* 1. Obtain the node wich you want to eliminate !
	* 2. Point to the next node. Now the secodn node is your head of the list. 
	* 3. Now delete the first node.


		   head         second         third
		     |             |             |
		     |             |             |
		+---+---+     +---+---+     +----+----+
		| 1  | o----->| 2 | o------>|  # |  # |
		+---+---+     +---+---+     +----+----+ 


		  head(temp)    XsecondX      "third"
		    |             |             |
            X(free) |             |             |
		+---+---+      +---+---+     +----+----+
		| 1  | o---X-->| 2 | o------>|  # |  # |
		+---+---+      +---+---+     +----+----+    
				  ^		 ^
		             new head!	      second!..   

*/

int main(void)
{
	node_t *head;

	int array[] ={23, 35, 67, 77, 55, 66}, \
	len = (int)sizeof(array) / sizeof(array[0]);
	
	initialize_head(&head);
	if(head == NULL)
		printf("Node is ON! \n");

	for (int i = 0; i < len; i++)
		push(&head, array[i]);
	
	print_content(head);
	delete_head(&head);
	print_content(head); puts("\n");

	insert_after(head->next, 100);
	push(&head, 1000);
	print_content(head); puts("\n");
	
	delete_head(&head);
	print_content(head); puts("\n");

	return (0);
}

void	initialize_head(node_t **head)
{
	*head = NULL;
}

void print_content(node_t *lst)
{
	while (lst != NULL)
	{
		printf("%i ", lst->data);
		lst = lst->next;
	}
}

void	delete_head(node_t **lst)
{
	if (lst) 
	{
		node_t *temp = *lst;
     		*lst = temp->next;
		// (*lst) works as well as its pointing to the same address for next value 42  in this case !
		/* *lst = (*lst)->next; */
    		free(temp); // TOFIX - not solving leaks !! 
		temp = NULL;
    	}
}

void insert_after(node_t *prev_node, int new_data)
{
	if (prev_node->next == NULL)
		return ;
	node_t *new_node = (node_t *)malloc(sizeof(node_t));
	new_node->data = new_data;
	new_node->next = prev_node->next;
	prev_node->next = new_node;
}

void append(node_t **head_ref, int new_data)
{
	node_t *new_node = (node_t *)malloc(sizeof(node_t));
	node_t *last_node = *head_ref;
	new_node->data = new_data;
	if (*head_ref == NULL)
	{
		new_node = *head_ref;
		return ;
	}
	while (last_node->next != NULL)
		last_node = last_node->next;
	last_node->next = new_node;
}

void push(node_t **head, int new_data)
{
	node_t *new_node = (node_t *)malloc(sizeof(node_t));
	new_node->data = new_data;
	new_node->next = (*head);
	(*head) = new_node;
}
```

Pop or return the deleted node example:

```c
// works as well if you need to display the value that just poped out! 
// Just call the function as head = delete_head(head);

node_t	*delete_head(node_t *lst) 
{
	if (lst) 
	{
		node_t *temp = lst;
		lst = lst->next;
		free(temp);
	}
	return (lst);
}
```

