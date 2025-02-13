# CSS

https://www.youtube.com/watch?v=Ub3FKU21ubk

CSS (*Cascading style sheets*) is another language we use to when constructing websites.

- If HTML is used to organize the content that we aim to display on our pages, then CSS is the tool we use to customize our website's look and feel.

Like HTML, CSS is not a programming language; it lacks logic. Rather, it is a styling language and its syntax describes how certain attributes of HTML elements should be modified.

```css
body
{
    background-color: blue;
}
```

A style sheet is constructed by identifying a *selector* (in the last example, body) and then an open curly brace to indicate the beginning of the style sheet for that selector.

In between the cruly brace you place a list of key-value pairs of style properties and values for those properties, each *declaration* ending with a semicolon.

Then a closing curly brace terminates the style sheet.

**Common CSS properties**

- `border: style color width`
    - Applies a border of the specified color, width and style (e.g., dotted, dashed, solid, ridge…).
- `background-color: [keyword | #<6-digit hex>]`
    - Sets the background color. Some colors are pre-defined in CSS.
- `color: [keyword | #<6-digit hex>]`
    - Sets the foreground color (usually text).
- `font-size: [absolute size | relative size]`
    - Can use keywords (xx-small, medium…), fixed points (10pt, 12pt…), percentage (80%, 120%), or base off the most recent font size (smaller, larger).
- `font-family: [font name | generic name]`
    - Certain "web safe" fonts are pre-defined in CSS.
- `text-align: [left | right | center | justify]`
    - For displaying text.

Your selectors don't have to apply only to HTML tag categories. There also exist ID selectors and class selectors.

A **tag** selector will apply to all elements with a given HTML tag

```css
h2
{
	font-family: times;
	color: #fefefe;
}
```

An **ID** selector will apply only to an HTML tag with a unique identifier.

```css
#unique
{
    border: 4px dotted blue;
    text-align: right;
}
```

A **class** selector will apply only to those HTML tags that have been given identical "class" attributes.

```css
.students
{
	background-color: yellow;
	opacity: 0.7;
}
```

Style sheets can be written directly into your HTML.

- Place them within `<style>` tags within your page's head.

Style sheets can also be written as separate CSS files and then linked in to your document,

- Use `<link>` tags within you page's head to accomplish this.

