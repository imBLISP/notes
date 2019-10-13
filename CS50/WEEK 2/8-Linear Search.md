# LINEAR SEARCH

---



#### Properties:

In Linear search, the idea of the algorithm is to iterate across the array from left to right, searching for a specified element.

#### In pseudocode:

- Repeat, starting at the first element
    - If the first element is what you're looking for (the target), stop.
    - Otherwise, move to the next element.



#### Runtimes:

###### Worst-case scenario $O(n)$

We have to look through the entire array of n elements,, either because the target element is th elast element of the array or doesn't exist in the array at all.

###### Best-case scenario $\Omega(1)$

The target element is the first element of the array, and so we can stop looking immediately after we start.

