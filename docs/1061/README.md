# GO - A Tour of Go
## A more detailed breakdown for 'noobs' 

## Packages - 1/17

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

### A more detailed breakdown of the function:





---

**Named return values - 7/17()**

Go's return values may be named. If so, they are treated as variables defined at the top of the function.

These names should be used to document the meaning of the return values.

A return statement without arguments returns the named return values. This is known as a "naked" return.

Naked return statements should be used only in short functions, as with the example shown here. They can harm readability in longer functions.

```go
package main

import "fmt"

func split(sum int) (x, y int) {
	x = sum * 4 / 9
	y = sum - x
	return
}

func main() {
	fmt.Println(split(17))
}

```

## A more detailed breakdown of the function:

```go
func split(sum int) (x, y int) {
    x = sum * 4 / 9
    y = sum - x
    return
}
```

1. **Function Declaration:**
   ```go
   func split(sum int) (x, y int) {
   ```
   - `func`: Keyword indicating the declaration of a function.
   - `split`: Name of the function.
   - `(sum int)`: Input parameter of the function, an integer named `sum`.
   - `(x, y int)`: Return values of the function, both integers named `x` and `y`.

2. **Calculation of `x`:**
   ```go
   x = sum * 4 / 9
   ```
   - `x`: Variable used to store the calculated value.
   - `sum * 4 / 9`: The input `sum` is multiplied by 4 and then divided by 9. The result of this calculation is assigned to the variable `x`.

3. **Calculation of `y`:**
   ```go
   y = sum - x
   ```
   - `y`: Variable used to store the calculated value.
   - `sum - x`: The value of `x` (calculated previously) is subtracted from the input `sum`, and the result is assigned to the variable `y`.

4. **Return Statement:**
   ```go
   return
   ```
   - The `return` statement doesn't explicitly provide return values. However, due to the function's signature `(x, y int)` specifying the return values as `x` and `y`, the values stored in these variables are automatically returned.

In essence, this function takes an integer `sum` as input, calculates two values (`x` and `y`) based on the input, and returns them. The value of `x` is obtained by performing a mathematical operation on the input, while the value of `y` is derived from the difference between the input and `x`. The function's structure uses named return values, which allows the function to automatically return the values assigned to `x` and `y`.

---






---

Documentation by: **Raymond C. TURNER**

Last Updated: Monady 25th August 2023 @ 15:49 BST