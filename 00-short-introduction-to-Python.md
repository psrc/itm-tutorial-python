---
layout: lesson
root: .
title: Short Introduction to Programming in Python
---

# The Basics of Python

Python is a general purpose programming language, that supports rapid development
of scripts and applications.

Python's main advantages:

* Open Source software, supported by Python Software Foundation
* Available on all platforms
* "Batteries Included" philosophy - libraries for common tasks available in
  standard installation
* Supports multiple programming paradigms
* Very large community

## Where is this "Python"??
Open a console/terminal/shell window and type "python". This starts a live interactive session with Python.

In the interactive mode we can basically use Python as a calculator and do some "live" interfacing. You can tell you're in the Python environment by the three angle brackets near the prompt. 

```python
user:host:~$ python
Python 3.5.1 (default, Oct 23 2015, 18:05:06)
[GCC 4.8.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 2 + 2
4
>>> print("Hello World")
Hello World
```
The most basic data types in Python are strings, integers and floats:

```python
text = "Data Carpentry"
number = 42
pi_value = 3.1415
```

To print out the value stored in a variable we can simply type the name of the
variable into the interpreter:

```python
>>> text
"Data Carpentry"
```

The other way of using Python is by executing programs/scripts saved as a text file, with `*.py` extension. For instance, if we open our favorite text editor (could be notepad or vim or sublime) and write a simple line 'print "Hello World"', we can run that in the terminal. This is how a lot of scripts work. It's how we run our travel model at PSRC. Typing one command sparks off a whole chain of other scripts and tasks that takes a day or 2 to run.

```
python run_soundcast.py
```

```
user:host:~$ python my_script.py
Hello World
```

## iPython Notebooks
How do we get to the point of running and building long scripts though? How do we test and build code, or just explore data? Python is good for all of these things - today we'll focus on just a quick way of reading in data and manipulating it - creating summaries, slicing and dicing, and making charts. These are the same things that might be done in Excel, but when its part of a script it can not only be repeated but be included in a chain of other analyses. One click and you're down (mostly).

Today we're going to use a tool called the iPython notebook, which is basically the same thing as the interpreter we already saw. It's an interactive session, but it's more flexible and user-friendly than the basic Python prompt. It allows you save your history of commands, back back and re-run old commands, and create graphs and charts as you work. It's one of the best tools for data analysis specifically. It's also a great way to build and test code snippets before moving them into larger scripts later. This is generally how I work - test things out in the notebook then move them to more formal design later. 

Let's open up the iPython notebook. Open the shell and 'cd' to the place you saved the data. Type:

```
ipython notebook
```
What happened? As long sa you didn't get 'command not found' you should see a few lines of code appear on your console, and the last 2 saying:

```
The IPython notebook is running at: https: //localhost:8888/
Use Control-C to stop this server and shut down all kernels
```

This console is acting as a local server and its running an interactive web-based Python console. It should have automatically opened up a new browser window or tab for you. If not, open your browser and type: localhost:8888 in the url bar. 

The notebook shows the directory information of where you started it. You should see your data there. If not, see if you can navigate to it. Folders are clickable. Otherwise, just move your data to the notebook's working directory. You can see that in your console window in the 2nd line: 

```
Serving notebooks from local directory: C:\
```

We're just looking at a directory list now. Create a new python notebook by clicking "New" in the upper right corner. 

Note we can execute lines of code just like before.

We can also change the name of the file in the top line. Go ahead and change the name now. You can click on the "jupyter" logo to go back to the home page and return by clicking on the notebook name, which is already running. We can run lines of code, make changes in the line and rerun them. 

Okay, now let's start loading in data and doing stuff!
