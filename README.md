<h1 align="center"> ECE2112 Programming Assignment 3 (Pandas) </h1>

<a id="top"></a>

## Table of Contents
1. [About the Project](#about)
2. [Getting Started](#getting_started)
   - [Instructions](#instructions)
4. [Sample Problems](#problems)
   - [Normalization Problem](#P1)
   - [Divisible by 3 Problem](#P2)
5. [Author](#author)

<a name="about"></a>
## About the Project
- Programming Assignment 3 is about identifying the codes and functions in the Pandas library and applying them in creating a Python program.

<a name="getting_started"></a>
## Getting Started
- To run the given code, follow these instructions:
  
<a name="instructions"></a>
 ### Instructions
 1. Install **Anaconda Navigator** at https://www.anaconda.com/download
 2. Open **Jupyter notebook**
 3. Download and open _Ching_Pandas-P1.ipynb_ and _Ching_Pandas-P2.ipynb_
 4. Run the programs 

<a name="problems"></a>
## Sample Problems:

<a name="P1"></a>
## **Problem 1**
* Using knowledge obtained from the experiment and demonstrations: </br>
> a. Load the corresponding .csv file into a data frame named cars using pandas

> b. Display the first five and last five rows of the resulting cars.


**Step 1.** Before coding, we must import the Pandas library.
``` python
import pandas as pd
```
<br/>

**Step 2.** I loaded the pre-installed file named 'cars.csv' and stored the data to `cars` 
``` python
# Load the csv file in the same folder
cars = pd.read_csv('cars.csv')
```
<br/>

**Step 3.1** Using `cars.index[]`, I specified the range of rows to be displayed in the variables `first` and `last`. Then, I concatenated the two sets of data using `pd.concat()`. 
``` python
# Locate the rows
first = cars.loc [ (cars.index[0:5]) ]
last = cars.loc [ (cars.index[27:32]) ]
# Concatenate first & last 
pd.concat([first,last])
```
<br/>

**Step 3.2** Alternatively, we can use `.head()` and `.tail()` in case the range of rows changes. I specified '5' in the functions, but it is not necessary.
```python
# Alternative: concatenate first & last rows using head and tail
pd.concat ( [cars.head(5), cars.tail(5)] )
```
<br/>

**Possible Output**: 
``` 

```
/assets/images/P1_Table.png 

<br/>


<a name="P2"></a>
## **Problem 2**
* Create a 10 x 10 ndarray, which is the squares of the first 100 positive integers. From this ndarray, determine all the elements that are divisible by 3. Save the result as div_by_3.npy.


**Step 1.** Again, we must import the numpy library first.
``` python
import numpy as np
```
<br/>

**Step 2.** I created a 10x10 array filled with 1's as a placeholder for the values. I also specified the array's data type `dtype=np.int16` since it sometimes returns float values.
``` python
# Create a 10x10 filled with 1's
X = np.ones([10,10],dtype=np.int16) # Specified dtype due to float output
```
<br/>

**Step 3.** To assign values one by one, I used two for loops. The first loop starts at the first row and waits for the second loop to go through each column. The `col` loop assigns the squared value of n, which increments by 1 each iteration.
``` python
n = 1
for row in range(10):     # Loop through rows 
    for col in range(10): # Loop through cols
        X[row,col] = n**2 # Square the value per column
        n += 1            # Increase n value by 1
```
<br/>

**Step 4.** I created a new array `div` to store only the values divisible by 3. By using modulo (%) on the original array, it takes each value and divides it by 3. If the remainder is 0, then the value is stored in `div`. Lastly, we save the new array data in "div_by_3.npy" by using `.save()`.
``` python
div = X [X%3 == 0]           # Store values divisible by 3
np.save("div_by_3.npy", div) # Save values
```
<br/>

**Step 5.** I printed out the values to verify the results.
``` python
print("10x10 Matrix:\n", X, "\n")                   # Show matrix data
print("Divisible by 3:\n",div, "\n")                # Show values divisible by 3
print("Saved Values:\n", np.load("div_by_3.npy"))   # Check if file saved div data
```
<br/>

**Expected Output**: 
``` 
10x10 Matrix:
 [[    1     4     9    16    25    36    49    64    81   100]
 [  121   144   169   196   225   256   289   324   361   400]
 [  441   484   529   576   625   676   729   784   841   900]
 [  961  1024  1089  1156  1225  1296  1369  1444  1521  1600]
 [ 1681  1764  1849  1936  2025  2116  2209  2304  2401  2500]
 [ 2601  2704  2809  2916  3025  3136  3249  3364  3481  3600]
 [ 3721  3844  3969  4096  4225  4356  4489  4624  4761  4900]
 [ 5041  5184  5329  5476  5625  5776  5929  6084  6241  6400]
 [ 6561  6724  6889  7056  7225  7396  7569  7744  7921  8100]
 [ 8281  8464  8649  8836  9025  9216  9409  9604  9801 10000]] 

Divisible by 3:
 [   9   36   81  144  225  324  441  576  729  900 1089 1296 1521 1764
 2025 2304 2601 2916 3249 3600 3969 4356 4761 5184 5625 6084 6561 7056
 7569 8100 8649 9216 9801] 

Saved Values:
 [   9   36   81  144  225  324  441  576  729  900 1089 1296 1521 1764
 2025 2304 2601 2916 3249 3600 3969 4356 4761 5184 5625 6084 6561 7056
 7569 8100 8649 9216 9801]
```
<br/>

<a name="author"></a>
## **Author** 
- Name: Elton Ching
- Section: 2ECE-B

<p align="right"> (<a href="#top">Back to Top</a>) </p>
