---
layout: lesson
root: .
title: Data Types and Formats
---

# Querying and Working with Missing Data


## Querying Data

Often we want a subset of our data using criteria. For example, we need to look at results for a specific range of years or for a given set of cities.

To select data from year 2002
```python
surveys_df[surveys_df['year'] == 2002]
```

Which produces the following output:

```python
record_id  month  day  year  district city  tenure  hindfoot_length  income
33320      33321      1   12  2002        1         DM    M     38      44 
33321      33322      1   12  2002        1         DO    M     37      58
33322      33323      1   12  2002        1         PB    M     28      45
33323      33324      1   12  2002        1         AB  NaN    NaN     NaN
33324      33325      1   12  2002        1         DO    M     35      29
...
35544      35545     12   31  2002       15         AH  NaN    NaN     NaN
35545      35546     12   31  2002       15         AH  NaN    NaN     NaN
35546      35547     12   31  2002       10         RM    F     15      14
35547      35548     12   31  2002        7         DO    M     36      51
35548      35549     12   31  2002        5        NaN  NaN    NaN     NaN

[2229 rows x 9 columns]
```

Or we can select all rows that do not contain the year 2002.

```python
surveys_df[surveys_df.year != 2002]
```

We can define sets of criteria too:

```python
surveys_df[(surveys_df['year'] >= 1980) & (surveys_df['year'] <= 1985)]
```

# Python Syntax Cheat Sheet

Use can use the syntax below when querying data from a DataFrame. Experiment
with selecting various subsets of the "surveys" data.

* Equals: `==`
* Not equals: `!=`
* Greater than, less than: `>` or `<`
* Greater than or equal to `>=`
* Less than or equal to `<=`


## Challenge Activities

1. Select a subset of rows in the `surveys_df` DataFrame that contain data from
   the year 1999 and that contain income values less than or equal to 20000 How
   many columns did you end up with? What did your neighbor get?
2. You can use the `isin` command in python to query a DataFrame based upon a
   list of values as follows:
   `surveys_df[surveys_df['city'].isin([listGoesHere])]`. Use the `isin` function
   to find all records that contain particular city in
   the surveys DataFrame. How many records contain these values?
3. Experiment with other queries. Create a query that finds all rows with a income value > or equal to 0.
4. The `~` symbol in Python can be used to return the OPPOSITE of the selection that you specify in python. 
It is equivalent to **is not in**. Write a query that selects all rows that are NOT equal to 'R' or 'O' in the surveys
data.

Answer: 

```
surveys_df[~surveys_df['tenure'].isin(['R','O'])]
```

## Missing Data Values - NaNs


Dealing with missing data values is always a challenge. It's sometimes hard to
know why values are missing - was it because of a data entry error? Or data that
someone was unable to collect? Should the value be 0? We need to know how
missing values are represented in the dataset in order to make good decisions.
If we're lucky, we have some metadata that will tell us more about how null
values were handled.

For instance, like in household surveys, missing data values are
often defined as -9999. Having a bunch of -9999 values in your data could really
alter numeric calculations. Often in spreadsheets, cells are left empty where no
data are available. Pandas will, by default, replace those missing values with
NaN. However it is good practice to get in the habit of intentionally marking
cells that have no data, with a no data value! That way there are no questions
in the future when you (or someone else) explores your data.

### Where Are the NaN's?


Dealing with missing data values is always a challenge. It's sometimes hard to
know why values are missing - was it because of a data entry error? Or data that
someone was unable to collect? Should the value be 0? We need to know how
missing values are represented in the dataset in order to make good decisions.
If we're lucky, we have some metadata that will tell us more about how null
values were handled.

For instance, like in household surveys, missing data values are
often defined as -9999. Having a bunch of -9999 values in your data could really
alter numeric calculations. Often in spreadsheets, cells are left empty where no
data are available. Pandas will, by default, replace those missing values with
NaN. However it is good practice to get in the habit of intentionally marking
cells that have no data, with a no data value! That way there are no questions
in the future when you (or someone else) explores your data.

### Where Are the NaN's?

>>>>>>> 644fa14f2c9efaa9e81600306bbcd670b53c52ab
Let's explore the NaN values in our data a bit further. Using the tools we
learned in lesson 02, we can figure out how many rows contain NaN values for
income. We can also create a new subset from our data that only contains rows
with income values > 0 (ie select meaningful income values):

```python
len(surveys_df[pd.isnull(surveys_df.income)])
# how many rows have income values?
len(surveys_df[surveys_df.income> 0])
```

We can replace all NaN values with zeroes using the `.fillna()` method (after
making a copy of the data so we don't lose our work):

```python
df1 = surveys_df.copy()
# fill all NaN values with 0
df1['income'] = df1['income'].fillna(0)
```

However NaN and 0 yield different analysis results. The mean value when NaN
values are replaced with 0 is different from when NaN values are simply thrown
out or ignored.

```python
df1['income'].mean()
38.751976145601844
```

We can fill NaN values with any value that we chose. The code below fills all
NaN values with a mean for all income values.

```python
 df1['income'] = surveys_df['income'].fillna(surveys_df['income'].mean())
```

We could also chose to create a subset of our data, only keeping rows that do
not contain NaN values.

The point is to make conscious decisions about how to manage missing data. This
is where we think about how our data will be used and how these values will
impact the scientific conclusions made from the data.

Python gives us all of the tools that we need to account for these issues. We
just need to be cautious about how the decisions that we make impact scientific
results.

## Recap

