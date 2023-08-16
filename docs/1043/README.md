
# Random Number Generator - GUI
## Protoype 2

This Python program utilizes the `tkinter` library to create a Graphical User Interface (GUI) for generating random numbers based on user inputs.

## Prerequisites

Make sure you have the following libraries installed:

- `tkinter`: Python's standard GUI library.
- `random`: Python's random number generation library.
- `os`: Python's operating system interface.

## Program Overview

The program creates a GUI window that allows users to input numbers, weights, and the number of samples. When the user clicks the "Generate Numbers" button, the program generates random numbers according to the provided inputs and displays them. Additionally, it logs the generated numbers to a log file for later reference.

## Code Explanation

### Importing Libraries

```python
import tkinter as tk
from tkinter import messagebox
import random
import os
```

- `tkinter`: Provides the tools to create GUI elements.
- `messagebox`: A sub-module from `tkinter` used to display pop-up message boxes.
- `random`: Allows random number generation.
- `os`: Provides a way to interact with the operating system.

### Generating Numbers

```python
def generate_numbers():
    """
    Generate random numbers based on the provided inputs and display them in the output text box.
    """
    try:
        input_numbers = [int(num) for num in num_entry.get().split(",")]
        input_weights = [int(weight) for weight in weight_entry.get().split(",")]
        num_samples = int(num_samples_entry.get())
```

This function is called when the "Generate Numbers" button is clicked. It takes the user-provided inputs for numbers, weights, and the number of samples.

- `input_numbers`: List of integer numbers entered by the user.
- `input_weights`: List of integer weights corresponding to each number.
- `num_samples`: Number of random samples to generate.

```python
        if len(input_numbers) != len(set(input_numbers)):
            messagebox.showerror("Input Error", "Duplicate numbers detected. Please provide unique numbers.")
            return
```

Check for duplicate numbers among the input numbers. If duplicates are found, show an error message in a pop-up box and return.

```python
        shuffled_numbers = input_numbers.copy()
        random.shuffle(shuffled_numbers)
```

Create a shuffled copy of the input numbers to ensure uniqueness in random selection.

```python
        random_numbers = random.choices(shuffled_numbers, weights=input_weights, k=num_samples)
```

Generate random numbers based on input weights and number of samples using the `random.choices` function.

```python
        output_text.config(state=tk.NORMAL)
        output_text.delete(1.0, tk.END)
        output_text.insert(tk.END, "Generated Random Numbers: " + ", ".join(map(str, random_numbers)) + "\n")
        output_text.config(state=tk.DISABLED)
```

Enable the output text box, clear its content, and insert the generated random numbers as text. Then disable the text box again to prevent further edits.

```python
        log_directory = "logs"
        if not os.path.exists(log_directory):
            os.makedirs(log_directory)
        log_filename = os.path.join(log_directory, f"log_{os.getpid()}.txt")
```

Create a directory named "logs" if it doesn't exist and generate a log filename based on the process ID.

```python
        with open(log_filename, "a", encoding="utf-8") as log_file:
            log_file.write("Generated Numbers: " + ", ".join(map(str, random_numbers)) + "\n")
```

Open the log file in append mode and write the generated random numbers along with a timestamp.

```python
    except ValueError:
        messagebox.showerror("Input Error", "Invalid input format. Please enter valid numbers and weights.")
```

Catch a ValueError in case of invalid input format and show an error message in a pop-up box.

### Opening Log File

```python
def open_log_file():
    """
    Open the log.txt file using the default text editor.
    """
    try:
        log_directory = "logs"
        log_filename = os.path.join(log_directory, f"log_{os.getpid()}.txt")
```

This function is called when the "Open Log File" button is clicked. It attempts to open the log file for viewing.

```python
        if os.name == "nt":
            os.system(f"start {log_filename}")  # For Windows
        elif os.name == "posix":
            os.system(f"open {log_filename}")  # For macOS
        else:
            os.system(f"xdg-open {log_filename}")  # For Linux
```

Use different commands to open the log file based on the operating system: `start` for Windows, `open` for macOS, and `xdg-open` for Linux.

```python
    except FileNotFoundError:
        messagebox.showerror("Error", "Log file not found.")
    except OSError as os_error:
        messagebox.showerror("Error", f"Error opening log file: {os_error}")
```

Handle exceptions if the log file is not found or an error occurs while attempting to open it.

### Creating the GUI

```python
root = tk.Tk()
root.title("Random Number Generator")
root.geometry("600x600")
```

Create the main GUI window with a title and dimensions.

```python
# Create labels and entry fields
tk.Label(root, text="Enter Numbers (comma-separated):").grid(row=0, column=0, padx=20, pady=10, sticky="e")
num_entry = tk.Entry(root)
# ... (Similar code for weight and num_samples entry fields)
```

Create labels and entry fields for users to input numbers, weights, and the number of samples.

```python
# Create Generate button
generate_button = tk.Button(root, text="Generate Numbers", command=generate_numbers)
# ... (Similar code for the open_log_button)
```

Create buttons for generating numbers and opening the log file. Associate them with their respective functions.

```python
# Create output text box
output_text = tk.Text(root, height=15, width=50, state=tk.DISABLED)
output_text.grid(row=5, column=0, columnspan=3, padx=20, pady=10)
```

Create a text box for displaying the generated random numbers.

```python
# Add a scrollbar to the output text box
scrollbar = tk.Scrollbar(root, command=output_text.yview)
scrollbar.grid(row=5, column=3, sticky="ns")
output_text.config(yscrollcommand=scrollbar.set)
```

Add a scrollbar to the output text box to enable scrolling.

```python
# Start the GUI event loop
root.mainloop()
```

Start the main event loop to display the GUI and handle user interactions.

---

This Markdown document provides a detailed explanation of the Python code and its corresponding program, which generates random numbers based on user inputs and displays them in a GUI window while also logging the generated numbers to a file.


Documentation By: **Raymond C. TURNER**

Last Updated: 1 Day ago