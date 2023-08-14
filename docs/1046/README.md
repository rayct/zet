# Random Number Generator - GUI
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


---

# Random Number Generator - GUI
## Protoype 3

It seems like you've provided a sequence of numbers: 04, 06, 10, 13, 34. However, based on this sequence alone, it's challenging to discern a clear algorithm that generates the numbers. If you have any additional information or patterns that could help determine the algorithm, please provide them.

Nevertheless, I can help you create a Python program using `tkinter` that generates more numbers based on the given sequence. This program will simply provide the next number by incrementing the last number in the sequence by a fixed step. Here's a basic example:

```python
import tkinter as tk

class NumberGeneratorApp:
    def __init__(self, root):
        self.root = root
        self.root.title("Number Generator")

        self.sequence = [4, 6, 10, 13, 34]

        self.label = tk.Label(root, text="Generated Number:")
        self.label.pack(pady=10)

        self.generate_button = tk.Button(root, text="Generate", command=self.generate_number)
        self.generate_button.pack()

    def generate_number(self):
        if len(self.sequence) > 0:
            next_number = self.sequence[-1] + 1  # Increment the last number by 1
            self.sequence.append(next_number)
            self.label.config(text=f"Generated Number: {next_number}")

if __name__ == "__main__":
    root = tk.Tk()
    app = NumberGeneratorApp(root)
    root.mainloop()
```

This program sets up a basic `tkinter` window with a label that displays the generated number and a button to generate the next number in the sequence. Note that this example is based on a simple incrementing pattern and may not reflect the actual algorithm generating the given sequence.


Keep in mind that this formula is just an example, and you can modify it to fit your specific needs or desired pattern for generating numbers.

Documentation By: **Raymond C. TURNER**

Last Updated: 1 Day ago