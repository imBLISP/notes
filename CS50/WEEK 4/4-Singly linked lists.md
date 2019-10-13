# SINGLY LINKED LISTS

https://www.youtube.com/watch?v=zQI3FyWm144&feature=youtu.be

-  So far in the course, we've only had one kind of data structure for representing collections of like values.
    - `Structs`, recall, give us "countainers" for holding variables of different datatypes, typically.
- Arrays are great for element lookup, but unless we want to insert at the very end of the array, inserting elements is quite costly - remember insertion sort?
- Arrays also suffer from a great inflexibility - what happens if we need a larger array than we thought?
- Through clever use of pointers, dynamic memory allocation, and `structs`, we can put the pieces together to develop a new kind of data structure that gives us the ability to grow and shrink a collection of like values to fit our needs.

- We call this combination of elements, when used in this way, a **linked list**.
- A linked list **node** is a special kind of struct with two members:
    - Data of some data type(`int`, `char`, `float`...)
    - A pointer to another node of the same type.
- In this way, a set of nodes together can be thought of as forming a chain of elements that we can follow from beginning to end.

```c
typedef struct sllist // we cant use sllnode here the reason being we havent created sllnode till we reach the end to the ;
{
    VALUE val;
    // self referential data type, struct sllist is a temperory name 
    struct sllist* next;
}
sllnode;
// sllnode is the new name 
```

- if your struct contains a self referential data type then you need to specify a temporary name. In this case the temporary name is `sllist` and the new name is `sllnode`.

###linked list Operations:

In order to work with linked lists effectively, there are a number of operations that we need to understand:

1. Create a linked list when it doesn't already exist.
2. Search through a linked list to find an element.
3. Insert a new node into the linked list.
4. Delete a single element from a linked list.
5. Delete an entire linked list.

#### Create a linked list:

```c
// VALUE is a arbitrary data type
// create returns a pointer to a singly linked list node
sllnode* create(VALUE val);

// example:
sllnode* new = create(6);
```

######Steps involved

1. Dynamically allocate space for a new `sllnode`.
2. check to make sure we didn't run out of memory.
3. Initialize the node's `val` field.
4. Initialize the node's `next` field.
5. Return a pointer to the newly created `sllnode`.

#### Search through the linked list to find an element:

```c
// return true or false depending on whether the value exists or not
// head is the pointer to the first element of the linked list
// val is the value you want to search
bool find(sllnode* head, VALUE val);
```

###### Steps involved:

1. Create a traversal pointer pointing to the list's head.
2. if the current node's `val` field is what we're looking for, report success.
3. if not, set the traversal pointer to the next pointer in the list and go back to step 2.
4. if you've reached the end of the list, report failure.

#### Insert a new node into the linked list.

```c
sllnode* insert(sllnode* head, VALUE val);
```

###### Steps involved:

1. Dynamically allocate space for a new `sllnode`.
2. Check to make sure we didn't run out of memory.
3. Populate and insert the node at the **beginning** of the linked list.
4. Return a pointer to the new head of the linked list.
5. We need the new node's `next` to point to the old head of the list first . order matters here.
6. If we move the head pointer to the new node then we will lose the list.

#### Delete an entire linked list:

```c
void destroy(sllnode* head);
```

###### Steps involved:

1. If you've reached a null pointer, stop.
2. Delete the rest of the list (recursion).
3. Free the current node.

- We are deleting the list from the end to the head.
- If we just freed the head first we would have no way to refer to the rest of the list.

#### Delete a single element from a linked list:

- This is tricky in singly linked lists.
- because we cant go backwards.



