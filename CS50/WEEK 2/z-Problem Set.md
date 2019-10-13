# 2PROBLEM SET 2

---



# Caesar Cipher 

## Et tu?

Supposedly, Caesar (yes, that Caesar) used to “encrypt” (i.e., conceal in a reversible way) confidential messages by shifting each letter therein by some number of places. For instance, he might write A as B, B as C, C as D, …, and, wrapping around alphabetically, Z as A. And so, to say HELLO to someone, Caesar might write IFMMP. Upon receiving such messages from Caesar, recipients would have to “decrypt” them by shifting letters in the opposite direction by the same number of places.

The secrecy of this “cryptosystem” relied on only Caesar and the recipients knowing a secret, the number of places by which Caesar had shifted his letters (e.g., 1). Not particularly secure by modern standards, but, hey, if you’re perhaps the first in the world to do it, pretty secure!

Unencrypted text is generally called *plaintext*. Encrypted text is generally called *ciphertext*. And the secret used is called a *key*.

hot toTo be clear, then, here’s how encrypting `HELLO` with a key of 1 yields `IFMMP`:

| plaintext    | H    | E    | L    | L    | O    |
| ------------ | ---- | ---- | ---- | ---- | ---- |
| + key        | 1    | 1    | 1    | 1    | 1    |
| = ciphertext | I    | F    | M    | M    | P    |

More formally, Caesar’s algorithm (i.e., cipher) encrypts messages by “rotating” each letter by *k* positions. More formally, if *p* is some plaintext (i.e., an unencrypted message), *pi* is the *ith* character in *p*, and *k* is a secret key (i.e., a non-negative integer), then each letter, *ci*, in the ciphertext, *c*, is computed as

ci = (pi + k) % 26

wherein `% 26` here means “remainder when dividing by 26.” This formula perhaps makes the cipher seem more complicated than it is, but it’s really just a concise way of expressing the algorithm precisely. Indeed, for the sake of discussion, think of A (or a) as 0, B (or b) as 1, …, H (or h) as 7, I (or i) as 8, …, and Z (or z) as 25. Suppose that Caesar just wants to say Hi to someone confidentially using, this time, a key, *k*, of 3. And so his plaintext, *p*, is Hi, in which case his plaintext’s first character, *p0*, is H (aka 7), and his plaintext’s second character, *p1*, is i (aka 8). His ciphertext’s first character, *c0*, is thus K, and his ciphertext’s second character, *c1*, is thus L. Can you see why?

Let’s write a program called `caesar` that enables you to encrypt messages using Caesar’s cipher. At the time the user executes the program, they should decide, by providing a command-line argument, on what the key should be in the secret message they’ll provide at runtime. We shouldn’t necessarily assume that the user’s key is going to be a number; though you may assume that, if it is a number, it will be a positive integer.

Here are a few examples of how the program might work. For example, if the user inputs a key of `1` and a plaintext of `HELLO`:

```
$ ./caesar 1
plaintext:  HELLO
ciphertext: IFMMP
```

Here’s how the program might work if the user provides a key of `13` and a plaintext of `hello, world`:

```
$ ./caesar 13
plaintext:  hello, world
ciphertext: uryyb, jbeyq
```

Notice that neither the comma nor the space were “shifted” by the cipher. Only rotate alphabetical characters!

How about one more? Here’s how the program might work if the user provides a key of `13` again, with a more complex plaintext:

```
$ ./caesar 13
plaintext:  be sure to drink your Ovaltine
ciphertext: or fher gb qevax lbhe Binygvar
```

Why?

Notice that the case of the original message has been preserved. Lowercase letters remain lowercase, and uppercase letters remain uppercase.

And what if a user doesn’t cooperate?

```
$ ./caesar HELLO
Usage: ./caesar key
```

Or really doesn’t cooperate?

```
$ ./caesar
Usage: ./caesar key
```

Or even…

```
$ ./caesar 1 2 3
Usage: ./caesar key
```

Try It

To try out the staff’s implementation of this problem, execute

```
./caesar key
```

substituting a valid integer in place of `key`, within [this sandbox](http://bit.ly/2Vwi8n0).

How to begin? Let’s approach this problem one step at a time.

## Pseudocode

First, write in `pseudocode.txt` at right some pseudocode that implements this program, even if not (yet!) sure how to write it in code. There’s no one right way to write pseudocode, but short English sentences suffice. Recall how we wrote pseudocode for [finding Mike Smith](https://cdn.cs50.net/2018/fall/lectures/0/lecture0.pdf). Odds are your pseudocode will use (or imply using!) one or more functions, conditions, Boolean expressions, loops, and/or variables.

Spoiler

There’s more than one way to do this, so here’s just one!

1. Check that program was run with one command-line argument
2. Iterate over the provided argument to make sure all characters are digits
3. Convert that command-line argument from a `string` to an `int`
4. Prompt user for plaintext
5. Iterate over each character of the plaintext:
    1. If it is an uppercase letter, rotate it, preserving case, then print out the rotated character
    2. If it is a lowercase letter, rotate it, preserving case, then print out the rotated character
    3. If it is neither, print out the character as is
6. Print a newline

It’s okay to edit your own after seeing this pseudocode here, but don’t simply copy/paste ours into your own!

## Counting Command-Line Arguments

Whatever your pseudocode, let’s first write only the C code that checks whether the program was run with a single command-line argument before adding additional functionality.

Specifically, modify `caesar.c` at right in such a way that: if the user provides exactly one command-line argument, it prints `Success`; if the user provides no command-line arguments, or two or more, it prints `Usage: ./caesar key` and returns from main a value of 1 (which tends to signify an error) immediately. Remember, since this key is coming from the command line at runtime, and not via `get_string`, we don’t have an opportunity to re-prompt the user. The behavior of the resulting program should be like the below.

```
$ ./caesar 20
Success
```

or

```
$ ./caesar
Usage: ./caesar key
```

or

```
$ ./caesar 1 2 3
Usage: ./caesar key
```

Hints

- Recall that you can compile your program with `make`.
- Recall that you can print with `printf`.
- Recall that `argc` and `argv` give you information about what was provided at the command line.
- Recall that the name of the program itself (here, `./caesar`) is in `argv[0]`.
- Know that `return 1;` in main will end the program immediately.

## Accessing the Key

Now that your program is (hopefully!) accepting input as prescribed, it’s time for another step.

Recall that in our program, we must defend against users who technically provide a single command-line argument (the key), but provide something that isn’t actually an integer, for example:

```
$ ./caesar xyz
```

Before we start to analyze the key for validity, though, let’s make sure we can actually read it. Further modify `caesar.c` at right such that it not only checks that the user has provided just one command-line argument, but after verifying that, prints out that single command-line argument. So, for example, the behavior might look like this:

```
$ ./caesar 20
Success
20
```

Hints

- Recall that `argc` and `argv` give you information about what was provided at the command line.
- Recall that `argv` is an array of strings.
- Recall that with `printf` we can print a string using `%s` as the placeholder.
- Recall that computer scientists like counting starting from 0.
- Recall that we can access individual elements of an array, such as `argv`using square brackets, for example: `argv[0]`.

## Validating the Key

Now that you know how to read the key, let’s analyze it. Modify `caesar.c` at right such that instead of printing out the command-line argument provided, your program instead checks to make sure that each character of that command line argument is a decimal digit (i.e., `0`, `1`, `2`, etc.) and, if any of them are not, terminates (with a return code of 1) after printing the message `Usage: ./caesar key`. But if the argument consists solely of digit characters, you should convert that string (recall that `argv` is an array of strings, even if those strings happen to look like numbers) to an actual integer, and print out the *integer*, as via `%i` with `printf`. So, for example, the behavior might look like this:

```
$ ./caesar 20
Success
20
```

or

```
$ ./caesar 20x
Usage: ./caesar key
```

Hints

- Recall that `argv` is an array of strings.
- Recall that a string, meanwhile, is just an array of `char`s.
- Recall that the `string.h` header file contains a number of useful functions that work with strings.
- Recall that we can use a loop to iterate over each character of a string if we know its length.
- Recall that the `ctype.h` header file contains a number of useful functions that tell us things about characters.
- Recall that we can `return` nonzero values from `main` to indicate that our program did not finish successfully.
- Recall that with `printf` we can print an integer using `%i` as the placeholder.
- Recall that the `atoi` function converts a string that looks like a number into that number.

## Peeking Underneath the Hood

As human beings it’s easy for us to intuitively understand the formula described above, inasmuch as we can say “H + 1 = I”. But can a computer understand that same logic? Let’s find out. For now, we’re going to temporarily ignore the key the user provided and instead prompt the user for a secret message and attempt to shift all of its characters by just 1.

Extend the functionality of `caesar.c` at right such that, after validating the key, we prompt the user for a string (using `"plaintext: "` for the prompt) and then shift all of its characters by 1, printing out `"ciphertext: "` followed by the result and a newline. Your program should then exit by returning `0` from `main`. We can also at this point probably remove the line of code we wrote earlier that prints `Success`. All told, this might result in this behavior:

```
$ ./caesar 1
plaintext:  hello
ciphertext: ifmmp
```

Hints

- Try to iterate over every character in the plaintext and literally add 1 to it, then print it.
- If `c` is a variable of type `char` in C, what happens when you call `printf("%c", c + 1)`?

## Your Turn

Now it’s time to tie everything together! Instead of shifting the characters by 1, modify `caesar.c` to instead shift them by the actual key value. And be sure to preserve case! Uppercase letters should stay uppercase, lowercase letters should stay lowercase, and characters that aren’t alphabetical should remain unchanged.

Hints

- Best to use the modulo (i.e., remainder) operator, `%`, to handle wraparound from Z to A! But how?
- Things get weird if we try to wrap `Z` or `z` by 1 using the technique in the previous section.
- Things get weird also if we try to wrap punctuation marks using that technique.
- Recall that ASCII maps all printable characters to numbers.
- Recall that the ASCII value of `A` is 65. The ASCII value of `a`, meanwhile, is 97.
- If you’re not seeing any output at all when you call `printf`, odds are it’s because you’re printing characters outside of the valid ASCII range from 0 to 127. Try printing characters as numbers (using `%i` instead of `%c`) at first to see what values you’re printing, and make sure you’re only ever trying to print valid characters!

## How to Submit

Execute the below, logging in with your GitHub username and password when prompted. For security, you’ll see asterisks (`*`) instead of the actual characters in your password.

```
submit50 cs50/2019/x/caesar
```

## My Code

```c
#include <cs50.h>
#include <stdio.h>
#include <string.h>
#include <ctype.h>


int main(int argc, string argv[])
{
    int text_length;
    int key;
    string text;
    
    //Check that program was run with one command-line argument
    if (argc != 2)
    {
        printf("Usage: ./caesar key\n");
        return 1;
    }
    
    // Find the length of the cma
    int string_length = strlen(argv[1]); 
    
    // Iterate over the provided argument to make sure all characters are digits
    for (int i = 0; i < string_length; i++)
    {
        // if((int)argv[1][i] <= 48 || (int)argv[1][i] >= 57)   can also use this
        if (!isdigit(argv[1][i]))
        {
            printf("Usage: ./caesar key\n");
            return 1;
        }
    }
    
    // Convert that command-line argument from a string to an int 
    key = atoi(argv[1]);   
    
    // Prompt user for plaintext
    text = get_string("plaintext: ");
    text_length = strlen(text);
    
    // Iterate over each character of the plaintext
    int num;
    printf("ciphertext: ");
    for (int i = 0; i < text_length; i++)
    {
        // If it is uppercase 
        if (text[i] >= 65 && text[i] <= 90)
        {
            num = text[i] + (key % 26);
            if (num > 90)
            {
                num %= 90;
                num += 64;
            }
            text[i] = num;
            printf("%c", text[i]);
        }
        
        // If it is lowercase 
        else if (text[i] >= 97 && text[i] <= 122)
        {
            num = text[i] + (key % 26);
            if (num > 122)
            {
                num %= 122;
                num += 96; 
            }
            text[i] = num;
            printf("%c", text[i]);
        }
        else
        {
            printf("%c", text[i]);
        }
    }
    printf("\n");
}

```



# Vigenère

## Ooh, la la!

Vigenère’s cipher improves upon Caesar’s cipher by encrypting messages using a *sequence* of keys (or, put another way, a *keyword*).

In other words, if *p* is some plaintext and *k* is a keyword (i.e., an alphabetical string, whereby A (or a) represents 0, B (or b) represents 1, C (or c) represents 2, …, and Z (or z) represents 25), then each letter, *ci*, in the ciphertext, *c*, is computed as:

ci = (pi + kj) % 26

Note this cipher’s use of *kj* as opposed to just *k*. And if *k* is shorter than *p*, then the letters in *k* must be reused cyclically as many times as it takes to encrypt *p*.

In other words, if Vigenère himself wanted to say HELLO to someone confidentially, using a keyword of, say, ABC, he would encrypt the H with a key of 0 (i.e., A), the E with a key of 1 (i.e., B), and the first L with a key of 2 (i.e., C), at which point he’d be out of letters in the keyword, and so he’d reuse (part of) it to encrypt the second L with a key of 0 (i.e., A) again, and the O with a key of 1 (i.e., B) again. And so he’d write HELLO as HFNLP, per the below:

| plaintext     | H    | E    | L    | L    | O    |
| ------------- | ---- | ---- | ---- | ---- | ---- |
| + key         | A    | B    | C    | A    | B    |
| (shift value) | 0    | 1    | 2    | 0    | 1    |
| = ciphertext  | H    | F    | N    | L    | P    |

Let’s now write a program called `vigenere` that enables you to encrypt messages using Vigenère’s cipher. At the time the user executes the program, they should decide, by providing a command-line argument, on what the keyword should be for the secret message they’ll provide at runtime.

Here are a few examples of how the program might work.

```
$ ./vigenere bacon
plaintext:  Meet me at the park at eleven am
ciphertext: Negh zf av huf pcfx bt gzrwep oz
```

or for when the user provides a keyword that is not fully alphabetic:

```
$ ./vigenere 13
Usage: ./vigenere keyword
```

or for when they don’t provide a keyword at all:

```
$ ./vigenere
Usage: ./vigenere keyword
```

or for when they provide too many keywords:

```
$ ./vigenere bacon and eggs
Usage: ./vigenere keyword
```

Try It

How to begin? Let’s start with something familiar.

## Déjà vu

As you may have gleaned already, the basic idea for this cipher is strikingly similar to the idea underlying Caesar’s cipher. As such, our code from Caesar seems like a good place to begin, so feel free to start by replacing the entire contents of `vigenere.c`, at right, with your solution to `caesar.c`.

One difference between Caesar’s and Vigenère’s ciphers is that the key for Vigenère’s cipher is a series of letters, rather than a number. So let’s make sure that the user actually gave us a keyword! Modify the check you implemented in Caesar to instead ensure every character of the keyword is alphabetic, rather than a digit. If any of them isn’t, print `Usage: ./vigenere keyword` and return a non-zero value as we did before. If they are all alphabetic, after checking you should print `Success` and then, `return 0;` immediately (for now), since our enciphering code is not quite ready to work just yet, so we won’t have our program execute it.

Sample behavior:

```
$ ./vigenere alpha
Success
```

or

```
$ ./vigenere 123
Usage: ./vigenere keyword
```

Hints

- Recall that the `string.h` header file contains a number of useful functions that work with strings. See [CS50 Reference](https://reference.cs50.net/)’s menu for some!
- Recall that we can use a loop to iterate over each character of a string if we know its length.
- Recall that the `ctype.h` header file contains a number of useful functions that tell us things about characters. See [CS50 Reference](https://reference.cs50.net/)’s menu for some!

## Getting the shift value

Let’s for now assume that the user is providing single-character keywords. Can we convert that character into the correct shift value? Let’s do so by writing a *function*.

Near the top of your file, below the `#include` lines, let’s *declare* the *prototype* for a new function whose purpose is to do just that. It will take a single character as input, and it will output the shift value for that character.

```
int shift(char c);
```

Now we’ve declared a function called `shift` that takes a single character (`c`) as input, and will output an integer.

Now, down below the closing curly brace of `main`, let’s give ourselves a place to *define*(i.e., implement) this new function.

```
int shift(char c)
{
   // TODO
}
```

In place of that `TODO` is where we’ll do the work of converting that character to its positional integer value (so, again, `A` or `a` would be 0, `B` or `b` would be 1, `Z` or `z`would be 25, etc.)

To test this out, delete the line where you printed `"Success"` (but leave the `return 0;`for now), and in place of the just-deleted line, add the below lines to test whether your code works.

```
int key = shift(argv[1][0]);
printf("%i\n", key);
```

Your program should print a 0 if run with the keyword `A` or `a`. Try running the program with other capital and lowercase letters as the keyword. Is the behavior what you expect?

Hints

- Functions have inputs and outputs.
- When we *declare* a function, we need to provide its return type, name, and an argument list, each of which also has a type.
- When we *use* or *call* a function, we just plug in appropriate values in the argument list, and assign the output of the function to a variable that corresponds to the function’s return type.
- If `argv[1]` is a string, then `argv[1][0]` is just the first character of that string.
- Recall that the `ctype.h` header file contains a number of useful functions that tell us things about characters.
- The ASCII value of `A` is 65. The ASCII value of `a` is 97.
- The ASCII value of `B` is 66. The ASCII value of `b` is 98. See a potential pattern emerging?

## One-character keywords

Time to get back to using that enciphering code you wrote before! You may have noticed that if your keyword *k* consists of exactly one letter (say, `H` or `h`), Vigenère’s cipher effectively becomes a Caesar cipher (of, in this example, 7). Let’s for now indeed assume the user’s keyword will just be a single letter. Use your newly-written `shift`function to calculate the shift value for the letter they provided, assign the return value of that function to an integer variable `key`, and use `key` exactly as you did in Caesar’s cipher! It should suffice, in fact, to simply delete the recently-added `printf` and the `return 0;` line now, letting the program finally proceed to your previously-written Caesar cipher code!

```
$ ./vigenere A
plaintext:  hello
ciphertext: hello
```

or

```
$ ./vigenere b
plaintext:  HELLO
ciphertext: IFMMP
```

or

```
$ ./vigenere C
plaintext:  HeLlO
ciphertext: JgNnQ
```

Hints

If some of your variables in your Caesar solution don’t match what they’ve been called so far in this lab, just edit the names of things so they do match!

## Final Steps

Now it’s your turn to take things across the finish line by implementing the remaining functionality in `vigenere.c`. Remember that the user’s keyword will probably consist of multiple letters, so you may need to calculate a new shift value for each letter of the plaintext; you may then want to move your `shift` function into your loop somehow.

Remember also that every time you encipher a character, you need to move to the next letter of *k*, the keyword (and wrap around to the beginning of the keyword if you exhaust all of its characters). But if you don’t encipher a character (e.g., a space or a punctuation mark), don’t advance to the next character of *k*!

And as before, be sure to preserve case, but do so only based on the case of the original message. Whether or not a letter in the keyword is capitalized should have no bearing on whether a letter in the ciphertext is!

Hints

- You’ll probably need one counter, `i` for iterating over the plaintext and one counter, `j` for iterating over the keyword.
- You’ll probably find it easiest to control the keyword counter yourself, rather than relying on the `for` loop you’re using to iterate over the plaintext!
- If the length of the keyword is, say, 4 characters, then the last character of that keyword can be found at `keyword[3]`. Then, for the next character you encipher, you’ll want to use `keyword[0]`.

## How to Submit

Execute the below, logging in with your GitHub username and password when prompted. For security, you’ll see asterisks (`*`) instead of the actual characters in your password.

```
submit50 cs50/2019/x/vigenere
```

## My code

```c
#include <cs50.h>
#include <stdio.h>
#include <string.h>
#include <ctype.h>

int shift(char c);

int main(int argc, string argv[])
{
    int text_length;
    string text;
    
    //Check that program was run with one command-line argument
    if (argc != 2)
    {
        printf("Usage: ./vigenere keyword\n");
        return 1;
    }
    
    // Find the length of the cma
    int string_length = strlen(argv[1]); 
    
    // Iterate over the provided argument to make sure all characters are digits
    for (int i = 0; i < string_length; i++)
    {
        // if((int)argv[1][i] <= 48 || (int)argv[1][i] >= 57)   can also use this
        if (!isalpha(argv[1][i]))
        {
            printf("Usage: ./vigenere keyword\n");
            return 1;
        }
    }
    int key;
    
    // Prompt user for plaintext
    text = get_string("plaintext: ");
    text_length = strlen(text);
    
    // Iterate over each character of the plaintext
    int num;
    int j = 0;
    printf("ciphertext: ");
    for (int i = 0; i < text_length; i++)
    {
        // set the value of key
        if (j < string_length)
        {
            key = shift(argv[1][j]);
        }
        else
        {
            j = 0;
            key = shift(argv[1][j]);
        }
        
        // rotate uppercase text 
        if (text[i] >= 65 && text[i] <= 90)
        {
            num = text[i] + (key % 26);
            if (num > 90)
            {
                num %= 90;
                num += 64;
            }
            text[i] = num;
            printf("%c", text[i]);
            j++;
        }
        else if (text[i] >= 97 && text[i] <= 122) // rotate lowercase text
        {
            num = text[i] + (key % 26);
            if (num > 122)
            {
                num %= 122;
                num += 96; 
            }
            text[i] = num;
            printf("%c", text[i]);
            j++;
        }
        else // just print any other characters without rotating
        {
            printf("%c", text[i]);
        }
    }
    printf("\n");
}

// this function returns 0 for a,A , 1 for b,B and so on..
int shift(char c)
{
    if (c >= 65 && c <= 90)
    {
        return c - 65;
    }
    else
    {
        return c - 97;
    }
}
```



# Crack

## The Shadow Knows

On most systems running Linux these days is a file called `/etc/shadow` that contains usernames and passwords. Fortunately, the passwords therein aren’t stored “in the clear” but are instead encrypted using a “one-way hash function.” When a user logs into these systems by typing a username and password, the latter is encrypted with the very same hash function, and the result is compared against the username’s entry in `/etc/shadow`. If the two hashes match, the user is allowed in. If you’ve ever forgotten some password, you might have been told that tech support can’t look up your password but can change it for you. Odds are that’s because tech support can only see, if anything at all, a hash of your password, not your password itself. But they can create a new hash for you.

Even though passwords in `/etc/shadow` are hashed, the hash function is not always that strong. Quite often are adversaries, upon obtaining that file somehow, able to guess (and check) users’ passwords or crack them using brute force (i.e., trying all possible passwords). Below is what `/etc/shadow` might look like, albeit simplified, wherein each line is formatted as `username:hash`.

```
brian:51.xJagtPnb6s
bjbrown:50GApilQSG3E2
emc:502sDZxA/ybHs
greg:50C6B0oz0HWzo
jana:50WUNAFdX/yjA
lloyd:50n0AAUD.pL8g
malan:50CcfIk1QrPr6
natmelo:50JIIyhDORqMU
rob:51v3Nh6ZWGHOQ
veronica:61v1CDwwP95bY
walker:508ny6Rw0aRio
zamyla:50cI2vYkF0YU2
```

## Safecracker

Your task is to design and implement a program, `crack`, that cracks passwords. We’re not going to give too many hints on this one, but to get started you may want to read up on how the `crypt` function works on Unix/Linux systems, such as this lab environment. To do so, type:

```
man crypt
```

in the terminal. Take particular note of that program’s mention of “salt”.

In order to declare function `crypt` for use in your solution, you’ll want to put

```
#include <crypt.h>
```

near the top of your file. Use `pseudocode.txt` as a notepad for ideas as to how you should organize your program!

### Specification

- Your program should accept one and only one command-line argument: a hashed password.
- If your program is executed without any command-line arguments or with more than one command-line argument, your program should print an error (of your choice) and exit immediately, with `main` returning `1` (thereby signifying an error).
- Otherwise, your program must proceed to crack the given password, ideally as quickly as possible, ultimately printing the password in the clear followed by `\n`, nothing more, nothing less, with `main` returning `0`.
- Assume that each password has been hashed with C’s DES-based (not MD5-based) `crypt` function.
- Assume that each password is no longer than five (5) characters. Gasp!
- Assume that each password is composed entirely of alphabetical characters (uppercase and/or lowercase).

Below, then, is some example behavior.

```
$ ./crack
Usage: ./crack hash
$ ./crack 50cI2vYkF0YU2
LOL
```

Hints

- Recall that `argc` and `argv` give us information about what was typed at the command line.
- Recall that a string is just an array of characters (`char`s).
- Recall that we can access individual elements of an array using square brackets (`[ ]`).
- Recall that the salt is the first two characters of the hash.
- Recall that sometimes, people use passwords that are actual words. Perhaps there’s an optimization that can be employed?
- Brute force algorithms aren’t the fastest, and that’s okay! Recall that shorter passwords are usually easier to crack than longer ones.

## How to Submit

Execute the below, logging in with your GitHub username and password when prompted. For security, you’ll see asterisks (`*`) instead of the actual characters in your password.

```
submit50 cs50/2019/x/crack
```

## My Code

```c
#include <cs50.h>
#include <stdio.h>
#include <crypt.h>
#include <string.h>

int main(int argc, string argv[])
{
    // initialize key and alphabets
    char key[] = ("\0\0\0\0\0\0");
    string alphabets = ("ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz");
    
    
    // check if command line argument is a hash or not 
    if (argc != 2 || strlen(argv[1]) != 13)
    {
        printf("Usage: ./crack hash\n");
        return 1;
    }
    
    // store salt in salt and hash in hash
    string hash = argv[1];
    char salt[3]; 
    salt[0] = argv[1][0];
    salt[1] = argv[1][1];
    salt[2] = '\0';
    
    // crack the key 
    for (int i = 1; i < 6; i++)
    {
        // if the password is single alphabet
        if (i == 1)
        {
            for (int n = 0; n < strlen(alphabets); n++)
            {
                key[0] = alphabets[n];
                key[1] = '\0';
                key[2] = '\0';
                key[3] = '\0';
                key[4] = '\0';

                if (!strcmp(crypt(key, salt), hash))
                {
                    printf("%s\n", key);
                    return 0;
                }
            }
        }
        
        // if the password is double alphabet
        if (i == 2)
        {
            for (int m = 0; m < strlen(alphabets); m++)
            {
                for (int n = 0; n < strlen(alphabets); n++)
                {
                    key[0] = alphabets[m];
                    key[1] = alphabets[n];
                    key[2] = '\0';
                    key[3] = '\0';
                    key[4] = '\0';

                    if (!strcmp(crypt(key, salt), hash))
                    {
                        printf("%s\n", key);
                        return 0;
                    }
                }
            }
        }
        
        // if the password has three alphabets 
        if (i == 3)
        {
            for (int l = 0; l < strlen(alphabets); l++)
            {
                for (int m = 0; m < strlen(alphabets); m++)
                {
                    for (int n = 0; n < strlen(alphabets); n++)
                    {
                        key[0] = alphabets[l];
                        key[1] = alphabets[m];
                        key[2] = alphabets[n];
                        key[3] = '\0';
                        key[4] = '\0';

                        if (!strcmp(crypt(key, salt), hash))
                        {
                            printf("%s\n", key);
                            return 0;
                        }
                    }
                }
            }
        }
        
        // if the password has four alphabets
        if (i == 4)
        {
            for (int k = 0; k < strlen(alphabets); k++)
            {
                for (int l = 0; l < strlen(alphabets); l++)
                {
                    for (int m = 0; m < strlen(alphabets); m++)
                    {
                        for (int n = 0; n < strlen(alphabets); n++)
                        {
                            key[0] = alphabets[k];
                            key[1] = alphabets[l];
                            key[2] = alphabets[m];
                            key[3] = alphabets[n];
                            key[4] = '\0';

                            if (!strcmp(crypt(key, salt), hash))
                            {
                                printf("%s\n", key);
                                return 0;
                            }
                        }
                    }
                }
            }   
        }
        
        // if the password has 5 alphabets 
        if (i == 5)
        {
            for (int j = 0; j < strlen(alphabets); j++)
            {
                for (int k = 0; k < strlen(alphabets); k++)
                {
                    for (int l = 0; l < strlen(alphabets); l++)
                    {
                        for (int m = 0; m < strlen(alphabets); m++)
                        {
                            for (int n = 0; n < strlen(alphabets); n++)
                            {
                                key[0] = alphabets[j];
                                key[1] = alphabets[k];
                                key[2] = alphabets[l];
                                key[3] = alphabets[m];
                                key[4] = alphabets[n];
                                
                                if (!strcmp(crypt(key, salt), hash))
                                {
                                    printf("%s\n", key);
                                    return 0;
                                }
                            }
                        }
                    }
                }
            }
        }
    }
    
    // print error
    printf("cant crack password\n");
}

```





