# HEXADECIMAL

---

- Most western cultures use decimal system, aka base-10, to represent numeric data.
    `0 1 2 3 4 5 6 7 8 9 `

- As we know, computers use the binary system, aka base-2, to represent numeric (and indeed all data).
    `0 1`

- As the computer scientists, it's useful to be able to express data the same way computer does.

- The **hexadecimal system**, aka base-16, is a much more consise way to express the data on the computer's system.
    `0 1 2 3 4 5 6 7 8 9 A B C D E F `

- Hexadecimal makes this mapping easy because a group of four binary digits (bits) is able has 16 different combinations, and each of those combinations maps to a single hexadecimal digit.

- Use prefix `0x` (`0` for octal and `0b` for binary) before the hexadecimal to distinguish them.

- Just like binary has place values (1, 2, 4, 8…) or ($2^0,2^1,2^2,2^3...$) and decimal does too (1, 10, 100, 1000…) or ($10^0,10^1,10^2,10^3...$) , so does hexadecimal ie  ($16^0,16^1,16^3...$)

- To convert a binary number to hexadecimal, group four binary digits (bits) together from right to left

    - Pad the leftmost group with extra 0 bits at the front if necessary.

- Then use the chart a few slides back or your memory to convert those bits to something a bit more concise.

    ```      
                            01000110101000101011100100111101
                         0100 0110 1010 0010 1011 1001 0011 1101  
                           4    6    A    2    B    9    3    D
                                      0x46A2B93D
    ```

