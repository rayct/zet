# # Random Number Generator - GUI
## Protoype 2

It appears that the given sequence of numbers does not follow an obvious mathematical pattern, so generating an algorithm based on these numbers might be challenging. However, I can help you create a Python program using `tkinter` to generate more numbers based on user input. The program will take a number as input and generate a sequence of numbers using a simple formula.

Here's a Python program using `tkinter` that generates a sequence of numbers based on user input:

```python
import tkinter as tk

def generate_numbers(seed):
    numbers = [seed]
    for _ in range(10):  # Generate 10 more numbers
        next_number = (numbers[-1] * 2 + 1) % 100
        numbers.append(next_number)
    return numbers

def generate_sequence():
    try:
        seed = int(seed_entry.get())
        numbers = generate_numbers(seed)
        result_label.config(text="Generated sequence: " + " ".join(map(str, numbers)))
    except ValueError:
        result_label.config(text="Please enter a valid number.")

# Create the main application window
root = tk.Tk()
root.title("Number Sequence Generator")

# Create and place widgets
label = tk.Label(root, text="Enter a seed number:")
label.pack(pady=10)

seed_entry = tk.Entry(root)
seed_entry.pack()

generate_button = tk.Button(root, text="Generate Sequence", command=generate_sequence)
generate_button.pack(pady=10)

result_label = tk.Label(root, text="")
result_label.pack()

# Start the GUI event loop
root.mainloop()
```

Save this code in a `.py` file and run it using a Python interpreter. The program will create a GUI window with an entry field for the seed number and a button to generate the sequence. It will display the generated sequence of numbers based on the formula `(previous_number * 2 + 1) % 100`.

Keep in mind that this formula is just an example, and you can modify it to fit your specific needs or desired pattern for generating numbers.

Documentation By: **Raymond C. TURNER**

Last Updated: 1 Day ago