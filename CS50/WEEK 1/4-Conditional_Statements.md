#CONDITIONAL STATEMENTS
---



###if statements:
```c
if (boolean -expression)
{
    //statement
}     
```



###if-else statements:
```c
if (boolean -expression)
{
    //first branch
}
else
{
    //second branch
}
```



###nested if-else statements:
* you can chain if-else statements.
* it goes from up to down.
* The statements are mutually exclusive. 
```c
if (boolean -expression)
{
    //first branch
}
else if (boolean -expression2)
{  
    //second branch                
}
else if (boolean -expression3)
{
    //third branch
}
else
{
    //fourth branch
}
```



###if statements and if-else statements:
* Only third branch and fourth branch are mutually exclusive(they depend on each other).
* The else statement only binds to the nearest if branch. 
```c
if (boolean-expr1)
{
    // first branch
}
if (boolean-expr2)
{
    // second branch           
}
if (boolean-expr3)
{
    // third branch
}
else
{
    // fourth branch
}

```



###Switch statements:
if you dont use break it will execute all the cases below it until it encounters another break.
```c
int x = GetInt ();
switch(x)
{
    case 1:
        printf("one \n");
        break;
    case 2:
        printf("two \n");
        break;
    case 3:
        printf("three \n");
        break;
    default:
        printf(sorry \n");
}

```



###if statements in one line:
* this is equivalent to a if else statement.
* if the boolean expr is true then  the value of x is 5 else its value is 6 .
* `?:` is also know as **ternery operator**

```c
int x = (expr) ? 5 : 6; 
```