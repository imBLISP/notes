# ARRAYS

####Declaration:

`type name[size];`

- The type is what kind of variable each element  of the array will be.
- the name is what you want to call your array.
- the size is how many elements you would like your array to contain. it starts from
    1 not 0.

#### Initialization:

######Instantiation Syntax:

```c
bool thruthtable[3] = { false, true, true };
```

```C
bool thruthtable[] = { false, true, true };
```

- You can ommit the size.
- First and second both are valid.

###### Individual element syntax:

``` C 
bool truthtable[3];
thruthtable[0] = false;
thruthtable[1] = true;
thruthtable[2] = true;
```

#### Multidimensional Array:

```c
bool battleship[10][10];
```

- Any number or dimensions.

#### Properties:

- it is a ==data structure==.
- hold values of ==same date types== at ==contiguous== memory locations.
- partitions of array are called elements.
- elements can store a certain amount of data.
- each partition has its own index number.
- array can consist of more than a single dimension. You can have as many size
    specifiers as you wish.
- while we can treat individual variables, we cannot treat entire array themselves as
    variables.
- we cannot, for instance, assign one array to another using the assignment
    operator. That is not legal C.
- instead, we must use loop to copy over the elements one at a time.
- most variables in c are ==passed by value== in function calls.ie
    the collie receives the copy of the variable.
- Arrays do not follow this rule. Rather, they are ==passed by reference==. The collie receives the
    actual array, not the copy of it.
- Multidimensional array : can think of it as 10x10 grid of cells. but in memory its really just a 100 element one dimensional array. referencing to the above example.
- multidimensional arrays are great abstractions to help visualize game boards or other complex
    representations.

