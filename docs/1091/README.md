# Algorithms

## Linear Search
* Linear search is an algorithm that you can use to find an element in array.
    * In Linear search, the idea of the algorithm is to iterate across the array from left to right, searching for a specific element.
    * **In pseudocode:
        * Repeat,starting at the first element:
            * If the first element is what you're looking for (the target), stop.
            Otherwise, move to the next element.
            * **Worst-case scenario:** We have to look through the entire array of n elements, either because the target element is the last element of the array or doesn't exist in the array at all.

            * **Best-case scenario:** The target element is the first element of the array, and so we can stop looking immediately after we start. 
    * **Recap**
        * So Worst-case is we don't find the element so it runs in `O(n)`
        * And the Best-case we find the element immediately and so it runs in `Ω(1)`

## Binary Search
* Binary search is an algorithm we can use to find an element inside an array.
* Unlike Linear search, it requires a special condition to be meet forehand, but it's so much more efficient if that condition is, in fact, met.

* So the idea here is divide and conquer.
    * In binary search, the idea the idea of the algorithm is to devide and conquer, reducing the search area by half each time, trying to find a target number.
        In order to leverage this power however, our array must be sorted, else we cannot make assumptions about the array's contents.
    
    **VIDEO TIME STAMP: 0:42**





---

Documentation By: **Raymond C. TURNER**

Last Update: Sunday 17th September 2023