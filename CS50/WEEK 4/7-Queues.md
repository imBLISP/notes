# QUEUES	

https://www.youtube.com/watch?v=3TmUv1uS92s&list=PLhQjrBD2T381k8ul4WQ8SQ165XqY149WW&index=41



- A queue is a special type of structure  that can be used to maintain data in an organized way.
- This data structure is commonly implemented in one of two ways as an **array** or as a **linked list**.
- In either case, the important rule is that when data is added to the queue, it is tacked onto the end, and so if an element needs to be removed, the element at the front is the only element that can legally be removed.
    - First in, first out (FIFO)
- There are only two operations that may legally be performed on a queue.
    - **Enqueue**: Add a new element to the end of the queue.
    - **Dequeue**: Remove the oldest element from the front of the queue.

#### Array-based implementation:

```c
typedef struct _queue
{
	VALUE array[CAPACITY];
	int front;
	int size;
}
queue;

queue q;
q.front = 0;
q.size = 0; // if size becomes equal to capacity we cant add any more elements	
```

###### Enqueue: 

Add a new element to the end of the queue

- In the general case, `enqueue()` needs to:
    - Accept a pointer to the queue.
    - Accept data of type `VALUE` to be added to the queue.
    - Add that data to the queue at the end of the queue (no need to change the `front` bcuz the `front `is the oldest element in the queue).
    - Change the `size `of the queue (add 1 to the size).
    - `void enqueue(queue* q, VALUE data);`
    - Ex: `enqueue(&q, 28);`
    - store the value in array location  `front` + `size`
    - we eventually need to mod `&`  the `front` + `size` by `capacity` to wrap around the array.

###### Dequeue:

Remove the most recent element from the `front` of the queue (`front` means the oldest element).

- In the general case, `dequeue()` needs to:
    - Accept a pointer to the queue.
    - Change the location of the `front` of the queue (to the next oldest element OR +1).
    - Decrease the `size` of the queue.
    - Return the value that was removed from the queue.
    - `VALUE dequeue(queue* q);`
    - `int x = dequeue(&q);`

#### Linked list-based implementation

```c
typedef struct _queue
{
	VALUE val;
	struct _queue *prev;
	struct _queue *next;
}
queue;
```

we can also implement this in the form of a singly-linked list.

> Just make sure to always maintain pointers to the head **and** tail of the linked list! (probably global)

###### Enqueue:

- Dynanically allocate a new node;
- Set its `next` pointer to `NULL`, set its `previous` pointer to the tail;
- Set the tail's `next` pointer to the new node;
- Move the tail pointer to the newly-created node.
- `enqueue(tail, 10)` (adds 10 to the end of the list)

###### Dequeue:

- Traverse the linked list to its second element (if it exists);
- Free the head of the list;
- Move the head pointer to the (former) second element;
- Make that node's prev pointer point to `NULL`.
- `Dequeue(head);`