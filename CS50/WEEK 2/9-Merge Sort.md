# MERGE SORT 

---



#### Properties:

- In the merge sort, the idea of the algorithm is to sort smaller arrays and then combine those arrays together (merge them) in a sorted order. 
- Merge sort leverages something called ==recursion==.

#### Pseudocode:

- Sort the left half of the array (assumming $n>1$ )
- Sort the right half of the array (assuming $n >$ 1)
- merge the two halves together

#### Runtimes:

###### Worst-case scenario $O(n \log n)$

We have to split n elements ep and then recombine them, effectively doubling the sorted subarrays as we build them up. (combining sorted 1-element array into 2-element arrays, combining sorted 2-element arrays into 4-element arrays..)

###### Best-case scenario $\Omega(n \log n)$

The array is already perfectly sorted. but we still have to split and recombine it back together with this algorithm.