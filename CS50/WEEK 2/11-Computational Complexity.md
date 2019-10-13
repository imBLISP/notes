# COMPUTATIONAL COMPLEXITY

- In order to make most effective use of our computational resources, it's important that we have the skill set to analyze the complexity of algorithms, so we know what resources those algorithms require.
- Being able to analyze an algorithm allows us to have an idea of how well it scales as we throw larger and larger data sets at it.
- When we talk about the complexity of an algorithm, we generally refer to the **worst-case scenario.**
    - We refer to this as $O$ (big $O$).
- We sometimes also care about the **best-case scenario ** (also known as $\Omega $ or **Big Omega**)
- In CS50, we'll leave the rigorous analysis aside and focus more on reasoning complexity with common sense. 
- What is a data set?
    - Whatever makes the sense in context.
- We can measure an algorithm based on how it handles these inputs. Let's call this measure $f(n)$.
- We don't actually care about what $f(n)$ is precisely. Rather, we care only about its **tendency**, which is dictated by its highest-order term.

|    $n$    | $f(n) = n^3$  | $f(n) = n^3 + n^2$ | $f(n) = n^3 - 8n^2 + 20n$ |
| :-------: | :-----------: | :----------------: | :-----------------------: |
|     1     |       1       |         2          |            13             |
|    10     |     1,000     |       1,100        |            400            |
|   1,000   | 1,000,000,000 |   1,001,000,000    |        992,020,000        |
| 1,000,000 | 1.0 x 10^18^  | 1.000001 x 10^18^  |     9.99992 x 10^17^      |

- difference between these algorithms becomes less and less as the datasize gets bigger.

| Symbols     | Name              |
| ----------- | ----------------- |
| $O(1)$      | constant time     |
| $O(log n)$  | logarithmic time  |
| $O(n)$      | linear time       |
| $O(nlogn)$  | Linearithmic time |
| $O(n^2)$    | Quadratic time    |
| $O(n^c)$    | polynomial time   |
| $O(c^n)$    | exponential time  |
| $O(n!)$     | factorial time    |
| $O(\infin)$ | infinite time     |

- $O(1)$
    - Always takes a single operation in the worst case.

```c
int four_for_you(int array[1000])
{
    return 4;
}

int add_two_nums(int a, int b)
{
    return a + b;
}
```

- $O(n)$
    - Always takes n operations in the worst case.
    - ex: Linear search.
- What's the runtime?
    - Ans: $O(m)$

```c
for (int j = 0; j < m; j++)
{
    // loop body that runs in O(1)
}
```

- What's the runtime?
    - Ans: $O(p^2)$

```c
for (int j = 0; j < p; j++)
{
    for (int k = 0; k < p; k++)
    {
        // loop body that runs in O(1)
    }
}
```

