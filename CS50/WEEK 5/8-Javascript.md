# JAVASCRIPT

​	

Like PHP, JavaScript is a modern programming language that is derived from the syntax at C.

It has been around just about as long as PHP, also having been invented in 1995.

JavaScript, HTML, and CSS make up the three languages defining most of the user experience on the web.

To start writing JavaScript, open up a file with the .js file extension.

No need for any code delimiters like we had in PHP. Our website will know that our file is JavaScript because we’ll explicitly tell it as much in an HTML tag.

Unlike PHP which runs *server-side*, JavaScript applications run client-side, on your own machine.

#### Including JavaScript in your HTML

Just like CSS with `<style>` tags, you can directly write your JavaScript between `<script>` tags.

Just like CSS with `<link>` tags, you can write your JavaScript in separate files and link them in by using the `src` attribute of the `<script>` tag.

#### Variables

JavaScript variables are similar to Python variables.

- No type specifier.
- When a local variable is first declared, preface with the `var` keyword.

#### Conditionals 

All of the old favourites from C are still available for you to use.

#### Loops

All of the old favourites from C are still available for you to use.

#### Functions

All functions are introduced with the `function` keyword.

JavaScript functions, particularly those bound specifically to HTML elements, can be `anonymous` - you don't have to give them a name!

- We'll revisit anonymity a little later, and we'll revisit "binding to HTML elements" in the video on the Document Object Model.

#### Arrays

Declaring an array is pretty straightforward.

`var nums = [1, 2, 3];`

`var mixed = [1, true, 3,333, 'five'];`

#### Objects

JavaScript has the ability to behave in a few different ways, but in particular it can behave as an *object-oriented* programming language.

An object is sort of analogous to C structure.

C structures contain a number of *fields* or members, which we might also call *properties.*

- But the properties themselves can not ever stand on their own.

```c
// structure
struct car
{
    int year;
    char model[10];
}

// We can say
struct car herbie;
herbie.year = 1963;
herbie.model = "Beetle";

// But we can't say
year = 1963;
model = "Beetle";
```

Objects, meanwhile, have properties but also *methods*, or functions that are inherent to the object, and mean nothing outside of it.

- Thus, like properties can methods not ever stand on their own.

In c: `function(object);`
In oop: `object.function();`

The fields and methods of an object are similar in spirit to the idea of a dictionary, with which we're familiar from python.

`var herbie = {year : 1963, model: 'beetle'};`

#### Loops

How do we iterate across all of the key-value pairs of an object (or indeed, all of the elments of an array?

```javascript
for (var key in object)
{
    // Use object[key] in here
}

for (var key of object)
{
    // Use key in here
}
```

#### Printing and variable interpolation

```javascript
console.log(wkArray[day] + ' is day number ' + (parseInt(day) + 1) + ' of the week!');
```

#### Functions(redux)

Arrays are a special case of an object (in fact, *everything* in JavaScript is a special case of an object), and has numerous methods that can applied to them:

- `array.size()`, `array.pop()`, `array.push(x)`, `array.shift();`

There is also a method for arrays called `map()`, which can be used to apply a function to all elements of an array

- A great situation to use an *anonymous function*

#### EVENTS

An *event* in HTML and JavaScript is a response to user interaction with the web page.

- A user clicks a button, a page has finished loading, a user has hovered over a portion of the page, the user typed in an input field.

JavaScript has support for *event handlers*, which are callback functions (https://www.geeksforgeeks.org/javascript-callbacks/) that respond to HTML events.

- Many HTML elements have support for events as an attribute.

We can write a generic event handler in JavaScript, creating an *event object*, that will tell us which of these two buttons was clicked.