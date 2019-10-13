# DOUBLY LINKED LISTS

https://www.youtube.com/watch?v=FHMPswJDCvU&list=PLhQjrBD2T381k8ul4WQ8SQ165XqY149WW&index=18

Singly-linked lists really extend our ability to collect and organize data, but they suffer from a crucial limitation.

- We can only ever move in one direction through the list.

Consider the implication that would have for trying to delete a node.

A doubly-linked list, by contrast, allows us to move forward and backward through the list, all by simply adding one extra pointer to our `struct`definition.

Use doubly-linked lists when you want to delete single elements.

```c
typedef struct dllist
{
    VALUE val;
    struct dllist* prev;
    struct dllist* next;
}
dllnode;
```

In order to work with linked lists effectively, there are a number of operations that we need to understand:

1. Create a linked list when it doesn't already exist.
2. Search through a linked list to find an element.
3. Insert a new node into the linked list **(Different from singly-linked list)**.
4. Delete a single element from a linked list **(different from singly-linked lists)**
5. Delete and entire linked list.

#### Insert a new node into the linked list:

`dllnode* insert(dllnode* head, VALUE val);`

`list = insert(list, 12);`

###### Steps involved:

1. Dynamically allocate space for a new `dllnode.`
2. Check to make sure we didn't run out of memory.
3. Populate and insert the node at the beginning of the linked list.
4. Fix the `prev` pointer of the old head of the linked list.
5. Return a pointer to the new head of the linked list.

#### Delete a node from the linked list:

`void delete(dllnode* target);`

###### steps involved:

1. Fix the pointers of the surrounding nodes to "skip over" target.
2. free target.

#### Notes:

- Linked lists, of both the singly- and doubly-linked varieties, support extremely efficient *insertion* and *deletion* of the elements.
    - In fact, these operations can be done in **constant time**.
- What's the downside? Remember how we had to find an element? We've lost the ability to randomly-access list elements.
    - Accessing a desired element may now take **linear time**.

