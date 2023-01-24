# Part 1: Using Jupyter and more advanced Data Structures

**Time:** 30 minutes

**Experience:** Beginner

**Skills:** Data Science

In this workbook you will learn how to use Jupyter and start using a more advanced data structure called a DataFrame.


# How to use Jupyter

Jupyter is platform for you to write Python in a web browser and view the outputs in the same window.

It is incredibly useful for manipulating data and testing transformations on them.

## Cells and Output
Code in Jupyter is written in "cells", you can run the cell pressing `Shift + Enter` the output is then displayed below the cell.

We can write a basic addition and print the result.


```python
x = 1 + 2
print(x)
```

    3


Variables/values remain available between "cells", and you don't need to use print to show a single output.

In this case we can write `x` and it will print the previous value.


```python
x
```




    3



### Exercises
* Write more code and printing outputs
  * Different calculations using `x` or new variables?
  * Words and characters?
* Re-use variables across cells

## Basic Data Structures

You should already be familiar with the basic data structures in python `lists` and `dictionary`.

### Lists
* Contain a sequence of items
* Created using square braces `[]`
* Referenced using a number, known as the `index`
  * Indexes must be a whole number like 0, 5 or 42, it can't be a fraction like 0.5
  * A list `index` will start at 0 and go as far as the length of the list minus 1
* A lot of useful built-in functions (`len`, `sum`, `min`, etc...) can make processing the data easy



```python
# List of maths test scores
test_scores = [75, 67, 73, 87, 49, 57, 81, 90, 63, 45]

# Print a score
print("The first score in the list is", test_scores[0])

# Print some information about the scores
print(len(test_scores), "students took the test")
print("The best score was", max(test_scores))
print("The worst score was", min(test_scores))

# Print the average score by adding the scores and dividing by the number of students
print("The average score was", sum(test_scores) / len(test_scores))
```

    The first score in the list is 75
    10 students took the test
    The best score was 90
    The worst score was 45
    The average score was 68.7


### Exercises
* How would you get the last score?
  * *Hint:* there are two ways to do it
* Loop through the list and print each score.


This is useful, but it is just the scores, you don't know who had the best score and who needs more help.

You could use two lists, one with the scores and one with the students but this can make the code more complex.

You can combine the student and score in a dictionary.

### Dictionary
* Contains unstructured data
* Created using squiggly braces `{}`
* Referenced with a value, known as a `key` which will give you a `value`
* Keys can be almost any value
  * There are rules to what can be a `key` but as long as you use a `string` or `number` you will be fine


```python
student_scores = {
    "Richard": 75,
    "Amy": 67,
    "Nick": 73,
    "Tony": 87,
    "Lindsay": 49,
    "Jason": 57,
    "Sam": 81,
    "Josh": 90,
    "Zoe": 63,
    "Nicole": 45,
}

# len still works on dictionaries
print(len(student_scores), "students took the test")

# You need to call the values() directly to get the min, max and average
print("The best score was", max(student_scores.values()))
print("The worst score was", min(student_scores.values()))
print("The average score was", sum(student_scores.values()) / len(student_scores))

# You can loop over the student to find out who had the best score
# A loop will get the student names or `keys`
for student in student_scores:

    # You can use the student name to get their score
    if student_scores[student] == max(student_scores.values()):
        print(student, "had the BEST score")

    if student_scores[student] == min(student_scores.values()):
        print(student, "had the WORST score")
```

    10 students took the test
    The best score was 90
    The worst score was 45
    The average score was 68.7
    Josh had the BEST score
    Nicole had the WORST score


### Exercises
* Can you loop through the students, print the student name and score?

### More Fields/Data Modelling

The above is fine for one value but what if you wanted to track the test results over a period of time?

This is where you would need to start thinking about modelling your data.

You can do this by combining the basic data structures, for example a student could end up looking like...

```python
maths_students = [
    {"name": "Richard", "2022": 75, "2021": 72, "2020": 69},
    ...
]
```

As your datastructure becomes more complex the processing is more difficult - this is where DataFrames help.

## DataFrames

A DataFrame stores data in a table (also known as tabulated), similar to an Excel spreadsheet.

DataFrame comes from the `pandas` library, you can read data from other datastructures or from files.


```python
import pandas as pd  # This is the common way of importing pandas

# Create a DataFrame with 5 rows and 3 columns
data_frame = pd.DataFrame(
    [
        {"a": 10, "b": 20, "c": 30},  # row 0
        {"a": 100, "b": 200, "c": 300},  # row 1
        {"a": 1, "b": 2, "c": 3},  # row 2
        {"a": 15, "b": 25, "c": 35},  # row 3
        {"a": 11, "b": 12, "c": 13},  # row 4
    ]
)
# Jupyter understands the DataFrame and prints it as a table
# The first column is the `index`, this is followed by the data columns
data_frame
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>a</th>
      <th>b</th>
      <th>c</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>10</td>
      <td>20</td>
      <td>30</td>
    </tr>
    <tr>
      <th>1</th>
      <td>100</td>
      <td>200</td>
      <td>300</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>2</td>
      <td>3</td>
    </tr>
    <tr>
      <th>3</th>
      <td>15</td>
      <td>25</td>
      <td>35</td>
    </tr>
    <tr>
      <th>4</th>
      <td>11</td>
      <td>12</td>
      <td>13</td>
    </tr>
  </tbody>
</table>
</div>




```python
# You can select rows from a DataFrame using the `index` in `loc` (short for location)
data_frame.loc[0]
# Notice how the data has been "pivoted" with the columns becoming rows
```




    a    10
    b    20
    c    30
    Name: 0, dtype: int64




```python
# You can select columns by using square braces
data_frame['a']
```




    0     10
    1    100
    2      1
    3     15
    4     11
    Name: a, dtype: int64




```python
# You can select a specific entry using `loc` with the row and column
data_frame.loc[0, "a"]
```




    10



Another benefit is that you can perform operations on the entire DataFrame quickly and easily.


```python
# Add all values in each column
data_frame.sum()
```




    a    137
    b    259
    c    381
    dtype: int64




```python
# Easily calculate different averages of each column
data_frame.mean()
```




    a    27.4
    b    51.8
    c    76.2
    dtype: float64




```python
data_frame.median()
```




    a    11.0
    b    20.0
    c    30.0
    dtype: float64



### Students DataFrame

Returning to our earlier example, we can create a DataFrame for students and query it.



```python
students_list = [
    {"name": "Richard", 2022: 75, 2021: 72, 2020: 69},
    {"name": "Amy", 2022: 67, 2021: 71, 2020: 83},
    {"name": "Nick", 2022: 73, 2021: 68, 2020: 65},
    {"name": "Tony", 2022: 87, 2021: 91, 2020: 69},
    {"name": "Lindsay", 2022: 49, 2021: 56, 2020: 63},
    {"name": "Jason", 2022: 57, 2021: 55, 2020: 43},
    {"name": "Sam", 2022: 81, 2021: 72, 2020: 68},
    {"name": "Josh", 2022: 90, 2021: 85, 2020: 81},
    {"name": "Zoe", 2022: 63, 2021: 70, 2020: 75},
    {"name": "Nicole", 2022: 45, 2021: 53, 2020: 57},
]
students_data_frame = pd.DataFrame(students_list)
students_data_frame
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>2022</th>
      <th>2021</th>
      <th>2020</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Richard</td>
      <td>75</td>
      <td>72</td>
      <td>69</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Amy</td>
      <td>67</td>
      <td>71</td>
      <td>83</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Nick</td>
      <td>73</td>
      <td>68</td>
      <td>65</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Tony</td>
      <td>87</td>
      <td>91</td>
      <td>69</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Lindsay</td>
      <td>49</td>
      <td>56</td>
      <td>63</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Jason</td>
      <td>57</td>
      <td>55</td>
      <td>43</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Sam</td>
      <td>81</td>
      <td>72</td>
      <td>68</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Josh</td>
      <td>90</td>
      <td>85</td>
      <td>81</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Zoe</td>
      <td>63</td>
      <td>70</td>
      <td>75</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Nicole</td>
      <td>45</td>
      <td>53</td>
      <td>57</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Again we can get the average for 2022
students_data_frame[2022].mean()
```




    68.7




```python
# To get multiple columns you will need to group the columns together
students_data_frame[[2020, 2021, 2022]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>2020</th>
      <th>2021</th>
      <th>2022</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>69</td>
      <td>72</td>
      <td>75</td>
    </tr>
    <tr>
      <th>1</th>
      <td>83</td>
      <td>71</td>
      <td>67</td>
    </tr>
    <tr>
      <th>2</th>
      <td>65</td>
      <td>68</td>
      <td>73</td>
    </tr>
    <tr>
      <th>3</th>
      <td>69</td>
      <td>91</td>
      <td>87</td>
    </tr>
    <tr>
      <th>4</th>
      <td>63</td>
      <td>56</td>
      <td>49</td>
    </tr>
    <tr>
      <th>5</th>
      <td>43</td>
      <td>55</td>
      <td>57</td>
    </tr>
    <tr>
      <th>6</th>
      <td>68</td>
      <td>72</td>
      <td>81</td>
    </tr>
    <tr>
      <th>7</th>
      <td>81</td>
      <td>85</td>
      <td>90</td>
    </tr>
    <tr>
      <th>8</th>
      <td>75</td>
      <td>70</td>
      <td>63</td>
    </tr>
    <tr>
      <th>9</th>
      <td>57</td>
      <td>53</td>
      <td>45</td>
    </tr>
  </tbody>
</table>
</div>




```python
students_data_frame[[2020, 2021, 2022]].mean()
```




    2020    67.3
    2021    69.3
    2022    68.7
    dtype: float64




```python
# To search for specific rows you need to use the following format
students_data_frame[students_data_frame["name"] == "Tony"]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>2022</th>
      <th>2021</th>
      <th>2020</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>3</th>
      <td>Tony</td>
      <td>87</td>
      <td>91</td>
      <td>69</td>
    </tr>
  </tbody>
</table>
</div>




```python
# You can combine these commands together to get the mean score over multiple years
students_data_frame[students_data_frame["name"] == "Tony"][
    [2020, 2021, 2022]
].mean(axis=1)  # axis=1 tells pandas to calculate the mean across the row instead of down columns
```




    3    82.333333
    dtype: float64



### Exercises
* Try getting different students and manipulating data.
* How could you get the length of the DataFrame?
  * *Hint:* There maybe a method that can help or try `len`

## Summary

This workbook has taken you through some data structures and introduced pandas DataFrame.

Once you are comfortable move onto the next workbook [2. Stock Price Graph](2.%20Stock%20Price%20Graph.md) to learn how to get stock prices and show graphs.
