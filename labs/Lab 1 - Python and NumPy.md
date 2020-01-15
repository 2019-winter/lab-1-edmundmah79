---
jupyter:
  jupytext:
    formats: ipynb,md
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.1'
      jupytext_version: 1.2.4
  kernelspec:
    display_name: Python 3
    language: python
    name: python3
---

# Name(s)
Edmund Mah


**Instructions:** This is an individual assignment, but you may discuss your code with your neighbors.


# Python and NumPy

While other IDEs exist for Python development and for data science related activities, one of the most popular environments is Jupyter Notebooks.

This lab is not intended to teach you everything you will use in this course. Instead, it is designed to give you exposure to some critical components from NumPy that we will rely upon routinely.

## Exercise 0
Please read and reference the following as your progress through this course. 

* [What is the Jupyter Notebook?](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/What%20is%20the%20Jupyter%20Notebook.ipynb#)
* [Notebook Tutorial](https://www.datacamp.com/community/tutorials/tutorial-jupyter-notebook)
* [Notebook Basics](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/Notebook%20Basics.ipynb)

**In the space provided below, what are three things that still remain unclear or need further explanation?**


**YOUR ANSWER HERE**


## Exercises 1-7
For the following exercises please read the Python appendix in the Marsland textbook and answer problems A.1-A.7 in the space provided below.

```python
import numpy as np
```

## Exercise 1

```python
a = 2 * np.ones((6,4))
a
```

## Exercise 2

```python
b = 2* np.eye(6,4) + 1
b
```

## Exercise 3

```python
a * b
#np.dot(a,b)
```

a * b multiplies corresponding elements of each array with each other. So both elements in the position (1,1) would be multiplied together. np.dot(a,b) is matrix multiplication which cannot be done with two 6x4 matrices. It must be done between a 6x4 matrix and a 4x6 matrix. 


## Exercise 4

```python
print(np.dot(a.transpose(),b))
np.dot(a,b.transpose())
```

The shape is different because the transpose of a is a 4x6 matrix and the product of a 4x6 matrix multiplied to a 6x4 matrix is a 4x4 matrix. When b is transposed, it is also a 4x6 matrix but it is multiplied second so when you multiply a 6x4 matrix with a 4x6 matrix, you get a 6x6 matrix.


## Exercise 5

```python
def printSomeOutput():
    print("some output")
printSomeOutput()
```

## Exercise 6

```python
def printRandomArrays():
    for i in range(np.random.randint(1,10)):
        print("Array " + str(i))
        randomArray = np.ones((np.random.randint(1,10), np.random.randint(1,10)))
        for j in range(randomArray.shape[0]):
            for k in range(randomArray.shape[1]):
                randomArray[j][k] = np.random.randint(1,10)
        print("sum: " + str(np.sum(randomArray)))
        print("mean: " + str(np.mean(randomArray)))
        print("shape: " + str(randomArray.shape))
        print("median: " + str(np.median(randomArray)))
        print("min: " + str(np.min(randomArray)))
        print("max: " + str(np.max(randomArray)))
printRandomArrays()
```

## Exercise 7

```python
def numOnes(someArray):
    numOne = 0
    for i in range(someArray.shape[0]):
        for j in range(someArray.shape[1]):
            if someArray[i][j] == 1:
                numOne += 1
    return numOne

```

## Excercises 8-???
While the Marsland book avoids using another popular package called Pandas, we will use it at times throughout this course. Please read and study [10 minutes to Pandas](https://pandas.pydata.org/pandas-docs/stable/getting_started/10min.html) before proceeding to any of the exercises below.

```python
import pandas as pd
```

## Exercise 8
Repeat exercise A.1 from Marsland, but create a Pandas DataFrame instead of a NumPy array.

```python
#a is already defined from Exercise 1
df_a = pd.DataFrame(a)
df_a
```

## Exercise 9
Repeat exercise A.2 using a DataFrame instead.

```python
#b is already defined from Exercise 2
df_b = pd.DataFrame(b)
df_b
```

## Exercise 10
Repeat exercise A.3 using DataFrames instead.

```python
df_a * df_b
```

## Exercise 11
Repeat exercise A.7 using a dataframe.

```python
def numOnes(someArray):
    numOne = 0
    for i in range(someArray.shape[0]):
        for j in range(someArray.shape[1]):
            if someArray.iloc[i,j] == 1:
                numOne += 1
    return numOne
```

## Exercises 12-14
Now let's look at a real dataset, and talk about ``.loc``. For this exercise, we will use the popular Titanic dataset from Kaggle. Here is some sample code to read it into a dataframe.

```python
titanic_df = pd.read_csv(
    "https://raw.githubusercontent.com/dlsun/data-science-book/master/data/titanic.csv"
)
titanic_df
```

Notice how we have nice headers and mixed datatypes? That is one of the reasons we might use Pandas. Please refresh your memory by looking at the 10 minutes to Pandas again, but then answer the following.


## Exercise 12
How do you select the ``name`` column without using .iloc?

```python
titanic_df["name"]
```

## Exercise 13
After setting the index to ``sex``, how do you select all passengers that are ``female``? And how many female passengers are there?

```python
titanic_df.set_index('sex', inplace = True)
titanic_df.loc["female"]
```

## Exercise 14
How do you reset the index?

```python
titanic_df.reset_index(inplace = True)
```

```python

```
