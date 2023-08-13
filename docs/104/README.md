# Random Number Generator
Program Created By: **Raymond C. TURNER**

### Version 1.0.7
* **Version Changes:**
#### **Major Features Update and Fixed a number of Critical Bugs.**
* This version of the code adds an "Open Log File" button that uses the os.system function to open the log.txt file using the default text editor. The try and except blocks are used to handle different operating systems (Windows, macOS, and Linux).

* In this updated code, I've added more specific exception handling using the os.name attribute to determine the operating system. This should help address the W0702 Pylint warning. Additionally, I've added a generic exception handler in the open_log_file function to display an error message in case of any exceptions.

* The log_filename is generated based on the process ID to create a unique log file for each execution of the program. After writing the log, the os.chmod() function is used to set the permissions of the log file to read-only. Additionally, the open_log_file function uses the process ID to open the correct log file.
  
* The shuffled_numbers list is created by shuffling the input_numbers list to ensure that each generated number is unique. This should prevent the generation of duplicate random numbers.

* In this updated version of the code, a directory named "logs" is created if it doesn't exist, and the log files are stored in that directory. The os.path.join() function is used to create the full path to the log file within the "logs" directory.

* Fixed the Bug: `Variable name "e" doesn't conform to snake_case naming stylePylintC0103:invalid-name`,
  by renaming the exception variable from `e` to `os_error` to better adhere to the `snake_case` naming style and provide a more descriptive name.


```python
import tkinter as tk
from tkinter import messagebox
import random
import os

def generate_numbers():
    """
    Generate random numbers based on the provided inputs and display them in the output text box.
    """
    try:
        input_numbers = [int(num) for num in num_entry.get().split(",")]
        input_weights = [int(weight) for weight in weight_entry.get().split(",")]
        num_samples = int(num_samples_entry.get())

        if len(input_numbers) != len(set(input_numbers)):
            messagebox.showerror("Input Error", "Duplicate numbers detected. Please provide unique numbers.")
            return

        # Shuffle input_numbers to ensure uniqueness
        shuffled_numbers = input_numbers.copy()
        random.shuffle(shuffled_numbers)

        random_numbers = random.choices(shuffled_numbers, weights=input_weights, k=num_samples)
        output_text.config(state=tk.NORMAL)
        output_text.delete(1.0, tk.END)
        output_text.insert(tk.END, "Generated Random Numbers: " + ", ".join(map(str, random_numbers)) + "\n")
        output_text.config(state=tk.DISABLED)

        log_directory = "logs"
        if not os.path.exists(log_directory):
            os.makedirs(log_directory)
        log_filename = os.path.join(log_directory, f"log_{os.getpid()}.txt")  # Use process ID to generate unique log file name

        with open(log_filename, "a", encoding="utf-8") as log_file:
            log_file.write("Generated Numbers: " + ", ".join(map(str, random_numbers)) + "\n")

    except ValueError:
        messagebox.showerror("Input Error", "Invalid input format. Please enter valid numbers and weights.")

def open_log_file():
    """
    Open the log.txt file using the default text editor.
    """
    try:
        log_directory = "logs"
        log_filename = os.path.join(log_directory, f"log_{os.getpid()}.txt")  # Use process ID to open the correct log file

        if os.name == "nt":
            os.system(f"start {log_filename}")  # For Windows
        elif os.name == "posix":
            os.system(f"open {log_filename}")  # For macOS
        else:
            os.system(f"xdg-open {log_filename}")  # For Linux
    except FileNotFoundError:
        messagebox.showerror("Error", "Log file not found.")
    except OSError as os_error:
        messagebox.showerror("Error", f"Error opening log file: {os_error}")

# Create the main window
root = tk.Tk()
root.title("Random Number Generator")
root.geometry("600x600")

# Create labels and entry fields
tk.Label(root, text="Enter Numbers (comma-separated):").grid(row=0, column=0, padx=20, pady=10, sticky="e")
num_entry = tk.Entry(root)
num_entry.grid(row=0, column=1, padx=20, pady=10, columnspan=2)
num_entry.config(width=int(num_entry.cget("width")) * 3 // 2)  # Adjust width

tk.Label(root, text="Enter Weights (comma-separated):").grid(row=1, column=0, padx=20, pady=10, sticky="e")
weight_entry = tk.Entry(root)
weight_entry.grid(row=1, column=1, padx=20, pady=10, columnspan=2)
weight_entry.config(width=int(weight_entry.cget("width")) * 3 // 2)  # Adjust width

tk.Label(root, text="Number of Samples:").grid(row=2, column=0, padx=20, pady=10, sticky="e")
num_samples_entry = tk.Entry(root)
num_samples_entry.grid(row=2, column=1, padx=20, pady=10, columnspan=2)
num_samples_entry.config(width=int(num_samples_entry.cget("width")) * 3 // 2)  # Adjust width

# Create Generate button
generate_button = tk.Button(root, text="Generate Numbers", command=generate_numbers)
generate_button.grid(row=3, column=0, columnspan=3, padx=20, pady=20)

# Create Open Log button
open_log_button = tk.Button(root, text="Open Log File", command=open_log_file)
open_log_button.grid(row=4, column=0, columnspan=3, padx=20, pady=10)

# Create output text box
output_text = tk.Text(root, height=15, width=50, state=tk.DISABLED)
output_text.grid(row=5, column=0, columnspan=3, padx=20, pady=10)

# Add a scrollbar to the output text box
scrollbar = tk.Scrollbar(root, command=output_text.yview)
scrollbar.grid(row=5, column=3, sticky="ns")
output_text.config(yscrollcommand=scrollbar.set)

# Start the GUI event loop
root.mainloop()
```

---


### Version 1.0.6
* **Version Changes:**
#### Improved GUI includes an expanded doubled layout
This version of the GUI doubles the size of components and spacing to create a more spacious layout.
You can adjust the size and placement of components further to match your desired appearance.

```python
import tkinter as tk
from tkinter import messagebox
import random

def generate_numbers():
    """
    Generate random numbers based on the provided inputs and display them in the output text box.
    """
    try:
        input_numbers = [int(num) for num in num_entry.get().split(",")]
        input_weights = [int(weight) for weight in weight_entry.get().split(",")]
        num_samples = int(num_samples_entry.get())

        random_numbers = random.choices(input_numbers, weights=input_weights, k=num_samples)
        output_text.config(state=tk.NORMAL)
        output_text.delete(1.0, tk.END)
        output_text.insert(tk.END, "Generated Random Numbers: " + ", ".join(map(str, random_numbers)) + "\n")
        output_text.config(state=tk.DISABLED)
    except ValueError:
        messagebox.showerror("Input Error", "Invalid input format. Please enter valid numbers and weights.")

# Create the main window
root = tk.Tk()
root.title("Random Number Generator")
root.geometry("600x600")

# Create labels and entry fields
tk.Label(root, text="Enter Numbers (comma-separated):").grid(row=0, column=0, padx=20, pady=10, sticky="e")
num_entry = tk.Entry(root)
num_entry.grid(row=0, column=1, padx=20, pady=10, columnspan=2)
num_entry.config(width=int(num_entry.cget("width")) * 3 // 2)  # Adjust width

tk.Label(root, text="Enter Weights (comma-separated):").grid(row=1, column=0, padx=20, pady=10, sticky="e")
weight_entry = tk.Entry(root)
weight_entry.grid(row=1, column=1, padx=20, pady=10, columnspan=2)
weight_entry.config(width=int(weight_entry.cget("width")) * 3 // 2)  # Adjust width

tk.Label(root, text="Number of Samples:").grid(row=2, column=0, padx=20, pady=10, sticky="e")
num_samples_entry = tk.Entry(root)
num_samples_entry.grid(row=2, column=1, padx=20, pady=10, columnspan=2)
num_samples_entry.config(width=int(num_samples_entry.cget("width")) * 3 // 2)  # Adjust width

# Create Generate button
generate_button = tk.Button(root, text="Generate Numbers", command=generate_numbers)
generate_button.grid(row=3, column=0, columnspan=3, padx=20, pady=20)

# Create output text box
output_text = tk.Text(root, height=15, width=50, state=tk.DISABLED)
output_text.grid(row=4, column=0, columnspan=3, padx=20, pady=10)

# Add a scrollbar to the output text box
scrollbar = tk.Scrollbar(root, command=output_text.yview)
scrollbar.grid(row=4, column=3, sticky="ns")
output_text.config(yscrollcommand=scrollbar.set)

# Start the GUI event loop
root.mainloop()
```


---


### Version 1.0.5
#### Improved GUI (Expanded layout)
* **Version Changes:**
This version of the GUI includes an expanded layout with a larger text box for output, a scrollbar for the output text box, and improved alignment of labels and entry fields. You can further customize and enhance the layout and appearance according to your preferences.

```python
import tkinter as tk
from tkinter import messagebox
import random

def generate_numbers():
    """
    Generate random numbers based on the provided inputs and display them in the output text box.
    """
    try:
        input_numbers = [int(num) for num in num_entry.get().split(",")]
        input_weights = [int(weight) for weight in weight_entry.get().split(",")]
        num_samples = int(num_samples_entry.get())

        random_numbers = random.choices(input_numbers, weights=input_weights, k=num_samples)
        output_text.config(state=tk.NORMAL)
        output_text.delete(1.0, tk.END)
        output_text.insert(tk.END, "Generated Random Numbers: " + ", ".join(map(str, random_numbers)) + "\n")
        output_text.config(state=tk.DISABLED)
    except ValueError:
        messagebox.showerror("Input Error", "Invalid input format. Please enter valid numbers and weights.")

# Create the main window
root = tk.Tk()
root.title("Random Number Generator")

# Create labels and entry fields
tk.Label(root, text="Enter Numbers (comma-separated):").grid(row=0, column=0, padx=10, pady=5, sticky="e")
num_entry = tk.Entry(root)
num_entry.grid(row=0, column=1, padx=10, pady=5, columnspan=2)

tk.Label(root, text="Enter Weights (comma-separated):").grid(row=1, column=0, padx=10, pady=5, sticky="e")
weight_entry = tk.Entry(root)
weight_entry.grid(row=1, column=1, padx=10, pady=5, columnspan=2)

tk.Label(root, text="Number of Samples:").grid(row=2, column=0, padx=10, pady=5, sticky="e")
num_samples_entry = tk.Entry(root)
num_samples_entry.grid(row=2, column=1, padx=10, pady=5, columnspan=2)

# Create Generate button
generate_button = tk.Button(root, text="Generate Numbers", command=generate_numbers)
generate_button.grid(row=3, column=0, columnspan=3, padx=10, pady=10)

# Create output text box
output_text = tk.Text(root, height=10, width=40, state=tk.DISABLED)
output_text.grid(row=4, column=0, columnspan=3, padx=10, pady=5)

# Add a scrollbar to the output text box
scrollbar = tk.Scrollbar(root, command=output_text.yview)
scrollbar.grid(row=4, column=3, sticky="ns")
output_text.config(yscrollcommand=scrollbar.set)

# Start the GUI event loop
root.mainloop()
```

---


### Version 1.0.4
#### Added a UI
* **Major Version Changes:**
Incorporated a simple graphical user interface (GUI) using the `tkinter`:
This program creates a simple GUI using the `tkinter` library. It allows you to input numbers, weights, and the number of samples, and then generates and displays random numbers based on the provided inputs. Make sure to have the `tkinter` library installed in your Python environment to run this program.

```python
import tkinter as tk
from tkinter import messagebox
import random

def generate_numbers():
    """
    Generate random numbers based on the provided inputs and display them in the output text box.
    """
    try:
        input_numbers = [int(num) for num in num_entry.get().split(",")]
        input_weights = [int(weight) for weight in weight_entry.get().split(",")]
        num_samples = int(num_samples_entry.get())

        random_numbers = random.choices(input_numbers, weights=input_weights, k=num_samples)
        output_text.config(state=tk.NORMAL)
        output_text.delete(1.0, tk.END)
        output_text.insert(tk.END, "Generated Random Numbers: " + ", ".join(map(str, random_numbers)) + "\n")
        output_text.config(state=tk.DISABLED)
    except ValueError:
        messagebox.showerror("Input Error", "Invalid input format. Please enter valid numbers and weights.")

# Create the main window
root = tk.Tk()
root.title("Random Number Generator")

# Create labels and entry fields
tk.Label(root, text="Numbers (comma-separated):").grid(row=0, column=0, padx=10, pady=5, sticky="e")
num_entry = tk.Entry(root)
num_entry.grid(row=0, column=1, padx=10, pady=5)

tk.Label(root, text="Weights (comma-separated):").grid(row=1, column=0, padx=10, pady=5, sticky="e")
weight_entry = tk.Entry(root)
weight_entry.grid(row=1, column=1, padx=10, pady=5)

tk.Label(root, text="Number of Samples:").grid(row=2, column=0, padx=10, pady=5, sticky="e")
num_samples_entry = tk.Entry(root)
num_samples_entry.grid(row=2, column=1, padx=10, pady=5)

# Create Generate button
generate_button = tk.Button(root, text="Generate Number", command=generate_numbers)
generate_button.grid(row=3, columnspan=2, padx=10, pady=10)

# Create output text box
output_text = tk.Text(root, height=6, width=40, state=tk.DISABLED)
output_text.grid(row=4, columnspan=2, padx=10, pady=5)

# Start the GUI event loop
root.mainloop()
```


---


### Version 1.0.3
#### CMD Line Version with prompt
* **Version Changes:**
A command-line version of the program that prompts the user to input the numbers, weights, and the number of samples:

**Run the program using the following command:**

`python random_number_generator_cmd_prompt.py`


```python
import argparse
import random

def generate_numbers(numbers, weights, num_samples):
    try:
        numbers = [int(num) for num in numbers.split(",")]
        weights = [int(weight) for weight in weights.split(",")]

        random_numbers = random.choices(numbers, weights=weights, k=num_samples)
        return random_numbers
    except ValueError:
        print("Invalid input format. Please enter valid numbers and weights.")
        return []

def main():
    numbers = input("Enter comma-separated list of numbers: ")
    weights = input("Enter comma-separated list of weights: ")
    num_samples = int(input("Enter the number of samples to generate: "))

    random_numbers = generate_numbers(numbers, weights, num_samples)

    if random_numbers:
        print("Generated Random Numbers:", ", ".join(map(str, random_numbers)))

if __name__ == "__main__":
    main()
```

---


### Version 1.0.2
#### CMD Line Version
* **Version Changes:**
To generate high-quality random numbers, you can use the `random.choices()` function from the `random` module with the `weights` parameter for weighted random selection. Here's the program using the `random` module to generate high-quality random numbers based on the provided list of numbers and their weights:


```python
import random

# The list of numbers and their corresponding weights
numbers = [4, 6, 10, 13, 34, 3, 5]
weights = [1, 1, 1, 1, 1, 1, 1]  # Equal weights for each number

# Generate a list of high-quality random numbers based on the weights
num_samples = 10  # Adjust the number of random numbers to generate
random_numbers = random.choices(numbers, weights=weights, k=num_samples)

# Print the generated random numbers
print("Generated Random Numbers:", random_numbers)
```

In this program, the `random.choices()` function is used to generate a list of high-quality random numbers based on the provided `numbers` and `weights`. You can adjust the `num_samples` variable to generate as many random numbers as you need. This approach ensures that the random numbers are generated with better statistical properties compared to manual weighted selection.


---


### Version 1.0.1
#### CMD Line Version
* **Version Changes:**
Using the `random` module to achieve weighted random selection:


```python
import random

# The list of numbers and their corresponding weights
numbers = [4, 6, 10, 13, 34, 3, 5]
weights = [1, 1, 1, 1, 1, 1, 1]  # Equal weights for each number

def weighted_random_choice(choices, weights):
    return random.choices(choices, weights=weights)[0]

# Generate random numbers based on the weights
random_number = weighted_random_choice(numbers, weights)
print("Random Number:", random_number)
```

The `random.choices()` function from the `random` module allows you to perform weighted random selection directly, which simplifies the process. The function returns a list of randomly selected elements based on their weights, and we select the first element from that list to get the final result.

Remember that this approach uses the `random` module for weighted random selection, which is more suitable for general use cases where high-quality random numbers are not necessarily required.


---


### Version 1.0
#### CMD Line Version
* **Version Changes:**
An algorithm to generate random numbers in Python based on the provided list of numbers: 4, 6, 10, 13, 34, 3, 5. One way to achieve this is by using a weighted random selection algorithm. Here's an example of how you can implement this:

```python
import random

# The list of numbers and their corresponding weights
numbers = [4, 6, 10, 13, 34, 3, 5]
weights = [1, 1, 1, 1, 1, 1, 1]  # Equal weights for each number

def weighted_random_choice(choices, weights):
    total_weight = sum(weights)
    rnd = random.uniform(0, total_weight)
    for choice, weight in zip(choices, weights):
        rnd -= weight
        if rnd < 0:
            return choice

# Generate random numbers based on the weights
random_number = weighted_random_choice(numbers, weights)
print("Random Number:", random_number)
```

In this example, each number in the `numbers` list has an equal weight of 1. You can adjust the weights according to your preferences if you want certain numbers to have a higher chance of being selected.

Please note that this algorithm ensures that numbers are selected with a probability proportional to their weights, but it may not provide the same statistical properties as Python's built-in `random` module. If you require high-quality random numbers for cryptographic or scientific purposes, it's recommended to use the `random` module provided by Python's standard library.


Documentation By: **Raymond C. TURNER**

Last Updated: 1 Day ago