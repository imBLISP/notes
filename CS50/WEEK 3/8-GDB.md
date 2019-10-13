# GDB

Fullform **GNU debugger**

#### Info:

- GDB (the **G**NU **D**e**b**ugger) is an amazingly powerful tool that we can use to root out glitches in out programs. 
- As a general rule, the output and interaction with GDB can be a bit idiosyncratic and cryptic.
    - Fortunately, we've taken steps to solve this problem!
- If you aren't using the graphical debugger, it's useful to know how to work through your program with GDB's command line interface. 

####How to use:

- To kick things off with GDB, type 
    `gdb <program name>`
- That will pull up the GDB environment. From there, the next two major commands you'll likely use (in order) are:
    - ` b [function name, line number]`
        Makes it so that once your program begins, it will run uninterrupted until it encounters the function with that name or hits that line number, at which point the program will pause execution and await further input.
    - `r [command-line arguments]`
        Runs the program with the command line arguments provided, if any.
- Some other commands:
    - `n`  OR `next` Will step forward one block of code.
    - `s` Will step forward one line of code. (step in the functions)
    - `p [variable]` Prints out the value of the variable given.
    -  `info locals` Prints out the value of all local variables.
    - `bt` Shows you the current point in the program. (backtrace, prints out the stack)
    - `q` Quits GDB.

