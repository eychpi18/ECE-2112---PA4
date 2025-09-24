## INTRODUCTION TO PYTHON PROGRAMMING
# Experiment 4 - Data Wrangling and Data Visualization Demonstrations
URGEL, Hannah Pauleen A.      2ECE-B

# OVERVIEW
This experiment is a practical application of data wrangling and data visualization, with a specific focus on using Python to analyze a dataset. The project is designed to develop skills in using code to manipulate and present data in a meaningful way.

The core problems explored in this experiment are:

Filtering and creating new data frames from a given dataset based on specific criteria.

Developing a visualization to explore the relationship between different features and a student's average grade.

The work is structured to demonstrate how these methods can be used to analyze and interpret data, ultimately providing insights into how factors like track, gender, or hometown might relate to a student's performance.

# ECE BOARD EXAM PROBLEM:
Using data wrangling and data visualization technique with storytelling, analyze the data and present different (i) data frames; and (ii) visuals using the dataset given.

## 1. Create the following data frames based on the format provided: Example: Vis = [“Name”, “Gender”, “Track”, “Math<70”]; hometown is constant as Visayas

## CODE:

```python
import pandas as pd
```
STEP 1:
To get an initial look at the beginning of the dataset, I imported pandas as pd, which is the standard way of loading the pandas library in Python for easier use throughout the code. Pandas allows me to work with structured data, like Excel files, in an organized and efficient way.

```python
boards = pd.read_excel('board2.xlsx')
boards
```
STEP 2:
To get an initial look at the beginning of the dataset, I imported pandas as pd, which is the standard way of loading the pandas library in Python for easier use throughout the code. Pandas allows me to work with structured data, like Excel files, in an organized and efficient way.

After that, I used pd.read_excel("board2.xlsx") to read the dataset and store it in a DataFrame called boards. This DataFrame acts like a table where all the board exam data is stored and ready for analysis.

Finally, I simply typed boards to display the entire dataset, which let me check that the file was loaded correctly before performing any subsetting, slicing, or indexing. 

## OUTPUT:
<img width="677" height="928" alt="image" src="https://github.com/user-attachments/assets/85f870ed-5510-4a70-aaeb-95d987d02def" />

### a. Filename: Instru = [“Name”, “GEAS”, “Electronics >70”]; where track is constant as Instrumentation and hometown Luzon
## CODE:
STEP 1:
```python
Instru = boards.loc [ ]
```
First, I assigned the result of my filtering operation to a variable by writing Instru = .... This makes sure that the subset I create is stored under the name Instru, allowing me to reuse or display it later without retyping the whole expression.

Next, I used boards.loc[...] to perform the actual filtering and column selection. The .loc method in pandas takes two parts: on the left side, I specified the row conditions, and on the right side, I listed the columns I wanted to keep.

STEP 2:
```python
(boards['Track'] == 'Instrumentation') &
(boards['Hometown'] == 'Luzon') &
(boards['Electronics'] > 70),
['Name', 'GEAS', 'Electronics']
```
For the row selection, I combined three conditions inside parentheses:

(boards['Track'] == 'Instrumentation') keeps only the rows where the Track column is exactly "Instrumentation".

(boards['Hometown'] == 'Luzon') keeps rows where the Hometown column is "Luzon".

(boards['Electronics'] > 70) keeps rows where the Electronics score is greater than 70.

I connected these three conditions with the & operator, which means all of them must be true for a row to be included. The parentheses are important here because they ensure each condition is evaluated before being combined.

After filtering the rows, I specified the columns to display by writing ['Name', 'GEAS', 'Electronics']. This keeps my output focused on just the student name, GEAS score, and Electronics score, excluding other unnecessary columns.

STEP 3:
```python
Instru
```

Finally, when I typed Instru, pandas displayed the resulting table, which included only the students who are in the Instrumentation track, from Luzon, and have an Electronics score above 70. The result is a clean and concise subset that’s easy to read and analyze.

## OUTPUT:
<img width="411" height="163" alt="image" src="https://github.com/user-attachments/assets/a917f440-5d5a-412e-a97e-7dd26740b6c4" />

### b. Filename: Mindy = [ “Name”, “Track”, “Electronics”, “Average >=55”]; where hometown is constant as Mindanao and gender Female
## CODE:
STEP 1:
```python
boards['Average'] = boards [['Math','Electronics','GEAS', 'Communication']].mean(axis=1)
```
First, I created a new column named Average in the boards DataFrame.
This line calculates the row-wise mean of the four subjects (Math, Electronics, GEAS, Communication) for every student.
By setting axis=1, I ensured that the calculation is done horizontally across columns, not vertically down rows.
The result is stored as a new column called Average inside the same DataFrame.

STEP 2:
```python
Mindy = boards.loc [
(boards['Hometown'] == 'Mindanao') &
(boards['Gender'] == 'Female') &
(boards['Average'] >= 55),
['Name', 'Track', 'Electronics', 'Average']
]
```
Next, I used the .loc[] function to filter the rows based on three conditions:
(boards['Hometown'] == 'Mindanao') → selects only students whose hometown is Mindanao.

(boards['Gender'] == 'Female') → further narrows it down to female students.

(boards['Average'] >= 55) → ensures only those students with an average grade of 55 or higher are included.

The & operator is used to combine all three conditions so that only rows that satisfy all of them at once are selected.

Finally, I specified the columns I wanted to display: ['Name', 'Track', 'Electronics', 'Average'].
This means the resulting Mindy DataFrame only shows those four columns for the filtered students.

STEP 3:
```python
Mindy
```
This allowed me to see which female students from Mindanao have an average of at least 55, along with their name, track, electronics score, and overall average.

## OUTPUT:
<img width="640" height="238" alt="image" src="https://github.com/user-attachments/assets/90629b41-d914-4f3d-9b7e-03f44cb41bed" />



## 2. Create a visualization that shows how the different features contributes to average grade. Does chosen track in college, gender, or hometown contributes to a higher average score?
### TRACK IN COLLEGE:
## CODE:
STEP 1:
```python
import matplotlib.pyplot as plt
```
First, I imported the matplotlib.pyplot library and gave it an alias plt.
This library allows me to create visualizations such as bar charts, line charts, and scatter plots.

STEP 2:
```python
plt.figure(figsize=(10,5))
```
This step ensures that the visualization will not look too cramped and that each bar will be clearly visible.

STEP 3:
```python
plt.bar(boards['Track'], boards['Average'],  color="lightpink")
```
boards['Track'] is used for the x-axis of the chart, which shows the different tracks (Instrumentation, Communication, Microelectronics).

boards['Average'] is used for the y-axis, which shows the average scores of students in each track.

The color="lightpink" parameter adds a nice visual touch by coloring the bars light pink. And because my fav color is pink:))

## OUTPUT:
<img width="1279" height="575" alt="image" src="https://github.com/user-attachments/assets/6b92b2bc-2c29-4af4-82f2-2a5f21c1aca0" />

Based on the visualizations, students from the Microelectronics track have the highest average grades compared to those in Instrumentationt and Communication tracks.

### GENDER:
## CODE:
```python
plt.figure(figsize=(10,5))
plt.bar(boards['Gender'], boards['Average'], color=['lavender']
```
First, I used plt.figure(figsize=(10,5)) to define the size of my visualization.
This makes the figure 10 inches wide and 5 inches tall, giving enough space for the bars and labels to be displayed clearly without overlapping.

Next, I used the plt.bar() function to create a bar chart
boards['Gender'] → This sets the x-axis values based on the “Gender” column from the DataFrame.

boards['Average'] → This sets the height of each bar based on the “Average” grade column.

color=['lavender'] → This applies a lavender color to the bars.

## OUTPUT:
<img width="1281" height="569" alt="image" src="https://github.com/user-attachments/assets/a2124aa1-26f4-4313-9b59-281fab11e81c" />

 Female students show a slightly higher average grade than male students, although the difference is minimal.

### HOMETOWN:
## CODE:
```python
plt.figure(figsize=(10, 5))
plt.bar(boards['Hometown'], boards['Average'], color="paleturquoise")
```
First, I used plt.figure(figsize=(10,5)) to define the size of my visualization.
This makes the figure 10 inches wide and 5 inches tall, giving enough space for the bars and labels to be displayed clearly without overlapping.

Next, I used the plt.bar() function to create a bar chart
boards['Hometown'] → This sets the x-axis values based on the “Hometown” column from the DataFrame.

boards['Average'] → This sets the height of each bar based on the “Average” grade column.

color=['paleturquoise'] → This applies my wanted color to the bars.

## OUTPUT:
<img width="1280" height="597" alt="image" src="https://github.com/user-attachments/assets/a4c5963a-8d8c-41da-9d8f-d3a67995cf74" />

When grouped by hometown, students from Luzon have the highest average performance, followed by those from Visayas, with Mindanao students scoring slightly lower on average. 
