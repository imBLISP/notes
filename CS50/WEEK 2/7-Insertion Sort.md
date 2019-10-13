# INSERTION SORT

---

#### Properties:

In insertion sort, the idea of the algorithm is to build your sorted array in place, shifting elements out of the way if necessary to make room as you go.

#### Pseudocode:

- Call the first element of the array "sorted".
- repeat until all the elements are sorted:
    - Look at the next unsorted element. Insert into the a "sorted" portion by shifting the requisite number of elements.

#### Runtimes:

###### Worst-case Scenario $O(n^2)$

The array is in reverse order; we have to shift each of the n elements n positions each time we make an insertion.

###### Best-case Scenario  $\Omega(n)  $ 

The array is already perfectly sorted, and we simply keep moving the line between "unsorted" and "sorted" as we examine each element.





