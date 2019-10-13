# PYTHON

Python is an example of a very commonly-used modern programming language.

- C was  first released in 1972, Python in 1991.

Python is an excellent and versatile language choice for making complex C operations much simpler.

- String manipulation
- Networking

Fortunately, Python is heavily inspired by C (its primary interpreter, *Cpython*, is actually written in C) and so the syntax should be a shallow learning curve.

To start writing Python, open up a file with the .py file extension.

Unlike a C program, which typically has to be compiled before you can run it, a Python program can be run without explicitly compiling it first.

Important note: In CS50, we teach **Python 3.** (Not Python 2, which is also still fairly popular.)

#### Variables 

Python variables have two big differences from C.

- No type specifier.
- Declared by initialization only.
- Python statements dont end with semicolons!

###### C:

```c
int x = 54;
string phrase = "This is CS50";
```

###### Python:

```python
x = 54

phrase = "This is CS50"
# OR
phrase = 'This is CS50'
```

#### Conditionals

All of the old favourites from C are still available for you to use, but they look a little bit different now.

###### C:

```c
// if statements
if (y < 43 || z == 15)
{
    // code goes here
}

// if else statements
if (y < 43 && z == 15)
{
    // code goes here
}
else 
{
    
}

// else if statements
if (coursenum == 50)
{
    // code block 1
}
else if (coursenum != 51)
{
    // code block 2
}

// ternery operator
char var = get_char();
bool alphabetic = isalpha(var) ? true : false;
```

###### Python:

```python
if y < 43 or z == 15:
    # code goes here

# if else statements
if y < 43 and z == 15:
    # code block 1
else: 
    # code block 2

# else if statements
if coursenum == 50:
    # code block 1
elif not coursenum == 51:
    # code block 2
    
# ternery operator
letters_only = True if input().isalpha() else False
```

#### Loops

Two varieties: `while` and `for`

###### C:

```c
// while loop
int counter = 0;
while (counter < 100)
{
	printf("%i\n", counter);
	counter++;
}

// for loop
for (int x = 0; x < 100; x++)
{
    printf("%i\n", x);
}

// for loop
for (int x = 0; x < 100; x += 2)
{
    printf("%i\n", x);
}
```

###### Python:

```python
# while loop
counter = 0
while counter < 100:
    print(counter)
    counter += 1

# for loop
for x in range(100):
    print(x)

# for loop
for x in range(0, 100, 2): # 0 is start point, 100 is end point, and 2 is increment value
    print(x)
```

#### Arrays (called *lists* in Python)

Here's where things really start to get a lot better than C.

Python arrays (more appropriately known as **lists**) are **<u>not</u>** fixed in size; they can grow or shrink as needed, and you can always tack extra elements onto your array and splice things in and out easily.

###### Declaring a list

```python
nums = [] # empty list/array
nums = [1, 2, 3, 4] # explicitely created list/array
nums = list() # empty list
```

###### List Comprehension

```python
nums = [x for x in range(500)] # using a for loop to generate a list of numbers and assign the list to nums 
```

###### Adding to an existing list

```python
nums = [1, 2, 3, 4]
nums.append(5) # add 5 to the end
nums.insert(4, 5) # add 5 in the fourth position
# attach one list to the end of another list
nums[len(nums):] = [5] # the nums list from position 4 onwards(which is the length of nums) gets the list to it's right assigned to it

```

`len(nums)` gives the length of any arbitrary list

#### Tuples

Python also has a data type that is not quite like anything comparable to C, a *tuple*.

Tuples are ordered, immutable sets of data; they are great for associating collections of data, sort of like a struct in C, but where those values are unlikely to change.

Here is a list of tuples:

```python
presidents = [("George Washington", 1789), 
              ("Johm Adams", 1797), 
              ("Thomas Jefferson", 1801), 
              ("James Madison", 1809)]

```

This list is iterable as well:

```python
for prez, year in presidents:
    print("In {1}, {0} took office".format(prez, year)) # we are using them in reverse order

```

#### Dictionaries

Python also has built in support for **dictionaries**, allowing you to specify the list indices with words or phrases (*keys*), instead of integers, which you were restricted to in C.

```python
pizzas = {
    "cheese": 9,
    "pepperoni": 10,
    "vegetable": 11,
    "buffalo chicken": 12,
}
# cheese etc are keys and the numbers are the values 

# changing a value 
pizzas["cheese"] = 8

if pizzas["vegetable"] < 12:
    #do something
    
# adding new keys to the dictionary
pizzas["bacon"] = 14
```

But this creates somewhat new problem… how do we iterate through a dictionary? We don't have indexes ranging from [0, n-1] anymore.

#### Loops (redux)

The for loop in python is extremwly flexible!

```python
# iterating over all the keys in a dictionary
for pie in pizzas:
    #use pie in here as a stand-in for "i"
    
# iterating over all the keys and the values in a dictionary
for pie, price in pizzas.items():
    print(price)
    # you have to use pizzas.items because we are not using just the keys
    # the pizzas.items notation changes dictionary to a list
    
OUTPUT
12
10
9
11
# side effect of changing dictionaries to lists is that you dont(mostly) get the output in the specified order

# printing both price and pie:
for pie, price in pizzas.items():
    print("A whole {} pizza costs ${}".format(pie, price))
    # order doesnt matter so we can ignore to specify numbers inside the curly braces
```

#### Printing and variable interpolation

format gives one way to interpolate variables into our printed statements in a very `printf`-like way, but there are others.

```python
print("A whole {} pizza costs ${}".format(pie, price))
# OR
print("A whole {1} pizza costs ${0}".format(pie, price))
# to print in reverse order
```

```python
print("A whole" + pie + "pizza costs $" + str(price)) # str transforms to string
```

```python
# you may see this, but avoid; deprecated in python 3
print("A whole %s pizza costs $#2d" % (pie, price))
```

#### Functions

Python has support for functions as well. Like variables, we don't need to specify the return type of the function (because it doesn't matter), nor the data types of any parameters (ditto).

All functions are introduced with the `def` keyword.

- Also, no need for `main`; the interpreter reads from top to bottom!

- if you wish to define `main` nonetheless (and you might want to!), you must at the very end of your code have: 

    ```python
    if __name__ == "__main__":
    	main()
    ```

```python
def square(x):
    return x ** 2 # ** is a exponentiation operator it basically means x^2
```

#### Objects

Python is an *object-oriented* programming language.

An object is sort of analogous to a C structure.

C structures contain a number of *fields*, which we might also call *properties*.

- But the properties themselves can not ever stand on their own.

- ```c
    // for example
    struct car
    {
        int year;
        char *model;
    }
    
    // i can say this
    struct car herbie;
    herbie.year = 1963;
    herbie.model = "Beetle";
    
    // but i can't say this
    struct car herbie;
    year = 1963;
    model = "Beetle";
    ```

Objects, meanwhile, have properties but also *methods*, or functions that are inherent to the object, and mean nothing outside of it. You define the methods inside the object also.

- Thus, properties and methods don't ever stand on their own.

You dont pass objects into a function `function(object)` is not valid.

We call methods on objects `object.method()`

You define a type of object using the `class` keyword in python.

Classes require an initialization function, also more-generally known as a *constructor*, which sets the starting values of the properties of the object.

In defining each method of an object, `self` should be its first parameter, which stipulates on what object the method is called.

`self` will always be a parameter

```python
class student():
    
    def __init__(self, name, id): # this is the contstructor
        self.name = name # self just means Student
        self.id = id
        
	def changeID(self, id):
        self.id = id
        
	def print(self):
        print("{} - {}".format(self.name, self.id))
        
# creating a new object
jane = student("Jane", 10)
jane.print()
jane.changeID(11)
jane.print()

# output
Jane - 10
Jane - 11
```

#### Style

if you haven't noticed, good style is **<u>crucial</u>** in Python.

Tabs and indentation actually matter in this language, and things will not work the way you intend for them to if you disregard styling!

Good new? No more curly braces to delineate blocks! 

- Now they just are used to declare dictionaries

#### Including files

Just like C programs can consist of multiple files to form a single program, so can Python programs tie files together.

```python
# in C
#include <cs50.h>

# in Python
import cs50 

# Using cs50
cs50.get_Int() # we have to use the dot operator because cs50 is basically a class and get_int is a method in that class
               # This is also called invoking a method
```

Calling a method through a dot operator is know as **invoking** a method.

Libraries are called *modules*

Python programs can be prewritten in .py files, but you can also write and test short Python snippets using the Python interpreter from the command line.

All that is required is that the Python interpreter is installed on the system you wish to run your Python programs on.

To run your Python program through the Python interpreter at the command-line, simply type:

`python <file>`

And your program will run throught the interpreter, which will execute everything inside of the file, top to bottom.

You can alsomake your programs look a lot more like C programs when they execute by adding a **shebang** to the top of your python files, which automatically finds and executes the interpreter for you.

```python
#!/usr.bin.env python3
```

If you do this you need to change the **permissions** on your file as well using the Linux command `chmod` as follows: 

`chmod a+x <file>`

the main difference between dictionaries and lists is that items in dictionaries are accessed via keys and not via their position. 

