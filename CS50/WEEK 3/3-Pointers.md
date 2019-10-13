# POINTERS

---

- Pointers provide an alternative way to pass data between functions .

    - Recall that up to this point, we have passed all data **by value**, with one exception.
    - When we pass data by value, we only pass a copy of that data.

- if we use pointers instead, we have the power to pass the actual variables itself.

    - that means that a change that is made in one function <u>can</u> impact what happens in a different function.
    - previously, this wasn't possible!

- Before we dive into what pointers are and how to work with them, it's worth going back to basics and have a look at our computer's memory.

- Every file on your computer  lives on your hard disk drive, be it a hard disk drive (HDD) or a solid-state drive (SSD).

- Disk drives are just storage space; we can't directly work there. Manipulation and use of data can only take place in RAM, so we have to move data there.(ram is cleared when you turn off your computer)

- Memory is basically a huge array of 8-bit wide bytes. 

    - 512 MB, 1GB, 2GB, 4GB... 
    - cs50 ide is a ==64bit or x64== system ie every adress is 8 bytes.
    - in a ==32bit or x32== machine every adress is 4 bytes (32bits).

- | Data Type                          | Size(in Bytes)                          |
    | ---------------------------------- | --------------------------------------- |
    | int                                | 4                                       |
    | char                               | 1                                       |
    | float                              | 4                                       |
    | double                             | 8                                       |
    | Long long                          | 8                                       |
    | String(cs50.h)  OR char*/int * etc | 4 or 8 <br />(depending on the machine) |

    Back to this idea of memory as a big array of byte-sized cells.

- Recall from our discussion of arrays that they not only are useful for storage of information but also for so-called **random access**.

    - We can access individual elements of the array by indicationg which index location we want.

- Similarly, each location in memory has an **address**. //little and big endianss

- There's only one critical thing to remember as we start working with pointers:

    - **POINTERS ARE JUST ADDRESSES**

- Pointers are adresses in memory where variables live.

- A **pointer**, then, is a data item whose

    - *value* is a memory adress
    - *type* describes the data located at that memory adress 

- As such, pointers allow data structures and/or variables to be shared among functions.

- Pointers make a computer environment more like the real world.

- The simplest pointer available to us in C is the **NULL** pointer.

    - As you might expect, this pointer points to nothing (a fact actually come in handy!)

- When you create a pointer and you don't set its value immediately, you should **always** set the value of the pointer to NULL..

- You can check whether a pointer is NULL using the equality operator `==`.

- Another easy way to create a pointer is to simply **extract** the adress of an already existing variable. We can do this with the adress **extraction operator** `&`.

- if `x` is an int-type variable, then `&x` is a pointer-to-int whose value is the address of x.

- if `arr` is an array of doubles, then `&arr[i]` is a pointer-to-double who's value is the adress of the `i`th element of `arr`.

    - An array's name, then, is actually just a pointer to its first element - you've been working with pointers all along!

- The main purpose of a pointer is to allow us to modify or inspect the location to which it points.

    - We do this by **dereferencing** the pointer.(ie we go to the reference and change the value there.)

- If we have a pointer-to-char called `pc` then `*pc` is the data that lives at the memory adress stored inside the variable `pc` .

- used in this context, `*` is known as **dereference operator**.

- It "goes to the reference" and accesses the data at that memory location, allowing you to manipulate it at will.

- This is just like visiting your neighbor. Having their address isn't enough. You need to <u>go to</u> the address and only then can you interact with them.

- Can you guess what might happen if we try to dereference a pointer whose value is NULL?

    - Segmentation fault

- Surprisingly, this is actually good behavior! It defends against accidental dangerous manipulation of unknown pointers.

    - That's why we recommend you set your pointers to NULL immediately if you aren't setting them to a known, desired value.

- `int* p;`

    - the value of `p` is an address.
    - We can dereference `p` with the `*` operator.
    - If we do, what we'll find at that location is an `int`.

- One more annoying thing with those `*`s. They're an important part of both the type name **and ** the variable name.

    - Best illustrated with an example.
    - `int* px, py, pz;`(here you get a pointer px, a integer py, and a integer pz)
    - `int* pa, *pb, *pc;`(here you woll get three pointers pa, pb, pc)

- All pointers are 4 or 8 bytes depending on what type of machine it is.