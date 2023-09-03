# The Coleman-Liau index in Python
The Coleman-Liau index is a readability test designed to gauge the understandability of English texts. It calculates a grade-level score based on the average number of letters per 100 words and the average number of sentences per 100 words. Here's a Python program to compute the Coleman-Liau index of a given text:

```python
import re

def count_letters(text):
    # Count the number of letters in the text (excluding spaces and punctuation)
    letters = re.findall(r'[a-zA-Z]', text)
    return len(letters)

def count_words(text):
    # Count the number of words in the text (assuming words are separated by spaces)
    words = text.split()
    return len(words)

def count_sentences(text):
    # Count the number of sentences in the text (assuming sentences end with ".", "!", or "?")
    sentences = re.split(r'[.!?]', text)
    return len(sentences)

def calculate_coleman_liau_index(text):
    letters = count_letters(text)
    words = count_words(text)
    sentences = count_sentences(text)

    # Calculate the average number of letters per 100 words
    L = (letters / words) * 100

    # Calculate the average number of sentences per 100 words
    S = (sentences / words) * 100

    # Calculate the Coleman-Liau index
    index = 0.0588 * L - 0.296 * S - 15.8

    return round(index)

if __name__ == "__main__":
    # Input the text for which you want to compute the Coleman-Liau index
    input_text = input("Enter the text: ")

    # Calculate the Coleman-Liau index
    coleman_liau_index = calculate_coleman_liau_index(input_text)

    # Determine the corresponding grade level
    if coleman_liau_index < 1:
        grade_level = "Preschool"
    elif coleman_liau_index >= 16:
        grade_level = "College Graduate"
    else:
        grade_level = f"Grade {coleman_liau_index}"

    # Display the Coleman-Liau index and grade level
    print(f"Coleman-Liau Index: {coleman_liau_index}")
    print(f"Corresponding Grade Level: {grade_level}")
```

*This program defines functions to count letters, words, and sentences in the input text and then calculates the Coleman-Liau index using the specified formula. It also determines the corresponding grade level based on the index. Simply run the program and enter the text when prompted to compute the Coleman-Liau index and grade level.*


---

# The Coleman-Liau index in C

The equivalent C program to calculate the Coleman-Liau index of a given text:

```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>

// Function to count the number of letters in the text
int count_letters(const char *text) {
    int count = 0;
    for (int i = 0; text[i]; i++) {
        if (isalpha(text[i])) {
            count++;
        }
    }
    return count;
}

// Function to count the number of words in the text
int count_words(const char *text) {
    int count = 0;
    int is_word = 0;  // Flag to track if we are inside a word

    for (int i = 0; text[i]; i++) {
        if (isalnum(text[i])) {
            if (!is_word) {
                count++;
                is_word = 1;
            }
        } else {
            is_word = 0;
        }
    }

    return count;
}

// Function to count the number of sentences in the text
int count_sentences(const char *text) {
    int count = 0;
    for (int i = 0; text[i]; i++) {
        if (text[i] == '.' || text[i] == '!' || text[i] == '?') {
            count++;
        }
    }
    return count;
}

// Function to calculate the Coleman-Liau index
double calculate_coleman_liau_index(const char *text) {
    int letters = count_letters(text);
    int words = count_words(text);
    int sentences = count_sentences(text);

    // Calculate the average number of letters per 100 words
    double L = ((double)letters / words) * 100.0;

    // Calculate the average number of sentences per 100 words
    double S = ((double)sentences / words) * 100.0;

    // Calculate the Coleman-Liau index
    double index = 0.0588 * L - 0.296 * S - 15.8;

    return index;
}

int main() {
    char input_text[1000];

    // Input the text for which you want to compute the Coleman-Liau index
    printf("Enter the text: ");
    fgets(input_text, sizeof(input_text), stdin);

    // Calculate the Coleman-Liau index
    double coleman_liau_index = calculate_coleman_liau_index(input_text);

    // Determine the corresponding grade level
    char *grade_level;
    if (coleman_liau_index < 1) {
        grade_level = "Preschool";
    } else if (coleman_liau_index >= 16) {
        grade_level = "College Graduate";
    } else {
        char grade_level_buffer[20];
        sprintf(grade_level_buffer, "Grade %.0lf", coleman_liau_index);
        grade_level = grade_level_buffer;
    }

    // Display the Coleman-Liau index and grade level
    printf("Coleman-Liau Index: %.2lf\n", coleman_liau_index);
    printf("Corresponding Grade Level: %s\n", grade_level);

    return 0;
}
```

This C program follows a similar structure to the Python program. It defines functions to count letters, words, and sentences in the input text, calculates the Coleman-Liau index, and determines the corresponding grade level. Compile and run this C program, and enter the text when prompted to compute the Coleman-Liau index and grade level.


---

Documentation By: **Raymond C. TURNER**

Last Updated: Sunday 3rd September 2023 @ 01:14 GMT