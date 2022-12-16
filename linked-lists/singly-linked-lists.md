---
description: Linked lists with example
---

# Singly Linked Lists

<figure><img src="../.gitbook/assets/Screen Shot 2022-09-19 at 5.01.10 PM.png" alt=""><figcaption></figcaption></figure>

Questions:

What is the difference between an "element" and a "node" in data structure concepts?

Another way to think of data structures is that they are organized containers for information. In this perspective, a data structure is composed of nodes, each of which contains an element. For example, an array is simply an indexable list of elements, though I wouldn't call any part of an array a node, despite an array being a very basic data structure.

In contrast, a binary tree is a data structure where the nodes are the units that have left and right relations to other nodes, but the data stored inside each node are elements of the data set contained in the tree.

In that sense, I suppose a node describes something which holds relation to other nodes, whereas an element describes a unit of information itself. The list \[1]->\[2]->\[3]->\[NULL] is a series of nodes containing the elements 1, 2, and 3.

In our libft project (42School), the generic linked list is a good example of a generalized container. Each node in the list is a struct with reference to an element, and a reference to the next node in the list. But the struct is a definition for the node, not for the data element referenced by the void pointer.

* ### Index:
* Simple construction of a singly linked list
* Append to a linked list with examples.
* Insert at a given n position.
