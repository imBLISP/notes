# DOM

Document object model

As we've seen, JavaScript objects are incredibly fliexible, and can contain various fields, even when those fields are other objects.

The *document object* is one way of employing this paradigm, whereby that object organizes the entire contents of a web page.

By organizing an entire page into a JavaScript object, we can manipulate the page's elements programmatically.

```html
<html>
    <head>
        <title>Hello, world</title>
    </head>
    <body>
        <h2>
            Here's my page
        </h2>
        <p>
            World, hello
        </p>
        <a href="test.html">Link</a>
    </body>
</html>
```

Video: 2:27

The document object itself, as well as all of the objects contained within it, have a number of *properties* and a number of *methods* that can be used to drill down to a very specific piece of your website.

By resetting those properties or calling certain methods, the contents of our web pages can change without us needing to refresh the page.

Video 3:43

#### DOM Properties

| DOM Property |                         Description                          |
| :----------: | :----------------------------------------------------------: |
| `innerHTML`  |          Holds the HTML inside a set of HTML tags.           |
|  `nodeName`  |     The name of an HTML element or element's attribute.      |
|     `id`     |            The "id" attribute of an HTML element.            |
| `parentNode` |       A reference to the node one level up in the DOM.       |
| `childNodes` | An array of references to the nodes one level down in the DOM. |
| `attributes` |         An array of attributes of an HTML elements.          |
|   `style`    |  An object encapsulating the CSS/HTML styling of an element  |

#### DOM Methods

|         DOM Methods         |                         Description                          |
| :-------------------------: | :----------------------------------------------------------: |
|    `getElementById(id)`     | Gets the element with the given ID below this point in the DOM. |
| `getElementsByTagName(tag)` | Gets all elements with the given tag below this point in the DOM. |
|     `appendChild(node)`     |       Add the given node to the DOM below this point.        |
|     `removeChild(node)`     |        Remove the specified child node from the DOM.         |

If we start from `document`, we can get to any piece of our web page that we choose, through careful use of DOM properties and methods.

#### jQuery

Because DOM manipulation is so common with JavaScript, and because the JavaScript to do so can get quite lengthy, people wanted alternatives.

jQuery is a popular open-source library, released in 2006, that is designed to simplify client-side scripting (such as DOM manipulations).

**javascript:**

```javascript
document.getElementById('colorDiv').style.backgroundColor = 'green'
```

**jQuery**

```
$('#colorDiv').css('background-color', 'green');
```

Video: 13:31

`https://api.jquery.com`