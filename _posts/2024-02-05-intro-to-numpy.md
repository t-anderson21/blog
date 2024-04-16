---
layout: post
title:  "Introduction to NumPy"
date: 2024-02-05
description: A first posting of thoughts on the basics of NumPy   
image: "/assets/img/image5.jpg"
display_image: false  # change this to true to display the image below the banner 
---
<p class="intro"><span class="dropcap">T</span>his post will discuss as a basic introduction to using Numpy, with my experiences as a beginner.  I've tried to include other resources and common places to get stuck.</p>

## Quick Intro to NumPy (for beginners!)
NumPy is a powerful library that forms the foundation of much of the scientific computing ecosystem in Python. Its array-based computing model, along with its extensive collection of mathematical functions, makes it an indispensable tool for data manipulation, numerical analysis, and scientific computing tasks. This introduction provides a brief overview of NumPy's features and its importance in Python programming.

#### Getting Started with NumPy:
To use NumPy in your Python environment, you first need to install it. You can install NumPy using pip, the Python package manager, with the following command:
```
pip install numpy
```
Once installed, you can import NumPy into your Python scripts or interactive sessions using the following convention:
```
import numpy as np
```

#### Best Uses
NumPy is an large library in Python for scientific computing, offering a comprehensive suite of tools for performing a wide range of mathematical operations. With NumPy, you can execute various mathematical computations and it facilitates operations like vector-vector, matrix-matrix, or matrix-vector multiplication. Beyond basic arithmetic, NumPy empowers you to perform other operations such as addition, subtraction, multiplication, and division by scalar values across vectors and matrices. Its intuitive interface and powerful functionality make it "a cornerstone of scientific computing, providing researchers, engineers, and data scientists with the tools they need to tackle complex mathematical challenges and explore numerical data effectively." It is the foundational building blocks used to then build much more sophisticated numerical operations efficiently. 

My first experiences with NumPy came in Math 215 at BYU. I had no previous coding experience with Python so there was a little bit of a learning curve that I hope this tutorial will speed up. I found that using ChatGPT at the same time is a great way to speed up troubleshooting which will inevitably happen. I quickly found that NumPy is a great way to contain lots of information and to move around. Several of the projects resulted in cool images and advanced estimates of different physics and engineering problems.

My favorite resource I found when I kept getting stuck was this website: <a href="https://numpy.org/doc/stable/user/absolute_beginners.html" target="_blank">NumPy Library</a>


#### Basic Commands to Master

| Command      | Description |
| ------------ | ---------------------------------------------------------|
| print()      | Outputs the specified message or variable to the console |
| type()       | Returns the data type of a variable or value             |
| np.array()   | Create an array, can control dimensions and inputs       |
| arr.max()    | Find maximum value in variable                           |
| arr.min()    | Find minimum value in array                              |
| np.range()   | Generates a sequence of numbers within a specified range |
| np.random.rand()| Random number generation                              |
| import from  | Import modules or specific functions from modules        |
| arr.reshape()| Reshape an array                                         |
| np.sort(arr) | Sort the array                                                 | 

These basic commands are fundamental tools in Python programming and data analysis using NumPy. The print() function is essential for displaying information to the console, aiding in debugging and program flow comprehension. The type() function helps identify the data type of variables or values, crucial for ensuring proper operations and compatibility. np.array() from the NumPy library facilitates the creation of arrays, a cornerstone for numerical computing. Operations like finding the maximum and minimum values with arr.max() and arr.min(), respectively, are fundamental for data analysis and algorithmic implementations. np.arange() and np.random.rand() enable the generation of sequences and random numbers, crucial for simulations and modeling. Importing modules or specific functions with import from grants access to extensive libraries and functionalities. Array manipulation operations such as reshaping with arr.reshape() and sorting with np.sort() enhance data processing and analysis capabilities. In summary, mastering these commands equips programmers and data analysts with the foundational tools needed to manipulate, analyze, and understand data efficiently and effectively in Python.

#### Code Examples
Here are a few simple commands to try and implement the above commands using the NumPy library!

Simple math is a great starting place to get a solid understanding of how commands fit together:
```
# Element-wise addition
addition = a + b
print("Element-wise addition:")
print(addition)
print()
```
Create your own test array to follow along below
```
arr = np.array([1, 2, 3, 4, 5])
arr_2d = np.array([[1, 2, 3], [4, 5, 6]])
```

We can easily learn more about the information in an array:
```
np.sum(arr)
np.mean(arr)
np.max(arr)
```
Moving the data around using 'indexing' and cutting selected portions out using 'slicing' is possible:
```
arr[0]
arr[1:4]

# Reshape array
reshaped_arr = arr.reshape((5, 1))
print("Reshaped array:", reshaped_arr)

```

An important way to store and move data is in an array. It is the fundamental data structure used for numerical computations and data manipulation in Python. From an array, we can move, replicate, splice, and vectorize the data into deserved outcomes. Arrays are also able to hold a variety of elements and values, making them are more memory efficient.

```
import numpy as np

# Creating a simple array
array1 = np.array([1, 2, 3, 4, 5])
print(array1)
```


## List of common uses
* Data Manipulation
* Mathematical Operations
  * Linear Algebra
  * Random Number Generation
* Statistical Analysis
* Image Processing
* Machine Learning
* Signal Processing
* Simulation and Modeling
* Support for Data Visualization


#### Accessing Data

```
{% raw %}<img src="{{site.url}}/{{site.baseurl}}/assets/img/image_name.jpg" alt="" style="width:300px;"/>{% endraw %}
```

#### Conclusion
As a beginner exploring NumPy, I've still learning a new toolset for computing in Python. Through hands-on exploration, I've learned how NumPy simplifies data manipulation, mathematical operations, and statistical analysis with its intuitive array-based structure. Its extensive library of functions and capabilities for linear algebra, random number generation, and signal processing have opened up new avenues for scientific exploration and problem-solving. The main takeaways I want the reader to have are: 1.) using Python is a process of constant learning and 2.) NumPy is a great starting point for any new coder. It's an important basic library to learn that will provide a foundation for future, more complex libaries.

In summary, NumPy has empowered me as a beginner to navigate the realm of scientific computing with confidence and proficiency, laying a solid foundation for my future endeavors in data science, machine learning, and beyond.

My challenge to you, the reader: Go practice moving around a dataset and learn one new command for data manupilation. Be an active learner!
