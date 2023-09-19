# Algorithms

## Linear Search
* Linear search is an algorithm that you can use to find an element in array.
    * In Linear search, the idea of the algorithm is to iterate across the array from left to right, searching for a specific element.
    * **In pseudocode:**
        * Repeat,starting at the first element:
            * If the first element is what you're looking for (the target), stop.
            Otherwise, move to the next element.
            * **Worst-case scenario:** We have to look through the entire array of n elements, either because the target element is the last element of the array or doesn't exist in the array at all.

            * **Best-case scenario:** The target element is the first element of the array, and so we can stop looking immediately after we start. 
* **Recap**
    * So Worst-case is we don't find the element so it runs in **O(*n*)**
    * And the Best-case we find the element immediately and so it runs in **Ω(*1*)**

---

## Binary Search
* **Target | Start | End | Middle**
* **Note!** With Binary search you must have a sorted array.
* Binary search is an algorithm we can use to find an element inside an array.
* Unlike Linear search, it requires a special condition to be meet forehand, but it's so much more efficient if that condition is, in fact, met.

* So the idea here is divide and conquer.
    * In binary search, the idea the idea of the algorithm is to devide and conquer, reducing the search area by half each time, trying to find a target number.
        In order to leverage this power however, our array must be sorted, else we cannot make assumptions about the array's contents.

* **In pseudocode:**
    * Repeat untill (sub)array is of size 0:
      * Calculate the middle point of the current (sub)array.
      * If the target is at the middle, stop.
      * Otherwise, if the target is less than what's at the middle, repeat, changing the end point to be just to the left of the middle.
      * Otherwise, if the target is greater than what's at the middle, repeat, changing the start point to be just to the right of the middle.
  
      * **Worst-case scenario:** We have to devide a list of n elements in half repeatedly to find the target element, either because the target element will be found at the end of the last division or doesn't exist in the array at all.
  
      * **Best-case scenario:** The target element is at the midpoint of the full array, and so we can stop looking immediately after we start. 

* **Recap**
    * So Worst-case is we don't find the element so it runs in **O(log*n*)**
    * And the Best-case we find the element immediately and so it runs in **Ω(*1*)**

Binary search is a lot better than Linear search, however you have to deal with the process of sorting your array first, before you can leverage the power of Binary search.

---

## Bubblesort
* In bubble, the idea of the algorithm is move higher valued elements generally towards the right and lower value elements generally towards the left.

* **In pseudocode:**
    * Set swap counter to a non-zero value
    * Repeat unti swap counter is 0:
        * Reset swap counter to 0
        * Look at each adjacent pair
            * If two adjacent elements are not in order, swap them and add one to the swap counter

* **Worst-case scenario:** The array is iin reverse order; we have have to bubble each of the ***n*** elements all the way accross the array, and since we can only fully bubble one element into position per pass, we musy do this ***n*** times.
  
* **Best-case scenario:** The array is already sorted, and we make no swaps on the first pass.

* **Recap**
    * **Worst-case scenario:** is we don't find the element so it runs in **O(*n*2)**
    * **Best-case scenario:** we find the element immediately and so it runs in **Ω(*n*)**

---

## Selection Sort
* In selection sort, the idea of the algorithm is to find the smallest unsorted element and add it to the end of the sorted list.

* **In pseudocode:**
    * Repeat until no unsorted elements remain:
        * Search the unsorted data to find the smallest value.
        * Swap the smallest found value with the first element of the unsorted part.

* **Recap**
    * **Worst-case scenario:** We have to iterate over each of the ***n*** elements of the array (to find to find the smallest unsorted element) and we must repeat this process ***n*** times, since only one element gets sorted on each pass. **O(*n2*)**
    * **Best-case scenario:** Exactly the same! There's way to guarantee the array is sorted until we go through this process for all the elements. **Ω(*n2*)**

---

## Recursion
* We might describe an implementation of an algorithm as being particularly *"elegant"* if it solves in a way that is both interesting and easy to visualize.
* The technique of **recursion** is a very common way to implement such an *"elegant"* solution.
* The definition of a recursive function is one, as part of its execution, involkes itself.
* The factorial function(*n!*) is defined over all positive integers.
  * Eg: 5 factorial is `5 * 4 * 3 * 2 * 1,` 4 factorial is `4 * 3 * 2 * 1`.
* *n!* equals all of the positive integers less than or equal to *n*, multiplied together.
* Thinking in terms of programming, we'll define mathmatical function *n!* as **fact**(n).

### Factorial
fact(1) = 1
fact(2) = 2 * 1
fact(3) = 3 * 2 * 1
fact(4) = 4 * 3 * 2 * 1
fact(5) = 5 * 4 * 3 * 2 * 1

fact(1) = 1
fact(2) = 2 * fact(1)
fact(3) = 3 * fact(2)
fact(4) = 4 * fact(3)
fact(5) = 5 * fact(5)
...

fact(n) = n * fact (n-1)

* This forms the basis for a **recursive definiton** of the factorial function.
* Every recursive function has two cases that could apply, given any input.
  * The *base case,* which when triggered will terminate the recursive process.
  * The *recursive case,* which is where the recursion will actually occur.

*fig : 1*
```c
int fact(int n)
{
  // base case
  if (n == 1)
  {
    return 1;
  }
  // recursive case
  else
  {
    return n * fact(n-1);
  }
}
```
And for the sake of having slightly cleaner and more elegant code, know that if we have single-line loops or single-line conditional branches, we can remove all the curly braces around them.

*fig: 2*
```c
int fact(int n)
{
  // base case
  if (n == 1)
      return 1;
  // recursive case
  else
    return n * fact(n-1);
}
```
The code above still has all the same functionality as in *fig: 1*, I'm just taking away the curly braces, because there's only one line inside of those conditional branches, so infact they behave identically.

`If n is equal to 1`, `return 1`. `Otherwise return n times the factorial of n minus 1`. So we are infact making the problem smaller `if n starts out as 5`, we're going to `return 5 times the factorial of 4`.
This is will help understand the *call stack* in the upcoming class.

* In general, but not alway's. recursive functions replace loops in non-recursive functions.
* It's also possible to have more than one base or recursive case, if the program might recurse or terminate in diffrent way's, depending on the input being passed in


fig: 1a - This version uses `recursion` to calculate
```c
int fact(int n)
{
  if (n == 1)
    return 1;
  else
    return n * fact(n-1)
}
```

fig: 1b - This version uses `iteration` to calculate, and notice we have to declare a variable an integer product. And then we loop. So lond as `n` is greater than 0, we keep multiplying that product by `n` and decrementing `n` until we calculate the product. So these functions do exactly the same thing. But they don't do it in the same way.  
```c
int fact2(int n)
{
  int product = 1;
  while(n > 0)
  {
    product *= n;
    n--;
  }
  return product;
}
```

* **Multiple base case**: The fibonacci number sequence is defined as follows:
  * The first element is 0.
  * The second element is 1.
  * The *nth*  element is the sum of the (*n-1*)th and (*n-1*)th elements.

* **Multiple recursive cases:** The Collatz conjecture.
* **The Collatz conjecture** is it applies to positive integers and speculates that it is always possible to get "back to 1" if you follow these steps:
  * If *n* is 1, stop.
  * Otherwise if *n* is even, repeat this process on *n/2*. `n/2`  (n divided by 2).
  * Otherwise, if *n* is odd, repeat this process on *3n +1*. `3 * n +1` (3 times n plus 1).

* **Exercise**
* Write a recursive function collatz(n) that calculates how many steps it takes to get to 1 if you start from n and recurse as indicated above. (Follow the steps up above)

```markdown
| n | collatz(n)  |                                         Steps                                                | 
|---|-------------|----------------------------------------------------------------------------------------------|
| 1 |      0      | 1                                                                                            |
| 2 |      1      | 2 -> 1                                                                                       |
| 3 |      7      | 3 -> 10 -> 5 -> 16 -> 8 -> 4 -> 2 -> 1                                                       |
| 4 |      2      | 4 -> 2 -> 1                                                                                  |
| 5 |      5      | 5 -> 16 -> 8 -> 4 -> 2 -> 1                                                                  |
| 6 |      8      | 6 -> 3 -> 10 -> 5 -> 16 -> 8 -> 4 -> 2 -> 1                                                  |
| 7 |     16      | 7 -> 22 -> 11 -> 34 -> 17 -> 52 -> 26 -> 13 -> 40 -> 20 -> 10 -> 5 -> 16 -> 8 -> 4 -> 2 -> 1 |
| 8 |      3      | 8 -> 4 -> 2 -> 1                                                                             |
|15 |     17      | 15 -> 46 -> 23 -> 70 -> ... -> 8 -> 4 -> 2 -> 1                                              |
|27 |     111     | 27 -> 82 -> 41 -> 124 -> ... -> 8 -> 4 -> 2 -> 1                                             |
|50 |     24      | 50 -> 25 -> 76 -> 38 -> ... -> 8 -> 4 -> 2 -> 1                                              |
```
* A Possible Definition of the Collatz function

```c
int collatz(int n)
{
  // base case
  if (n == 1)
    return 0;
  // even numbers
  else if ((n % 2) == 0)
    return 1 + collatz(n/2);
  // odd numbers
  else
    return 1 + collatz(3*n + 1;

}
```

---

## Merge Sort

* In merge sort the idea of the algorithm is to sort smaller array
and thencombine those arrays together (merge them) in sorted order.

* Merge sort leverages something called **recursion**, which we'll
touch on in more detail in a future video.

In pseudocode:
  * Sort the left half of the array (assuming n > 1)
  * Sort the right half of the array (assuming n > 1)
  * Merge the two halves together
A single-
element array must necessarily be sorted.


**Recap**
* **Worst-case scenario:** We have to split *n* elements up and then recombine them, effectively doubling the sorted subarrays as we build them up. (combining sorted 1-element arrays into 2-element arrays, combining sorted 2-element arrays into 4-element arrays...) So in the worst-case scenario the runtime of merge sort is **O(*n log n*)** which in general is going to be less than or faster than *n* squared.

* **Best-case scenario:** The array is already perfectly sorted. But we have split and recombine it back together with this algorithm. And in the bestst-case scenario the runtime of merge sort is **Ω(*n log n*)**. Again, it still *n* log *n*. So in the best-case scenario, it can be slower than say, bubble sort, where the array happens to be perfectly sorted. So as you may recall the omega there is *n*, and not *n* log *n*.

But in the worst-case or maybe even the average case, merge sort is actually going to be faster, at the exspense of maybe taking up more memory because we have to recombine and create new segments in memory for our sub-arrays. So merge sort is a really powerful tool to have in your toolbox once you understand recursion, because it can make the speed of sorting an array that much faster.


---

Documentation By: **Raymond C. TURNER**

Last Update: Tuesday 19th September 2023