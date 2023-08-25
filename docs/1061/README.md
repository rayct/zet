# ***GO*** - A Tour of Go
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

### A break down of the Go code step by step: 1/17

1. **Package Declaration:**
    ```go
    package main
    ```
    This line defines the package name. In Go, the `main` package is special and serves as the entry point for the executable program. All Go programs must have a `main` package with a `main` function.

2. **Import Statements:**
    ```go
    import (
        "fmt"
        "math/rand"
    )
    ```
    Here, the code is importing two packages: `fmt` and `math/rand`. The `fmt` package provides functions for formatting and printing text, while the `math/rand` package allows generating random numbers.

3. **Main Function:**
    ```go
    func main() {
        fmt.Println("My favorite number is", rand.Intn(10))
    }
    ```
    The `main()` function is the entry point of the program, where the execution starts. Here's what's happening within this function:

    - `fmt.Println("My favorite number is", rand.Intn(10))`: This line prints a string concatenated with a random integer generated using `rand.Intn(10)`. The `rand.Intn(10)` function call generates a random non-negative integer less than 10.

        - `rand.Intn(10)` generates a random integer between 0 (inclusive) and 10 (exclusive).
        - The generated number is then printed along with the string "My favorite number is" using `fmt.Println`.

In summary, this program prints a message along with a randomly generated favorite number between 0 and 9 every time it is executed. The behavior is a simple example of utilizing the `fmt` and `math/rand` packages to perform basic output and random number generation in Go.

---

## Imports - 2/17

This code groups the imports into a parenthesized, "factored" import statement.

You can also write multiple import statements, like:

```go
import "fmt"
import "math"
```
But it is good style to use the factored import statement.

```go
package main

import (
	"fmt"
	"math"
)

func main() {
	fmt.Printf("Now you have %g problems.\n", math.Sqrt(7))
}
```

### A break down of the Go code step by step: 2/17

Of course! Let's break down the provided Go code in more detail:

1. **Package Declaration:**
    ```go
    package main
    ```
    This is the declaration of the package. In Go, the `main` package is a special package name that indicates that this is an executable program, and it should have a `main()` function as its entry point.

2. **Import Statements:**
    ```go
    import (
        "fmt"
        "math"
    )
    ```
    The code is importing two packages: `fmt` and `math`. The `fmt` package is used for formatting and printing text, and the `math` package provides various mathematical functions, including the `Sqrt` function used in this code.

3. **Main Function:**
    ```go
    func main() {
        fmt.Printf("Now you have %g problems.\n", math.Sqrt(7))
    }
    ```
    The `main()` function is the entry point of the program, where the execution starts. Here's what's happening within this function:

    - `fmt.Printf(...)`: This line is using the `fmt` package's `Printf` function to format and print a string. The format string is `"Now you have %g problems.\n"`, where `%g` is a placeholder for a floating-point number in a compact form.

    - `math.Sqrt(7)`: This part of the code is using the `math` package's `Sqrt` function to calculate the square root of 7. The result of this calculation is a floating-point number.

    - The `Printf` function combines the format string and the result of `math.Sqrt(7)` to create the final output string. The `%g` placeholder is replaced with the calculated square root value.

    - The newline character `\n` is added at the end of the string to start a new line after printing.

So, when you run this program, it will print the message "Now you have X problems." where X is the square root of 7, formatted as a floating-point number. The use of the `fmt` and `math` packages demonstrates the capability of formatting text and performing mathematical calculations in Go.


## Exported names - 3/17

In Go, a name is exported if it begins with a capital letter. For example, `Pizza` is an exported name, as is `Pi`, which is exported from the `math` package.

`pizza` and `pi` do not start with a capital letter, so they are not exported.

When importing a package, you can refer only to its exported names. Any "unexported" names are not accessible from outside the package.

Run the code. Notice the error message.

To fix the error, rename `math.pi` to `math.Pi` and try it again.































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