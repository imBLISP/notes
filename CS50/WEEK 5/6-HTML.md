# HTML

https://www.youtube.com/watch?v=YK78KhMf7bs

HTML (*Hypertext Markup Language*) is a fundamental component of every website.

HTML is a language, but it is <u>not</u> a programming language. It lacks concepts of variables, logic, functions, and the like.

Rather, it is a *markup language*, using angle-bracket enclosed tags to semantically define the structure of a web page, causing the plain text inside of sets of tags to be interpreted by web browsers in different ways.

```html
<html>
    <head>
        <title>
            Hello, world
        </title>
    </head>
    <body>
        World, hello
    </body>
</html>
```

Notice how the markup allows us to convey extra information about the text we've written.

There are over 100 HTML tags, and lots of great resources online to find them. We won't cover them all here.

Another interesting way to learn about HTML tags is to view the source of a website you frequent by opening your browser of choice's developer tools.

**Common HTML tags:**

- `<b>`, `</b>`
    - Text between these tags will be rendered in **boldface** by the browser.
- `<i>`, `</i>`
    - Text between these tags will be rendered in *italics* by the browser.
- `<u>`, `</u>`
    - Text between these tags will be rendered <u>underlined</u> by the browser.
- `<p>`, `</p>`
    - Text between these tags will be rendered as a paragraph by the browser, with space above and below.
- `<hX>, </hX>`
    - X = 1, 2, 3, 4, 5 or 6
    - Text between these tags will be rendered as an X-level section header.
- `<ul>`, `</ul>`
    - Demarcate the beginning and end of an unordered (bulleted) list.
- `<ol>`, `</ol>`
    - Demarcate the beginning and end of an ordered (numbered) list.
- `<li>`, `</li>`
    - Demarcate list items with and ordered or unordered list.
- `<table>`, `</table>`
    - Demarcate the beginning and end of a table definition.
- `<tr>`, `</tr>`
    - Demarcate the beginning and end of a row withing a table.
- `<td>`, `</td>`
    - Demarcate the beginning and end of a column withing a row withing a table.
- `<form>`, `</form>`
    - Demarcate the beginning and end of an HTML form.
- `<div>`, `</div>`
    - Demarcate the beginning and end of an arbitrary HTML page division.
- `<input name=X type=Y />` (self closing tag)
    - Define a field within an HTML form. X is a unique identifier for that field, Y is what type of data it accepts.
- `<a href=X>`, `</a>`
    - Creates a hyperlink to web page X, with the text between the tags rendered and function as the <u>link text</u>.
- `<img src=X ... />`
    - Another self-closing tag for displaying an image located at X, with possible additional *attributes* (such as specifying width and height).
- `<!DOCTYPE html>`
    - Specific to HTML5, lets the browser know that's the standard you're using.
- `<!--,-->`
    - Demarcate the beginning and end of an HTML comment.

Beyond the tags as explained here, each can also have multiple *attributes* that slightly modify the tag.

- For example, you can usually add and id=X attribute, to uniquely identify a tag within an overall page.

It is important that the HTML you write be will-formed. Every tag you open should be closed (unless it is a self-closing tag), and tags should by closed in reverse order of when they were opened.

Unlike C, your HTML will not necessarily fail with syntax errors if not well-formed, so it's up to you to be vigilant.

Because it can be an arduous tasl to investigate this, be sure to use onlin HTML validators to help!







