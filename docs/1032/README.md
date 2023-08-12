# CS50P - 2022
**Harvard - CS50P An introduction to programming using a language called Python.**

Learn how to read and write code as well as how to test and "debug" it. Designed for students with or without prior programming experience who'd like to learn Python specifically. Learn about functions, arguments, and return values (oh my!); variables and types; conditionals and Boolean expressions; and loops. Learn how to handle exceptions, find and fix bugs, and write unit tests; use third-party libraries; validate and extract data with regular expressions; model real-world entities with classes, objects, methods, and properties; and read and write files. Hands-on opportunities for lots of practice. Exercises inspired by real-world programming problems.

* Python Course Sylabus
    * Functions and Variables
    * Explicit
    * Constants
    * Conditionals
    * Loops
    * Exceptions
    * Libraries
    * Unit Tests
    * File I/O
    * Regular Expressions
    * Object-Oriented Programming

## Problem Sets
### Week 0 - Functions and Variables
??? abstract "Problem Set 0 - Functions and Variables"

    * Indoor Voice `Completed`
    * Playback Speed `Completed`
    * Making Faces `Completed`
    * Einstein
    * Tip Calculator `Completed`



### Week 1 - Conditionals
??? abstract "Problem Set 1 - Conditionals"

    * Deep Thought `Completed`
    * Home Federal Savings Bank `Completed`
    * File Extensions `Completed`
    * Math Interpreter
    * Meal Time   



### Week 2 - Loops
??? abstract "Problem Set 2 - Loops"

    * camelCase
    * Coke Machine
    * Just setting up my twttr
    * Vanity Plates
    * Nutrition Facts




### Week 3 - Exceptions
??? abstract "Problem Set 3 - Exceptions"

    * Fuel Gauge
    * Felipe’s Taqueria
    * Grocery List
    * Outdated




### Week 4 - Libraries
??? abstract "Problem Set 4 - Libraries"

    * Emojize
    * Frank, Ian and Glen’s Letters
    * Adieu, Adieu
    * Guessing Game
    * Little Professor
    * Bitcoin Price Index



### Week 5 - Unit Tests
??? abstract "Problem Set 5 - Unit Tests"

    * Testing my twttr
    * Back to the Bank
    * Re-requesting a Vanity Plate
    * Refueling



### Week 6 - File I/O
??? abstract "Problem Set 6 - File I/O"

    * Lines of Code
    * Pizza Py
    * Scourgify
    * CS50 P-Shirt



### Week 7 - Regular Expressions
??? abstract "Problem Set 7 - Regular Expressions"

    * NUMB3RS
    * Watch on YouTube
    * Working 9 to 5
    * Regular, um, Expressions
    * Response Validation



### Week 8 - Object-Oriented Programming
??? abstract "Problem Set 8 - Object-Oriented Programming"

    * Seasons of Love
    * Cookie Jar
    * CS50 Shirtificate



### Week 9 - Et Cetera
??? abstract "Problem Set 9 - Et Cetera"

    * Final Project

    Once you have solved each of the course’s problem sets, it’s time to implement your final project, a Python program of your very own! The design and implementation of your project is entirely up to you, albeit subject to these requirements:

    * Your project must be implemented in Python.
    * Your project must have a main function and three or more additional functions. At least three of those additional functions must be accompanied by tests that can be executed with pytest.
      * Your main function must be in a file called project.py, which should be in the “root” (i.e., top-level folder) of your project.
      * Your 3 required custom functions other than main must also be in project.py and defined at the same indentation level as main (i.e., not nested under any classes or functions).
      * Your test functions must be in a file called test_project.py, which should also be in the “root” of your project. Be sure they have the same name as your custom functions, prepended with test_ (test_custom_function, for example, where custom_function is a function you’ve implemented in project.py).
      * You are welcome to implement additional classes and functions as you see fit beyond the minimum requirement.
    Implementing your project should entail more time and effort than is required by each of the course’s problem sets.
    Any pip-installable libraries that your project requires must be listed, one per line, in a file called requirements.txt in the root of your project.

    Example Project Structures

    `project.py`

    ```python
    def main():
        ...


    def function_1():
        ...


    def function_2():
        ...


    def function_n():
        ...


    if __name__ == "__main__":
        main()
    ```

    `test_project.py`

    ```python
    def test_function_1():
        ...


    def test_function_2():
        ...


    def test_function_n():
        ...
    ```

    When to Do It

    **By Monday, January 1, 2024 at 4:59 AM GMT.**

    #### Getting Started
    Creating an entire project may seem daunting. Here are some questions that you should think about as you start:

    What will your software do? What features will it have? How will it be executed?
    What new skills will you need to acquire? What topics will you need to research?
    If working with one or two classmates, who will do what?
    In the world of software, most everything takes longer to implement than you expect. And so it’s not uncommon to accomplish less in a fixed amount of time than you hope. What might you consider to be a good outcome for your project? A better outcome? The best outcome?
    Consider making goal milestones to keep you on track.

    **How to Submit**

    You must complete all three steps!

    * Step 1 of 3

    Create a short video (that’s no more than 3 minutes in length) in which you present your project to the world, as with slides, screenshots, voiceover, and/or live action. Your video should somehow include your project’s title, your name, your city and country, and any other details that you’d like to convey to viewers. See howtogeek.com/205742/how-to-record-your-windows-mac-linux-android-or-ios-screen for tips on how to make a “screencast,” though you’re welcome to use an actual camera. Upload your video to YouTube (or, if blocked in your country, a similar site) and take note of its URL; it’s fine to flag it as “unlisted,” but don’t flag it as “private.”

    Submit this form!

    * Step 2 of 3
  
    Create a README.md text file (named exactly that!) in your ~/project folder that explains your project. This file should include your Project title, the URL of your video (created in step 1 above) and a description of your project. You may use the below as a template.

    ```md
    # YOUR PROJECT TITLE
    #### Video Demo:  <URL HERE>
    #### Description:
    TODO
    ```
    ??? note "Your [README.md]"

        Your README.md file should be minimally multiple paragraphs in length, and should explain what your project is, what each of the files you wrote for the project contains and does, and if you debated certain design choices, explaining why you made them. Ensure you allocate sufficient time and energy to writing a README.md that documents your project thoroughly. Be proud of it! If it is too short, the system will reject it.


    Execute the `submit50` command below from within your `~/project` directory (or from whichever directory contains `README.md` file and your project’s code, which must also be submitted). If your project does not meet all the requirements above, it may be rejected, so be sure you have satisfied all of the bullet points atop this specification and written a thorough `README`:

    `submit50 cs50/problems/2022/python/project`

    * Step 3 of 3

    That’s it! Your project should be graded within a few minutes. Be sure to visit your gradebook at `cs50.me/cs50p` a few minutes after you submit. It’s only by loading your Gradebook that the system can check to see whether you have completed the course, and that is also what triggers the (instant) generation of your free CS50 Certificate and the (within 30 days) generation of the Verified Certificate from edX, if you’ve completed all of the other assignments.



### The Academic Honesty policy
??? warning "The Academic Honesty policy "

    Note that CS50’s staff audits submissions to CS50P including this final project. Students found to be in violation of <a href="https://cs50.harvard.edu/python/2022/#honesty">the Academic Honesty policy</a> will be removed from the course and deemed ineligible for a certificate. Students who have already completed CS50P, if found to be in violation, will have their CS50 Certificate (and edX Certificate, if applicable) revoked.
---


Documentation By: **Raymond C. TURNER**

Last Updated: 1 Day ago