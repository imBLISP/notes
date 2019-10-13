# BINARY SEARCH

---

#### Runtimes:

Worst case runtime: $O(\log n )$

Best case runtime: $\Omega (1)$

#### Pseudocode:

- Calculate the middle point of the current (sub)array.
- if the target is at the middle, stop.
- Otherwise, if the target is less than what's at the middle, repeat, changing the end point to be just to the left of the middle.
- otherwise, if the target is greater than what's at the middle, repeat, changing the start point to be      just to the right of the middle.

#### Properties:

- the idea of the algorithm is to divide and conquer, reducing the search area by half each time, trying      to find a target number.
- ==ARRAY MUST BE SORTED==
- $mid point$ = $(start index + end index) / 2$ 

- when we are searching for a element that is not in the array the start point and end point will cross.      and we will have a subarray of size 0.
- ==worst case scenario==: 
    we have to divide a list of n elements in half repeatedly to find the target element, either because the target element will be found at the end of the last division or doesnt exist in the array at all. 
- ==Best case scenario==:
    The target element is at the midpoint of the full array, and so we can stop looking immediately after we start. 
- [Picture on page "Binary Search"](onenote:https://d.docs.live.net/0ec05fbb91911b65/Documents/CS50 notes/week 2.one#Binary Search&section-id={9C45C914-86C3-D741-BF8F-AED174BAE2A3}&page-id={FECA02D4-0699-A84F-A785-039B036006EB}&object-id={40DD68A9-A648-7F43-974C-C53F515D6EAA}&5B)  ([Web view](https://onedrive.live.com/view.aspx?resid=EC05FBB91911B65!1558&id=documents&wd=target(week 2.one|9C45C914-86C3-D741-BF8F-AED174BAE2A3%2FBinary Search|FECA02D4-0699-A84F-A785-039B036006EB%2F)))

