# MVC

https://www.youtube.com/watch?v=Fr4P6FkZUTE&list=PLhQjrBD2T381k8ul4WQ8SQ165XqY149WW&index=37

MVC is a programming paradigm that is very commonly-used for web design.

It is used to *abstract* away certain details from the user that are not necessary or are uninteresting for them to see, but that are essential for your site to work properly.

- The primary motivation for this is **data security**

#### Model

This is where the important data for the site lives, and it may be updated, referenced, or the like as part of the user experience.

#### View

These are the pages the user sees when they are interacting with you sitem usually based on interaction with the model.

#### Controller

This is where the so-called *business logic* of your site lives. Users may submit information to the controller, which will then decide what to present to the user. 

Video: 3:20

Adhering to this paradigm means that you separate

- the data required for you website
- from the logic (PHP) that implements your website's functionality
- from the simple aesthetics and page templates

This also means that  you can make files you need in order to run your sites but that will never be accessed by users (for example, anything that you might `require_once()`) not publicly accessible.

- Ever received a "403 Forbidden" error?

To change the permissions of a file to make it accessible (or not) to the public, you need to befriend a possibly-new Linux command, `chmod`.

`chmod <permissions> <file(s)>`

`chmod 600 helpers.php`

`chmod a+x includes/`

This so-called *octal numbers* permissions scheme assigns permissions to three categories of users simultaneously

`chmod 711 file ` 

`7` is what you can do, `1` is what your group can do, `1` is what the world can do

This would, for example, assign you the right to read, write, and execute the file, and would allow others (specifically, your group and the world) to only execute the file.

| Octal # | Read (r) | Write (w) | Execute (x) |
| :-----: | :------: | :-------: | :---------: |
|    0    |    NO    |    NO     |     NO      |
|    1    |    NO    |    NO     |     YES     |
|    2    |    NO    |    YES    |     NO      |
|    3    |    NO    |    YES    |     YES     |
|    4    |   YES    |    NO     |     NO      |
|    5    |   YES    |    NO     |     YES     |
|    6    |   YES    |    YES    |     NO      |
|    7    |   YES    |    YES    |     YES     |

here `NO` and `YES` can be translated to 0 and 1 and we call them octal because there are eight different possibilities to arrance them (3 bit)

The so-called *symbolic* permissions scheme also can assign permissions to three categories of users simultaneously, but is typically best used to apply (or remove) a position across the board.

`chmod a+x file`

This would, for example, **add** (+) (or maintain) the right to **execute**(x) the file to **all**(a) three categories.

| Reference | Class  |
| :-------: | :----: |
|     a     |  all   |
|     g     | group  |
|     o     | others |
|     u     |  user  |

| Mode |  Description   |
| :--: | :------------: |
|  r   |  read access   |
|  w   |  write access  |
|  x   | execute access |

| Operation |    Description    |
| :-------: | :---------------: |
|     +     |     add perm      |
|     -     |    remove perm    |
|     =     | exactly this perm |

To check the permissions of a file, you can run the `ls` command with which you're probably quite familiar, with a small tweak, adding the `-l` flag.

`username@ide50:~/workspace $ ls -l`

Output :

```
total 8
drwx-w---- 2 ubuntu ubuntu 4096 Oct 30 00:58 php/
drwx-w---- 3 ubuntu ubuntu 4096 Oct 30 00:55 php-webdev/
-rw------- 1 ubuntu ubuntu   28 Oct 30 01:01 test.php
```

`rwx`

means that the permissions that i have

`-w` 

are the permissions your group has

there is not a third parameter so the world cannot perform any operation on the server

`d`, `-`

d means directories and - means files

