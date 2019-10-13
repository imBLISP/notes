# FILE POINTERS

---

- The ability to read data from and write data to file is the primary means of storing  **persistent data**, data that does not dissapear when your program stops running.

- The abstraction of files that C provides is implemented in a data structure known as `FILE`.

    - Almost universally when working with files, we will be using pointers to them, `FILE*`.

- The file manipulation functions all live in `stdio.h`

    - All of them accept `FILE*` as one of their parameters, except for the function fopen(), which is used to get a file pointer in the first place.

- Some of the most common input/output (I/O) functions that we'll be working with are:

    | fopen() | fclose() | fgetc() | fputc() | fread() | fwrite() |
    | ------- | -------- | ------- | ------- | ------- | -------- |

#### `fopen()`

- Opens a file and returns a file pointer to it.

- Always check the return value to make sure you don't get back NULL.

- ```c
    FILE* ptr = fopen(<filename>, <operation>);
    ex:
    FILE* ptr1 = fopen("file1.txt", "r"); // r, w, a means read, write, append
    ```

#### `fclose()`

- Closes the file pointed to by the given file pointer.

    ```c
    fclose(<file pointer>);
    ex:
    fclose(ptr1);
    ```

#### `fgetc()`

- Reads and returns the next character from the file pointed to.

- file get a character.

- Note: The operation of the file pointer passed in as a parameter must be "r" for read, or you will suffer an error.

    ```c
    char ch = fgetc(<file pointer>);
    ex:
    char ch = fgetc(ptr1);
    ```

- The ability to get single characters from files, if wrapped in a loop, means we could read all the characters from a file and print them to the screen, one-by-one, essentially.

    ```c
    // prints out all the characters of the file.
    char ch;
    while((ch = fgetc(ptr)) != EOF) // EOF- end of file character.
        printf("%c", ch);
    ```

- We mightput this in a file called `cat.c` , after the linux command "cat" which essentialy does this.

#### `fputc()`

- Writes or appends the specified character to the pointed-to file.

- Note: The operation of the file pointer passed in as a parameter must be "w" for write or "a" for append, or you will suffer an error.

    ```c
    fputc(<character>, <file pointer>);
    ex:
    fputc('A', ptr3);
    ```

- Now we can read characters from files and write characters to them. Let's extend our previous example to copy one file to another, instead of printing to the screen.

    ```c
    char ch;
    while((ch = fgetc(ptr)) != EOF)
        fputc(ch, ptr2);
    ```

- We might put this in a file called cp. c, after the linux command "cp" which essentially does just this.

#### `fread()`

- ```c
    fread(<buffer>, <size>, <qty>, <file pointer>);
    ```

- Reads` <qty>` units of size `<size>` from the file pointed to and stores them in memory in a buffer (usually an array) pointed to by `<buffer> `.

- Note: The operation of the file pointer passed in as a parameter must be "r" for read, or you will siffer an error.

    ```c
    int arr[10];
    fread(arr, sizeof(int), 10, ptr);
    ```

    ```c
    double* arr2 = malloc(sizeof(double) * 80);
    fread(arr2, sizeof(double), 80, ptr);
    ```

    ```c
    char c;
    fread(&c, sizeof(char), 1, ptr);
    ```

#### `fwrite()`

- ```c
    fwrite(<buffer>, <size>, <qty>, <file pointer>);
    ```

- Writes `<qty>` units of size `<size>` to the file pointed to by reading them from a buffer (usually an array) pointed to by `<buffer>`.

- Note: The operation of the file pointer passed in as a parameter must be "w" for write or "a" for append, or you will suffer an error.

    ```c
    double* arr2 = malloc(sizeof(double) * 80);
    fwrite(arr2, sizeof(double), 80, ptr);
    ```

    ```c
    char c;
    fwrite(&c, sizeof(char), 1, ptr);Other functions:
    ```

#### Other Functions:

| Function    | Description                                                  |
| ----------- | ------------------------------------------------------------ |
| `fgets()`   | Reads a full string from a file.                             |
| `fputs()`   | Writes a full string to a file.                              |
| `fprintf()` | Writes a formatted string to a file.                         |
| `fseek()`   | Allows you rewind or fast-forward within a file.             |
| `ftell()`   | Tells you at what (byte) position you are at within a file.  |
| `feof()`    | Tells you whether you've read to the end of the file.        |
| `ferror()`  | Indicates whether an error has occured in working with a file. |

