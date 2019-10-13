#STACKS (data structure)

https://www.youtube.com/watch?v=hVsNqhEthOk&list=PLhQjrBD2T381k8ul4WQ8SQ165XqY149WW&index=47&t=0s

- We are talking about a stack data structure not a stack segment of memory.
- A stack is a special type of a structure that can be used to maintain data in an organized way.
- This data structure is commonly implemented in one of two ways: as an **array** or as a **linked list**.
- In either case, the important rule is that when data is added to the stack, it sits "on top", and so if an element needs to be removed, the most recently added element is the only element that can legally be removed.
    - *Last in, first out (LIFO)*
- There are only two operations that may legally be performed on a stack.
    - **Push:** Add a new element to the top of the stack.
    - **Pop**: Remove the most recently-added element from the top of the stack.

#### Array-based implementation

```c
typedef struct _stack
{
    // VALUE is a previously defined datatype and CAPACITY is a pound defined constant
    VALUE array[CAPACITY]; 
    int top;
}
stack;

// declaration
stack s;
```

- **Push:**

    In the general case, push( ) needs to:

    - Accept a pointer to the stack.
    - Accept data of type VALUE to be added to the stack.
    - Add that data to the stack at the top of the stack.
    - Change the location of the top of the stack.
    - Declaration: `void push(stack* s, VALUE data);`

```c
stack s;
s.top = 0;
push(&s, 28);
```

- **Pop:**

    In the general case, pop( ) needs to:

    - Accept a pointer to the stack.
    - Change the location of the top of the stack.
    - Return the value that was removed from the stack.
    - Declaration: `VALUE pop(stack* s)`

#### Linked list-based implementation

```c
typedef struct _stack
{
    VALUE val;
    struct _stack *next;
}
stack;
```

- just make sure to always maintain a pointer to the head of the linked list!
- To **push**, dynamically allocate a new node, set its next pointer to point to the current head of the list, then move the head pointer to the newly-created node.
- To **pop**, traverse the linked list to its second element (if it exists), free the head of the list, then move the head pointer to the (former) second element. 