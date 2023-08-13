
# Command Line Random Number Generator


This Python program generates random numbers based on user inputs from the command line. It utilizes the `argparse` library to parse command line arguments.

## Prerequisites

Make sure you have the following libraries installed:

- `argparse`: Python's command-line argument parsing library.
- `random`: Python's random number generation library.

## Program Overview

The program prompts the user to input numbers, weights, and the number of samples from the command line. It then generates random numbers according to the provided inputs and displays them in the terminal.

## Code Explanation

### Importing Libraries

```python
import argparse
import random
```

- `argparse`: Provides the tools for parsing command line arguments.
- `random`: Allows random number generation.

### Generating Numbers

```python
def generate_numbers(numbers, weights, num_samples):
    try:
        numbers = [int(num) for num in numbers.split(",")]
        weights = [int(weight) for weight in weights.split(",")]

        random_numbers = random.choices(numbers, weights=weights, k=num_samples)
        return random_numbers
    except ValueError:
        print("Invalid input format. Please enter valid numbers and weights.")
        return []
```

This function takes the user-provided inputs for numbers, weights, and the number of samples, and generates random numbers based on the input weights and number of samples using the `random.choices` function.

```python
def main():
    numbers = input("Enter comma-separated list of numbers: ")
    weights = input("Enter comma-separated list of weights: ")
    num_samples = int(input("Enter the number of samples to generate: "))

    random_numbers = generate_numbers(numbers, weights, num_samples)

    if random_numbers:
        print("Generated Random Numbers:", ", ".join(map(str, random_numbers)))
```

The `main` function is the entry point of the program. It prompts the user to input numbers, weights, and the number of samples from the command line. It then calls the `generate_numbers` function to generate random numbers and displays the results.

```python
if __name__ == "__main__":
    main()
```

This block of code ensures that the `main` function is executed only when the script is run directly and not when it's imported as a module.

---

This Markdown document provides a detailed explanation of the Python code for the Command Line Version of the Random Number Generator. It describes how the program uses command line arguments to generate random numbers and display them in the terminal.


Documentation By: **Raymond C. TURNER**

Last Updated: 1 Day ago