---
description: Inserts a node at a specific position (n) inside a linked list.
---

# 💡 Insertion - at a specific position

<figure><img src="../.gitbook/assets/Screen Shot 2022-12-19 at 8.29.06 PM.png" alt=""><figcaption></figcaption></figure>

```c
#include <stdio.h>
#include <stdlib.h>

typedef struct s_node
{
	int data;
	struct s_node *next;
}				t_node;

void	initiate_t_node(t_node **head)
{
	*head = NULL;
}	

void	push_to_head(t_node **head, int data)
{
	t_node *temp = (t_node *)malloc(sizeof(t_node));
	temp->data = data;
	temp->next = (*head);
	(*head) = temp;
}

int check_size(t_node **head)
{
	t_node *ptr = *head;
	int size = 0;
	while (ptr != NULL)
	{
		size++;
		ptr = ptr->next;
	}
	return (size);
}

void	insert_at_position_n(t_node **head, int position, int new_data)
{
	t_node *ptr = *head;
	int node = 0;

	if (position < 1 || position > check_size(head))
		printf("\nInvalid Position!!!!!!!!!!!!!");
	
	t_node *new_node = (t_node *)malloc(sizeof(t_node));
	if (!new_node)
		return ;
	while ((ptr != NULL) && (position != node))
	{
		node++;	
		if (position == node)
		{	
			new_node->data = new_data;
			new_node->next = ptr->next;
			ptr->next = new_node;
		}
		ptr = ptr->next;
	}	
}

void	print_lls_content(t_node *lls)
{	
	while (lls != NULL)
	{
		printf("%d ", lls->data);
		lls = lls->next;
	}
}

int main(void)
{
	// Data to insert;
	int num = 110;

	t_node *head;
	// function to initiate a lls
	initiate_t_node(&head);
																																
	int array[] = {12, 44, 55, 66, 77, 88};
	int len_array = sizeof(array) / sizeof(int);

	//Add array data inside lls.
	if (head == NULL)
	{
		for (int i = 0; i < len_array; i++)
			push_to_head(&head, array[i]);
	}
	
	// Print lls content
	if (head != NULL)
		print_lls_content(head);

	// insertion of a new node at certain position n.
	// at position 2 num = 2;
	insert_at_position_n(&head, 5, num);
	
	puts("\nResult: ");
	
	if (head != NULL)
		print_lls_content(head);
		
	
	free(head);
	return (0);
}
```
