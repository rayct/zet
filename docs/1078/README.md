# My Gripe With OOP - Bring Back C as the Foundational Language.

## C Is the basis of all languages.

## Really Open there Eye's.

I don't like it that some languages or libraries like like (or try to) hide/shield from the programmer what's actually going on under the hood.

Lets take for example the following snippet: 

## Why is the Next() method stateful?

You might be wondering why the `Next()` method was implemented as a stateful method? Couldn't the .NET Class Library designers figure out a way to generate a random number without requiring state? And what exactly is being stored or referenced by the Next() method?

These are fair questions. At a high level, computers are good at following specific instructions to create a reliable and repeatable outcome. To create the illusion of randomness, the developers of the `Next()` method decided to capture the date and time down to the fraction of a millisecond and use that to seed an algorithm that produces a different number each time. While not entirely random, it suffices for most applications. The state that is captured and maintained through the lifetime of the dice object is the seed value. Each subsequent call to the `Next()` method is rerunning the algorithm, but ensures that the seed changes so that the same value isn't (necessarily) returned.

To use the `Random.Next()` method, however, **you don't have to understand how it works.** ***(As Developer, Yes I do!)*** The important thing to know is that some methods require you to create an instance of a class before you call them, while others do not.

I understand that it helps with productivity, but this is the problem with some of the more complex production software outhere, is that, if the developer does not understand what they are are writing because there just hitting targets then all hell breaks loose. Because 9/10 thay have started learning an OOP language first sugar coated with Garbage collectors.

Fucking Learn C First, understand what Memory mangement is. Algorithms, Linked lists vs Array's, Linear Search, Binary Search. when to use them and when not to.

* Sorting: Bubble Sort, Selection Sort, Merge Sort. Asymptotic Notation: 
* Searching: Linear Search, Binary Search. 
* Sorting: Bubble Sort, Selection Sort, Merge Sort.
* Asymptotic Notation: 

## How can you determine whether you need to create an instance of a class before calling its methods?

One approach for determining whether a method is stateful or stateless is to consult the **documentation**. The **documentation** includes examples that show whether the method must be called from the object instance or directly from the class.

1. **DOCUMENTATION**!
1. **REFACTOR**!
1. **TEST**!

1. **DOCUMENTATION**!
1. **REFACTOR**!
1. **TEST**!

1. **DOCUMENTATION**!
1. **REFACTOR**!
1. **TEST**!

OFFICIAL DOCUMENTATION IS YOUR BEST **FUCKING** FREIND!

**Rant over for Now!**

To be Cont'd....


---

</br>

Documentation By: **Raymond C. TURNER**

Last Updated: Thursday 7th September 2023 @ 18:11 GMT