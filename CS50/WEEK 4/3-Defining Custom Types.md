# DEFINING CUSTOM TYPES

https://www.youtube.com/watch?v=v7MdPP2fyj4

- The C keyword `typedef` (typedefinition) provides a way to create a shorthand or rewritten name for data types.
- The basic idea is to first define a type in the normal way, then alias it to something else.

```c
typedef <old name> <new name>;

// example: we can just use byte everywhere we are using unsigned char.
// we rewrote the name from "unsigned char" to byte
typedef unsigned char byte;

// example: in CS40 library, this is how they created a string
typedef char* string;
```

- example:

```c
// define a struct car
struct car 
{
    int year;
    char model[10];
    char plate[7];
    int odometer;
    double engine_size;
};

// change the old name/datatype ie struct car to car_t
typedef struct car car_t;
```

- Defining a structure in the middle of typedef:

```c
typedef <old name> {define old name} <new name>;

typedef struct car
{
    int year;
    char model[10];
    char plate[7];
    int odometer;
    double engine_size;
}
car_t;

// variable declaration
car_t mycar;

// field accessing
mycar.year = 2011;
mycar.plate = "CS50";
mycar.odometer = 50505;
```

