#DATA TYPES
---

Data Type| Description 
---------|----------
 `int` | take upto 4 bytes of memory ie 32 bits . from -2^31 to +2^31- 1 
 `unsigned  int`   | unsigned is used to double the positive range of the variables of that type , at the cost of disallowing any negative values. range : 0 to 2^32 - 1 
 `char` | store single character , 1 byte = 2^8 total combinations . ie range of characters = -128 to 127.0 to 127 are mapped to letters through ascii standard 
 `float` | real numbers . 4 bytes of memory. precision problem .  
 `double` | 8 bytes . double precision over float 
 `void` | not data type but a type. void return type means it doesnt return a value. void can be a parameter which means the function doesnt take any arguments 



####CS50 Library:

Data type | Description |
---------|----------|
 `bool` | boolean value only two distinct value . c doesnt have this datatype | 
 `string` | collections of characters| 
 `structs` | group integers and strings| 



#### Creating a datatype:

```c
int num1,num2,num3;  //this is called declaration 
num1 = 17;          //this is called assignment
int num1 = 17;     //this is called initialization
```
>unsigned, short, long, are qualifiers.