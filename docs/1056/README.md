## A small Gripe with Go's strict typing

```go
package main

import "fmt"

func swap(x, y string) (string, string) {
	return y, x
}

func main() {
	a, b := swap("hello", "world")
	fmt.Println(a, b)
}
```
The Go code provided above for the simple swap function is indeed a bit repetitive due to the need to repeat the type declaration for the return values. This is a characteristic of Go's strict and explicit type system.

Other programming languages, like Python, allow for more concise type hinting or provide features like tuple destructuring that can make the code less repetitive in cases like this.

However, it's important to note that Go's explicitness and strict typing also come with benefits, particularly in terms of code readability and avoiding ambiguity. The trade-off is that it can lead to more verbosity in certain cases, like the one you've highlighted.

So, while your observation is valid, it's also a reflection of Go's design principles and the trade-offs it makes in terms of code readability, maintainability, and type safety. Different languages make different trade-offs, and the choice of language often depends on the specific needs and preferences of the development team.

---

My point is that Unfortunately, Go does not provide a direct mechanism to create type aliases for tuples like you're suggesting. The repetition of the type name is a requirement in Go when defining multiple return values.

In Python, you can achieve what you're suggesting by using type hints and type aliases, but in Go, the repeated type declarations are necessary due to its strict typing system.

Your initial Go code:

```go
func swap(x, y string) (string, string) {
    return y, x
}
```

The equivalent Python code:

```python
from typing import Tuple

def swap(x: str, y: str) -> Tuple[str, str]:
    return y, x
```

In the Python code, the type hint `Tuple[str, str]` indicates that the function returns a tuple of two strings. Python's type hinting helps convey the structure of the returned values, but it doesn't eliminate the repetition of the type name I was curious to achieve in your proposed syntax.


---

Documentation By: **Raymond C. TURNER**

Last Updated: Wednesday 24th August 2023 @ 11:54 BST