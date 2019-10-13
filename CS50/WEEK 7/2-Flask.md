# FLASK

Python is not just used for command-line programming, though that's a mahor use case.

Python contains native functionality to support networking and more, enabling site backends to be written in Python.

Web frameworks make this process much easier, abstracting away the minutia of Python's syntax and providing helper functions.

Some of the mose popular include: Django, Pyramid, and Flask.

We use Flask in CS50 because it is lightweight for ease of use in CS50 IDE, while still being feature-rich.

We know that we can use HTML to build websites, but websites built using pure HTML suffer from a serious limitation.

Imagine we want to create a website that displays the current time in Cambridge, MA, displaying it to the latest minute.

```html
<html>
    <head>
        <title>Current Time in Cambridge</title>
    </head>
    <body>
        The current time in Cambridge is 14:08 <!--this time cannot change-->
    </body>
</html>
```

Websites that are pure HTML are completely static. The only way we can update the content of our pages is to manually open up our source files, edit and save, and then the next time the user visits or refreshes the page they'll get the content.

Incorporating Python into our code can make our code quite a bit more flexible and introduce a way for our pages to update or be dynamic without requiring our intervention.

**webpage that displays time in real time:**

```python
from flask import Flask
from datetime import datetime
from pytz import timezone

app = Flask(__name__)

@app.route("/")
def time():
    now = datetime.now(timezone('America/New_York'))
    return "The current data and time in Cambridge is {}".format(now)
```

It's pretty simple to get started using Flask within CS50 IDE.

We create a file generally called application.py and write the following

```python
from flask import Flask # we are importing the Flask class (classes are denoted by first letter capitalized)
```

After importing the Flask module, we need to initiate a Flask application.

```python
# we are creating a Flask application from the __name__ file
app = Flask(__name__) # __name__ is basically the name of the file
```

From there, it's just a matter of writing functions that define the behaviour of our application.

```python
# this is called applying a decorator
@app.route("/") # this refers to the index page
def index():
    return "You are at the index page!"

@app.route("/sample") # this is the sample page
def sample():
    return "You are on the sample page!"
```

The lines just added are known as "decorators". They are used, in Flask, to associate a particular function with a particular URL.

Decorators also have more general use in Python, but that goes beyond scope of CS50.

It's also quite straightforward to run our Flask application within CS50 IDE.

```
export FLASK_APP = application.py // FLASK_APP is a system variable and it will be stored in the memory of the IDE
	export FLASK_DEBUG=1 // (optional) 1 means true, ie if something goes wrong you will se it in the command line
		flask run // only type this is you have typed all three lines once
```

Data can be passed in via URLs, akin to using HTTP GET.

```python
@app.route("/show/<number>")
def show(number):
    return "You passed in {}".format(number)
```

Data can be passed in via HTML forms, as with HTTP POST, but we need to indicate that Flask should respond to HTTP POST requests explicitly.

```python
@app.route("/login", methods=['GET', 'POST'])
def login():
    if not request.form.get("username"):
    	return apology("must provide username")
```

We cound also vary the behaviiur of our function depending on the type of HTTP request received:

```python
@app.route("/login", methods = ['GET', 'POST'])
def login():
    if request.method == "POST":
        # do one thing
    else:
        # do a different thing

```

Flask has a number of functions withing its module that will be useful for application development.

So along with importing Flask from flask we can import these too:

- `url_for()`
- `Redirect()`
- `session()`
- `render_template()`

More information available at the Flask quick start guide:

`http://flask.pocoo.org/docs/0.12/quickstart/`

More information on using Jinja can be found at:

`http://jinja.pocoo.org/`

