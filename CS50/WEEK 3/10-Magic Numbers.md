# MAGIC NUMBERS

- Some of the programs we've written in CS50 have some weird numbers thrown in there.
    - The height of Mario's pyramid is capped at 23, for example.
- What do those numbers mean? if someone looks at your program, is the meaning of 23 immediately obvious?
- Directly writing constants into our code is sometimes referred to as using **magic numbers**.

```c
card deal_cards(deck name)
{
    for(int i = 0; i < 52; i++)
    {
        // deal the card
    }
}
```

- We've got a magic number in here. Do you see what it is?
    - More importantly, do you see a potential problem here? 
        Particularly if this function is just one of manu in a suite of programs that manipulate decks of cards.

```c
card deal_cards(deck name)
{
    int deck_size = 52;
    for (int i = 0; i< deck_size; i++)
    {
        // deal the cards
    }
}
```

- This fixes one problem, but introduces another.
    - Even if glocally declared, what if some other function in our suite inadvertently manipulates deck_size. Could spell trouble.

- C provides a **preprocessor directive** (also called a macro) for creating symbolic constants.

```c
#define NAME REPLACEMENT
ex
#define PI 3.14159265
ex2
#define COURSE "CS50"
// this replaces every PI in your code with 3.14159265
```

- At the time your program is compiled, `#define` goes through the code and replaces `NAME` with `REPLACEMENT`
    - if `#include` is similar to copy/paste, then #define is analogous to find/replace.
    - The `NAME` is always in **capital** by convention.

```c
#define DECKSIZE 52

Card deal_cards(deck name)
{
    for (int i = 0; i < DECKSIZE; i++)
    {
        // deal the card
    }
}
```

- This is a better solution.

