# ***GO*** A Tour of Go ported to Python

## Go version - Packages 1/17

Every Go program is made up of packages.

Programs start running in package main.

This program is using the packages with import paths "fmt" and "math/rand".

By convention, the package name is the same as the last element of the import path. For instance, the "math/rand" package comprises files that begin with the statement package rand.

```go 
package main

import (
	"fmt"
	"math/rand"
)

func main() {
	fmt.Println("My favorite number is", rand.Intn(10))
}

```

## Python Version - Packages 1/17

```python
def split(sum):
    x = sum * 4 // 9
    y = sum - x
    return x, y

print(split(17))
```

**Both of these programs will produce the same output:**

---

Documentation by: **Raymond C. TURNER**

Last Updated: Friday 25th August 2023 @ 18:44 BST