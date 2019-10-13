#LOOPS
---



###Infinite Loop:
The lines of code bw the curly brackets will execute repeatedly from top to bottom unless we break out of it or otherwise kill the program. 
```c
while (true)
{

}
```



###While Loop:
* executes repeatedly in order from top to bottom until the boolean-expr evaluates false
* **Used when you want a loop to repeat an unknown number of times, and possibly not at all.**
```c
while (boolean_expr)
{

}
```



###Do-While Loops:
* executes all lines of code in the curly brackets atleast once.
* **used when you want a loop to repeat an unknown number of times but atleast once. ex asking user for input you want to display the message "give input" atleast once.**
```c
do 
{

}
while (boolean_expr)
```



###For Loops:
* used for repeating something a specific number of times , in this example 10 times.
* used to loop a descrete number of times.
* i only exists inside the loop.
process: start>expr>code>increment>expr>code ....
* process of for loops: 
    1. the counter variables is set (here `i`).
    2. the boolean expression is checked.
    3. the counter variable is incremented and then the boolean expression is checked again
```C
for (start; expr; increment)
{

}

```
```c
for (int i = 0; i < 10; i++)
{
    //example loop
}
```



>* `i++` means that will increment after executing the code in the curly brackets once.
>* `++i` means that `i` will increment before executing the loop.

