# Number Sequence Generator v1.0.0
## Developed by: Raymond C. TURNER

The Number Sequence Generator is a Python application that allows users to generate unique number sequences based on a seed number. It provides a graphical user interface (GUI) built using the tkinter library.

## Features

- Generate a unique sequence of 10 random numbers based on a seed number.
- Option to switch between light and dark themes for the GUI.
- View and manage log files of generated sequences.
- Close the application gracefully.

## Table of Contents

- [Number Sequence Generator v1.0.0](#number-sequence-generator-v100)
  - [Developed by: Raymond C. TURNER](#developed-by-raymond-c-turner)
  - [Features](#features)
  - [Table of Contents](#table-of-contents)
  - [Installation](#installation)
  - [Usage](#usage)
  - [Themes](#themes)
  - [Log Files](#log-files)
  - [About](#about)
  - [License](#license)
- [CODE](#code)
    - [Number Sequence Generator v1.0.0](#number-sequence-generator-v100-1)
      - [Developed by: Raymond C. TURNER](#developed-by-raymond-c-turner-1)
  - [Installer Package Creation](#installer-package-creation)
- [User Guide - Mark Down Format](#user-guide---mark-down-format)
- [Number Sequence Generator v1.0.0-beta - User Guide](#number-sequence-generator-v100-beta---user-guide)
  - [Table of Contents](#table-of-contents-1)
  - [Introduction](#introduction)
    - [About the Number Sequence Generator](#about-the-number-sequence-generator)
    - [System Requirements](#system-requirements)
    - [Installation](#installation-1)
  - [Getting Started](#getting-started)
    - [Running the Program](#running-the-program)
    - [User Interface Overview](#user-interface-overview)
  - [Generating Number Sequences](#generating-number-sequences)
    - [Entering a Seed Number](#entering-a-seed-number)
    - [Generating a Sequence](#generating-a-sequence)
    - [Viewing Generated Sequences](#viewing-generated-sequences)
    - [Clearing Log Files](#clearing-log-files)
  - [Customization](#customization)
    - [Switching Themes](#switching-themes)
    - [Exiting the Application](#exiting-the-application)
  - [Troubleshooting](#troubleshooting)
    - [Common Issues and Solutions](#common-issues-and-solutions)
  - [About](#about-1)
    - [Application Information](#application-information)
    - [Developer Contact](#developer-contact)
  - [User Guide - Text Format](#user-guide---text-format)

## Installation

To use the Number Sequence Generator, follow these steps:

1. Make sure you have Python 3.10.8 installed.
2. Install the required libraries by running the following command:
   ```
   pip install tkinter ttkthemes
   ```
3. Download the code files or copy the code provided into a `.py` file.

## Usage

1. Run the script you've downloaded or created.
2. The main window of the application will open with the title "Number Sequence Generator."
3. Enter a seed number in the provided entry field.
4. Click the "Generate Unique Sequence" button to generate a sequence of 10 unique random numbers based on the seed.
5. The generated sequence will be displayed below the button.
6. You can toggle between light and dark themes using the "Toggle Theme" button.
7. Use the "Open Log File" button to view the log of generated sequences.
8. Use the "Clear Log File" button to clear the log file.
9. Use the "Close Log File" button to close the log file window.
10. To exit the application, either click the "Close Application" button or select "Exit" from the "File" menu.

## Themes

The application provides two themes: light and dark. You can switch between these themes by clicking the "Toggle Theme" button.

## Log Files

The application maintains a log of generated sequences. Each time you generate a sequence, the seed and the generated sequence will be appended to the log file. You can view the log by clicking the "Open Log File" button. The log window allows you to track your generated sequences over time.

You can also clear the log file by clicking the "Clear Log File" button.

## About

The "About" window provides information about the Number Sequence Generator application. It includes details such as the version, release date, Python version used, and the developer's information.

## License

This application is distributed under the [MIT License](LICENSE). You are free to modify and use the code for your own purposes.

---

For support or inquiries, please contact the developer:  
Raymond C. TURNER  
Website: [codestak.io](https://codestak.io)

# CODE

### Number Sequence Generator v1.0.0
#### Developed by: Raymond C. TURNER

```python
import tkinter as tk
from tkinter import scrolledtext, messagebox
import os
import random
from ttkthemes import ThemedStyle  # Import ThemedStyle from ttkthemes library


# Define log_text as a global variable
log_text = None

# Define log_window as a global variable
log_window = None


# Function to apply the selected theme
def apply_theme(theme):
    global log_text
    if theme == "light":
        root.config(bg="white")
        label.config(bg="white", fg="black")
        seed_entry.config(bg="white", fg="black")
        generate_button.config(bg="white", fg="black")
        open_log_button.config(bg="white", fg="black")
        close_log_button.config(bg="white", fg="black")
        clear_log_button.config(bg="white", fg="black")
        theme_button.config(bg="white", fg="black")
        close_button.config(bg="white", fg="black")
        if log_text:  # Check if log_text is defined
            log_text.config(bg="white", fg="black")
        result_label.config(bg="white", fg="black")
        root.tk_setPalette(background="white")
    elif theme == "dark":
        root.config(bg="black")
        label.config(bg="black", fg="white")
        seed_entry.config(bg="black", fg="white")
        generate_button.config(bg="black", fg="white")
        open_log_button.config(bg="black", fg="white")
        close_log_button.config(bg="black", fg="white")
        clear_log_button.config(bg="black", fg="white")
        theme_button.config(bg="black", fg="white")
        close_button.config(bg="black", fg="white")
        if log_text:  # Check if log_text is defined
            log_text.config(bg="black", fg="white")
        result_label.config(bg="black", fg="white")
        root.tk_setPalette(background="black")

    # Explicitly set the text color of the buttons for both light and dark themes
    generate_button.config(fg="black")
    open_log_button.config(fg="black")
    close_log_button.config(fg="black")
    clear_log_button.config(fg="black")
    theme_button.config(fg="black")
    close_button.config(fg="black")


# Toggle between light and dark themes
def toggle_theme():
    global current_theme
    current_theme = "light" if current_theme == "dark" else "dark"
    apply_theme(current_theme)


current_theme = "light"  # Default theme is light


def generate_numbers(seed):
    numbers = {seed}
    while len(numbers) < 11:  # Generate 10 unique numbers
        next_number = random.randint(0, 99)  # Generate a random number between 0 and 99
        numbers.add(next_number)
    return list(numbers)


def generate_sequence():
    try:
        seed = int(seed_entry.get())
        numbers = generate_numbers(seed)
        result_label.config(text="Generated sequence: " + " ".join(map(str, numbers)))

        # Append the generated sequence to a unique log file
        log_filename = f"log_{os.getpid()}.txt"
        log_directory = "logs"
        os.makedirs(log_directory, exist_ok=True)
        with open(os.path.join(log_directory, log_filename), "a") as log_file:
            log_file.write(
                "Seed: {}\nGenerated sequence: {}\n\n".format(
                    seed, " ".join(map(str, numbers))
                )
            )

    except ValueError:
        result_label.config(text="Please enter a valid number.")

        # Function to close the application


def close_application():
    if messagebox.askokcancel("Quit", "Do you really want to quit?"):
        root.destroy()


def open_log_file():
    global log_window

    if log_window:
        result_label.config(text="Log window already open.")
        messagebox.showerror("Error", "Log window is already open.")
        return

    log_directory = "logs"
    log_filename = f"log_{os.getpid()}.txt"
    log_filepath = os.path.join(log_directory, log_filename)

    log_window = tk.Toplevel(root)
    log_window.title("Log File")

    # Add a scrolled text widget with scroll bar
    global log_text
    log_text = scrolledtext.ScrolledText(log_window, wrap=tk.WORD)
    log_text.pack(fill=tk.BOTH, expand=True)

    def update_log_contents():
        try:
            with open(log_filepath, "r") as log_file:
                log_contents = log_file.read()
                log_text.delete("1.0", tk.END)
                log_text.insert(tk.END, log_contents)
        except FileNotFoundError:
            log_text.delete("1.0", tk.END)
            log_text.insert(tk.END, "Log file not found.")

        # Schedule the next update after a short delay (in milliseconds)
        log_window.after(1000, update_log_contents)

    # Bind the close event to the log window
    log_window.protocol("WM_DELETE_WINDOW", close_log_window)

    # Start the initial update and schedule subsequent updates
    update_log_contents()

# Function to close the log file window
def close_log_window():
    global log_window
    if log_window:
        log_window.destroy()
        log_window = None  # Reset log_window variable

def clear_log_file():
    try:
        log_directory = "logs"
        log_filename = f"log_{os.getpid()}.txt"
        log_filepath = os.path.join(log_directory, log_filename)

        if os.path.exists(log_filepath):
            os.remove(log_filepath)
            result_label.config(text="Log file cleared.")
        else:
            result_label.config(text="Log file not found.")

    except Exception as e:
        result_label.config(text="Error clearing log file.")

# Function to display the About window
def show_about_window():
    about_window = tk.Toplevel(root)
    about_window.title("About")
    about_text = "Number Sequence Generator\n\nVersion: 1.0\n\nDate: 15-08-2023\n\nPython 3.10.8\n\nttkthemes 3.2.2\n\nTcl/TK version 8.6\n\nDeveloped By: codestak.io\n\nAuthor: Raymond C. TURNER\n\nDescription: This application generates unique number sequences based on a seed number."
    about_label = tk.Label(about_window, text=about_text, padx=20, pady=20)
    about_label.pack()
    
    
# Create the main application window
root = tk.Tk()

# Set a custom icon for the main window
icon_path = (
    "path_to_your_icon_file.ico"  # Replace with the actual path to your icon file
)
root.iconbitmap(icon_path)

# Create a themed style
style = ThemedStyle(root)
style.set_theme("default")  # Set the theme to "default"

# Enlarge the UI to three times the original size
root.geometry("900x700")

# Create a custom title with padding for the icon
custom_title = "Number Sequence Generator         "  # Adjust padding as needed
root.title(custom_title)

# Create and place widgets
label = tk.Label(root, text="Enter a seed number:")
label.pack(pady=30)

seed_entry = tk.Entry(root)
seed_entry.pack()

generate_button = tk.Button(
    root, text="Generate Unique Sequence", command=generate_sequence
)
generate_button.pack(pady=20)

# Create a "Open Log" button on UI
open_log_button = tk.Button(root, text="Open Log File", command=open_log_file)
open_log_button.pack(pady=10)

# Create a "Clear Log" button on UI
clear_log_button = tk.Button(root, text="Clear Log File", command=clear_log_file)
clear_log_button.pack(pady=10)

# Create a "Close Log File" button on the UI
close_log_button = tk.Button(root, text="Close Log File", command=close_log_window)
close_log_button.pack(pady=10)

# Create a "Toggle Theme" theme switcher button on the UI
theme_button = tk.Button(root, text="Toggle Theme", command=toggle_theme)
theme_button.pack(pady=10)

# Create a "Close Application" button on the UI
close_button = tk.Button(root, text="Close Application", command=close_application)
close_button.pack(pady=10)

result_label = tk.Label(root, text="")
result_label.pack()

# Apply the initial theme
apply_theme(current_theme)

# Create a menu bar
menu_bar = tk.Menu(root)
root.config(menu=menu_bar)

# Create a File menu
file_menu = tk.Menu(menu_bar, tearoff=0)
menu_bar.add_cascade(label="File", menu=file_menu)
file_menu.add_command(label="Open Log File", command=open_log_file)
file_menu.add_command(label="Clear Log File", command=clear_log_file)
file_menu.add_separator()
file_menu.add_command(
    label="Close Application", command=close_application
)  # Add Close Application option
file_menu.add_separator()
file_menu.add_command(label="Exit", command=root.destroy)

# Create a Help menu
help_menu = tk.Menu(menu_bar, tearoff=0)
menu_bar.add_cascade(label="Help", menu=help_menu)
help_menu.add_command(label="About", command=show_about_window)

# Start the GUI event loop
root.mainloop()
```

---

## Installer Package Creation
Creating an installer package for a Python application involves bundling your code, dependencies, and any required assets into a distributable package that users can install on their systems. One common way to achieve this is by using a tool like `pyinstaller` or `cx_Freeze` to create standalone executable files or installable packages.

In this example, I'll demonstrate how to use `pyinstaller` to create a standalone executable for your Number Sequence Generator application.

1. **Install PyInstaller**: If you haven't already, you can install PyInstaller using the following command:

   ```bash
   pip install pyinstaller
   ```

2. **Create an Executable**:

   Open a terminal and navigate to the directory containing your script (`number_sequence_generator.py`). Then, use PyInstaller to create an executable:

   ```bash
   pyinstaller --onefile numgen.py
   ```

   This command will create a `dist` directory in your project folder, containing the standalone executable. Note that the `--onefile` option bundles everything into a single executable, which is more convenient for distribution.

3. **Distribute the Executable**:

   Once the executable is created, you can distribute it to users. They can simply run the executable without needing to install Python or any dependencies. You may want to provide instructions for running the executable and any additional files that might be required (such as your icon file).

Remember that this process might vary depending on your specific requirements and the platform you're targeting. You might need to customize the PyInstaller command or handle additional considerations for packaging, such as including external files or specifying application metadata.

Please note that while creating standalone executables can make distribution easier, it may result in larger file sizes compared to using a Python interpreter directly. Additionally, be sure to comply with licensing requirements for any libraries or assets you use in your application.

---


# User Guide - Mark Down Format

# Number Sequence Generator v1.0.0-beta - User Guide

## Table of Contents

1. [Introduction](#introduction)
   - About the Number Sequence Generator
   - System Requirements
   - Installation

2. [Getting Started](#getting-started)
   - Running the Program
   - User Interface Overview

3. [Generating Number Sequences](#generating-number-sequences)
   - Entering a Seed Number
   - Generating a Sequence
   - Viewing Generated Sequences
   - Clearing Log Files

4. [Customization](#customization)
   - Switching Themes
   - Exiting the Application

5. [Troubleshooting](#troubleshooting)
   - Common Issues and Solutions

6. [About](#about)
   - Application Information
   - Developer Contact

## Introduction

### About the Number Sequence Generator

The Number Sequence Generator is a simple Python-based application that allows you to generate unique number sequences based on a seed number. This guide provides instructions on how to install, use, and customize the application.

### System Requirements

- Windows 7 or later
- macOS (version)
- Linux (version)
- Python 3.10.8 or later

### Installation

1. Download the executable file ("number_sequence_generator.exe") from the provided source.
2. Double-click the executable file to run the application.

## Getting Started

### Running the Program

To start the Number Sequence Generator, follow these steps:

1. Locate the "number_sequence_generator.exe" file on your computer.
2. Double-click the executable file to launch the application.

### User Interface Overview

The application's user interface consists of several elements:

- Seed Entry: Enter a seed number in this field to generate a sequence.
- Generate Unique Sequence Button: Click this button to generate a sequence based on the entered seed number.
- Open Log File Button: View the log of generated sequences.
- Clear Log File Button: Clear the log file of generated sequences.
- Toggle Theme Button: Switch between light and dark themes.
- Close Application Button: Exit the application.
- Result Label: Displays the generated sequence or error messages.

## Generating Number Sequences

### Entering a Seed Number

1. Launch the application.
2. In the "Enter a seed number" field, type a numerical seed value.

### Generating a Sequence

1. Enter a seed number as described above.
2. Click the "Generate Unique Sequence" button.
3. The generated sequence will be displayed below the button.

### Viewing Generated Sequences

1. Click the "Open Log File" button to view the log of generated sequences.
2. The log window will display the list of previously generated sequences.

### Clearing Log Files

1. Click the "Clear Log File" button to remove the log of generated sequences.
2. Confirm the action if prompted.

## Customization

### Switching Themes

- Click the "Toggle Theme" button to switch between light and dark themes.

### Exiting the Application

- Click the "Close Application" button or select "Exit" from the "File" menu to exit the application.

## Troubleshooting

### Common Issues and Solutions

- **Issue**: Error message "Please enter a valid number."
  - **Solution**: Ensure you have entered a valid numerical seed value.

- **Issue**: Log window not opening.
  - **Solution**: Make sure no other log window is open. Try clicking "Open Log File" again.

## About

### Application Information

- Application Name: Number Sequence Generator
- Version: 1.0.0-beta
- Release Date: August 16, 2023

### Developer Contact

- Developer: Raymond C. TURNER
- Website: [codestak.io](https://codestak.io)
- Email: [support@codestak.io](mailto:support@codestak.io)

---


## User Guide - Text Format
Number Sequence Generator v1.0.0-beta - User Guide

Table of Contents

1. Introduction
   - About the Number Sequence Generator
   - System Requirements
   - Installation

2. Getting Started
   - Running the Program
   - User Interface Overview

3. Generating Number Sequences
   - Entering a Seed Number
   - Generating a Sequence
   - Viewing Generated Sequences
   - Clearing Log Files

4. Customization
   - Switching Themes
   - Exiting the Application

5. Troubleshooting
   - Common Issues and Solutions

6. About
   - Application Information
   - Developer Contact

Introduction

About the Number Sequence Generator

The Number Sequence Generator is a simple Python-based application that allows you to generate unique number sequences based on a seed number. This guide provides instructions on how to install, use, and customize the application.

System Requirements

- Windows 7 or later
- macOS (version)
- Linux (version)
- Python 3.10.8 or later

Installation

1. Download the executable file ("number_sequence_generator.exe") from the provided source.
2. Double-click the executable file to run the application.

Getting Started

Running the Program

To start the Number Sequence Generator, follow these steps:

1. Locate the "number_sequence_generator.exe" file on your computer.
2. Double-click the executable file to launch the application.

User Interface Overview

The application's user interface consists of several elements:

- Seed Entry: Enter a seed number in this field to generate a sequence.
- Generate Unique Sequence Button: Click this button to generate a sequence based on the entered seed number.
- Open Log File Button: View the log of generated sequences.
- Clear Log File Button: Clear the log file of generated sequences.
- Toggle Theme Button: Switch between light and dark themes.
- Close Application Button: Exit the application.
- Result Label: Displays the generated sequence or error messages.

Generating Number Sequences

Entering a Seed Number

1. Launch the application.
2. In the "Enter a seed number" field, type a numerical seed value.

Generating a Sequence

1. Enter a seed number as described above.
2. Click the "Generate Unique Sequence" button.
3. The generated sequence will be displayed below the button.

Viewing Generated Sequences

1. Click the "Open Log File" button to view the log of generated sequences.
2. The log window will display the list of previously generated sequences.

Clearing Log Files

1. Click the "Clear Log File" button to remove the log of generated sequences.
2. Confirm the action if prompted.

Customization

Switching Themes

- Click the "Toggle Theme" button to switch between light and dark themes.

Exiting the Application

- Click the "Close Application" button or select "Exit" from the "File" menu to exit the application.

Troubleshooting

Common Issues and Solutions

- Issue: Error message "Please enter a valid number."
  Solution: Ensure you have entered a valid numerical seed value.

- Issue: Log window not opening.
  Solution: Make sure no other log window is open. Try clicking "Open Log File" again.

About

Application Information

- Application Name: Number Sequence Generator
- Version: 1.0.0
- Release Date: August 15, 2023

Developer Contact

- Developer: Raymond C. TURNER
- Website: codestak.io
- Email: support@codestak.io

Documentation by: **Raymond C. TURNER**

Last Updated: 1 Day ago