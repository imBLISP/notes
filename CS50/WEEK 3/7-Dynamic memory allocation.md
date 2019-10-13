# DYNAMIC MEMORY ALLOCATION

---

- We've seen one way to work with pointers, namely pointing a pointer variable to another variable that already exists in our system.

    - This requires us to know exactly how much memory our system will need at the moment our program is compiled.

- What if we **don't** know how much memory we'll need at compile-time? How do we get access to new memory while our program is running?

- We can use pointers to get access to a block of **dynamically-allocated memory** at runtime.

- Dynamically allocated memory comes from a pool of memory known as **heap**.

- prior to this point, all memory we've been working with has been coming from a pool of memory known as **stack**.

- static-ly allocated memory(ex `int x = 10;`) comes from stack and dynamically allocated memory comes from heap.

    |                             Text                             |
    | :----------------------------------------------------------: |
    |                       initialized data                       |
    |                      uninitialized data                      |
    | heap<br />                                                                                     \|<br />                                                                                     \|<br />                                                                                     \|<br />                                                                                     V<br /><br /><br />                                                                                     ^<br />                                                                                     \|<br />                                                                                     \|<br />                                                                                     \|<br />                                                                                  stack |
    |                    Environment variables                     |

- We get this dynamically-allocated memory by making a call to the C standard library function `malloc()`, passing as its parameter the number of bytes requested.

- After obtaining memory for you (if it can), `malloc()` (`stdlib.h`) will return a pointer to that memory.

- What if `malloc()` **cant** give you memory? it'll hand you back NULL.

    ```c
    // statically obtain an integer
    int x;
    
    // dynamically obtain an integer
    int *px = malloc(4); // we can use sizeof(int) rather than 4 here
    ```

    ```c
    // get an integer from the user
    int x = get_int();
    
    // array of floats on the stack
    float stack_array[x];
    
    // array of floats on the heap
    float* heap_array = malloc(x * sizeof(float));
    ```

- Here's the trouble: Dynamically-allocated memory is not automatically returned to the system for later use when the function in which it's created finishes execution.

- Failing to return memory bakc to the system when you're finished with it results in a **memory leak** which can compromise your system's performance.

- When you finish working with dynamically-allocated memory, you must `free()` it.

    ```c
    char* word = malloc(50 * sizeof(char));
    
    // do stuff with word
    
    // now we're done working with that block
    free(word);
    ```

- Three Golden Rules:

    - Every block of memory that you `malloc()` must subsequently be `free()`d.
    - Only memory that you `malloc()` (dynamically allocate) should be `free()` d.
    - Do not `free()` a block of memory more than once.

- https://www.youtube.com/embed/xa4ugmMDhiE?autoplay=1&rel=0

- Watch last part.

