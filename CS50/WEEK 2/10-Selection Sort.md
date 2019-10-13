# SELECTION SORT

---



#### Properties:

In selection sort, the idea of the algorithm is to find the smallest list.

#### Pseudocode:

- Repeat until no unsorted elements remaina:
    - Search the unsorted part  of the data to find the smallest value.
    - swap the smallest found value with the first element of the unsorted part.

#### Runtimes:

###### Worst-case scenario $O(n^2)$

We have to iterate over each of the n elements of the array (to find the smallest unsorted element) and we must repeat this process   n times, since only one element gets sorted on each pass.

###### Best-case scenario $\Omega(n^2)$

Exactly the same! There's no way to guarantee the array is sorted until we go through this process for all the elements.