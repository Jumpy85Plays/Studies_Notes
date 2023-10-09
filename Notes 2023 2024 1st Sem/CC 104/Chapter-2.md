# Data Structures and arrays
Data structure uses some algorithms and need storage for storing values
storing values require fundamental data types

## Arrays
Linear data structure
a fixed-size sequenced collection of the same data type
	`syntax: data_type data_name [array_size]`
Element = All items stored in an array
Index = memory location of an element

### Basic operations
**Traversing**: prints all array elements
**Inserting**: adding an element at a given index
**Deleting**: delete an element at a given index 
**Searching:** finds an element(s) using a given index or value
**Updating:** update an element at a given index

## Linked List
	Linear data structure
	also known as one way list
	a linear set of data elements which is also termed as nodes
	the linear order is specified using pointers

Node structure
consists of 2 elements
- **Data**
	- Holds the actual values or data associated with the node
- **Next Pointer**
	- Stores the memory address (reference) of the next bide in the sequence

**Syntax**
```C++
struct node {
	// values
	int data;
	// addresses
	struct node *next;
};
```
**Head and tail**
	accessed through the head node
	which points to the first node in the list
	the last node in the list points to NULL
	indicating the end of the list
	this node is known as the tail node

### Why use link list
- Dynamic data structure
	the size of memory can be allocated or de-allocated at run time based on the operation insertion or deletion
- Ease of insertion/deletion
	simpler than arrays since no elements need to be shifted after insertion and deletion
	Just address updates
- efficient memory utilization
	avoids wasting memory
- implementation
	various advanced data structures can be implemented using link list

### Advantages
- Dynamic Size
	can grow or shrink dynamically as memory allocation is done at runtime
- Insertion and deletion
	adding or removing elements from a linked list is efficient
- Flexibility
	easily reorganized and modified without requiring a contiguous block or memory
### Disadvantages
- Random Access
	Does not allow direct access to elements by index
	Traversal required to reach a specific node
- Extra Memory Usage
	require additional memory for storing pointers compared to arrays

### Types of link list
1. Singly-linked list : Traversal of items in a forward direction
2. Doubly linked list : each node contains a reference to both the next and previous nodes. Allows traversal both backward and forward but requires additional memory
3. Circular linked list : the last node points back to the head node and can be singly or doubly

### Operations
#### general operations
1. Insertion
	refers to adding a node to the tail of the list
	head = fi, in which case the node we are adding is now both the head and tail of the list
	or we simply need to append our node onto the end of the list updating the tail reference appropriately
```Psudocode
PRE: value is the value added to the list
POST: value has been placed at the tail of the list
ADD(value)
	n <- node(value)
	if head = fi
		head <- n
		tail <- n
	else
		Next <- n
		tail <- n
	end if
end ADD
```

2. Deletion
	deleting a node from a link list
things cases to account for
- the list is empty
- the node to remove is the only node in the link list
- removing the head node
- removing the tail node
- removing a node in between the head and tail
- removing an item that doesn't exist in the link list
```Psudocode
PRE: the head is the head node of the list
values is the value to remove from the list
POST: if value is removed from the list true otherwise false
REMOVE(head, value)
	if head = fi
		return false
	end if
	n <- head
	if n.value == value
		if head == tail
			head <- fi
			tail <- fi
		else
			Head <- head.Next
		end if
		return true
	end if
	while n.Next != fi and n.Next.Value != value
		n <- n.Next
	end while
	if n.Next != fi
		if n.Next == tail
			tail <- n
		end if
		Next <- n.Next.Next
		return true
	end if
	return false
end REMOVE
```

3. Searching
traverse the list checking the value we are looking for with the value of each node in the linked list
```Psudocode
PRE: the head is the head of the node in the list
value is the value to search for
POST: if item is in the list, true otherwise false
CONTAINS(head, value)
	n <- head
	while n != fi and n.value != value
		n <- n.Next
	end while
	if n = fi
		return false
	end if
	return true
end CONTAINS
```

#### singly operations
1. Insertion
	- Inserting at the beginning of the list
	```Psudocode
	PRE: the head is the head of the node in the list
	value is the value to add
	POST: inserts a new node to the front of the list
	PUSH(head, value)
		// 1. allocate node
		node = new node
		// 2. put in the data
		node.Value = value;
		// 3. Make next of the new node as head
		node.Next = head
		// 4. Move the head to point to the new node
		head = node
	end PUSH
	```
	- Inserting at the end of the list
	- Inserting somewhere in-between the list
		- conditions: check if given node exists
			- if it does not 
				- terminate process
			- if it exists
				- make the element to be inserted as a new node
				- change the next pointer of the given node to the new node
				- shift the original pointer of the given note to the next pointer of the new node
	``` Psudocode
	PRE: prev_node is the node to insert a new node
	POST: insert new node and connect previous node to new node
	INSERTAFTER(prev_node, value)
		1. Check if the given node is null
		if prev_node == NULL
			return
		end if
		1. Allocate new node
		node = new node
		1. Insert data
		node.Value = value
		4. Make next of new node as next of prev_node
		node.Next = prev_node.Next
		5. move the next of pre_node as new node
		prev_node.Next = node
	end INSERTAFTER
	```

2. Deletion
	- deleting from the beginning of the list
	- deleting at the end of the list
	- deleting somewhere in-between the list

3. Search
	determining and retrieving a specific node either from anywhere in the list

4. Display
	shows elements in the singly linked list

