# PSET6

https://docs.cs50.net/2019/x/psets/6/index.html

#### Hello

https://docs.cs50.net/2019/x/psets/6/sentimental/hello/hello.html

```python
# take user input
name = input("What is you name?\n")

# print hello name
print("hello, " + name)

```

#### Mario

###### Mario(less)

https://docs.cs50.net/2019/x/psets/6/sentimental/mario/less/mario.html

```python
# get height from the user
while True:
    try:
        height = int(input("Height: "))
    except ValueError:
        continue
    if height >= 1 and height <= 8:
        break

# for loop iterating through the height
for i in range(height):
    # print the spaces
    print(" " * (height - (i + 1)), end="")

    # print the hashes
    print("#" * (i + 1))
```

###### Mario(more)

https://docs.cs50.net/2019/x/psets/6/sentimental/mario/more/mario.html

```python
# take user input and validate
while True:
    try:
        height = int(input("Height: "))
    except ValueError:
        continue

    if height >= 1 and height <= 8:
        break

# for loop
for i in range(height):
    # print spaces
    print(" " * (height - (i + 1)), end="")

    # print hashes
    print("#" * (i + 1), end="")

    # print two spaces
    print(" " * 2, end="")

    # print hashes
    print("#" * (i + 1))
```

#### Cash

https://docs.cs50.net/2019/x/psets/6/sentimental/cash/cash.html

```python
import sys

# take user input and ensure it's valid
while True:
    try:
        cash = float(input("Change Owed: "))
    except ValueError:
        continue

    if cash >= 0:
        break

# round off the value
# cash = round(cash, 2)

# coins
coins = 0;

# multiply dollars with 100 to make cents
cash *= 100;

# check if input is smaller than 25
if cash >= 25:
    # if its not then input = input % 25 and coins += input // 25
    coins += cash // 25
    cash = cash % 25

    # if input is 0 then return coins
    if cash == 0:
        print(coins)
        sys.exit()
# check if input is smaller than 10
if cash >= 10:
    # if its not then input = input % 10 and coins += input // 10
    coins += cash // 10
    cash = cash % 10

    # if input is 0 then return coins
    if cash == 0:
        print(coins)
        sys.exit()
# check if input is smaller than 5
if cash >= 5:
    # if its not then input = input % 5 and coins += input // 5
    coins += cash // 5
    cash = cash % 5\

    # if input is 0 then return coins
    if cash == 0:
        print(coins)
        sys.exit()
# input = input % 1 and coins += input // 1
coins += cash // 1
cash = cash % 1

# return coins
print(coins)
```

#### Credit

https://docs.cs50.net/2019/x/psets/6/sentimental/credit/credit.html

```python
import sys


while True:
    try:
        temp = int(input("Number: "))
    except ValueError:
        continue
    card_number = str(temp)
    break

start = 1
summation = 0
length = len(card_number)

if (length - 1) % 2 != 0:
    start = 0
else:
    summation += int(card_number[0])

for i in range(start, length, 2):

    if int(card_number[i])*2 > 9:
        summation += (int(card_number[i]) * 2) % 10 + 1
    else:
        summation += int(card_number[i]) * 2

    summation += int(card_number[i + 1])

if summation % 10 != 0:
    print("INVALID")
    sys.exit()

if length == 15 and (int(card_number)//10000000000000 == 34 or int(card_number)//10000000000000 == 37):
    print("AMEX")

elif length == 16 and (int(card_number)//100000000000000 == 51 or int(card_number)//100000000000000 == 52 or int(card_number)//100000000000000 == 53 or int(card_number)//100000000000000 == 54 or int(card_number)//100000000000000 == 55):
    print("MASTERCARD")

elif (length == 13 or length == 16) and (int(card_number)//1000000000000000 == 4 or int(card_number)//1000000000000 == 4):
    print("VISA")
else:
    print("INVALID")

```

#### Caesar

https://docs.cs50.net/2019/x/psets/6/sentimental/caesar/caesar.html

```python
import sys

# check if there are two command line arguments
if len(sys.argv) != 2:
    print("Usage: python caesar.py k")
    sys.exit(1)

# store the key
key = int(sys.argv[1])

# ask user for plaintext
plainText = input("plaintext: ")

print("ciphertext: ", end="")

for c in plainText:

    if not c.isalpha():
        print(c, end="")
        continue

    if c.isupper():
        c = chr((ord(c) + key) % 65 % 26 + 65)
        print(c, end="")
    else:
        c = chr((ord(c) + key) % 97 % 26 + 97)
        print(c, end="")

print()
```

#### Crack

https://docs.cs50.net/2019/x/psets/6/sentimental/crack/crack.html