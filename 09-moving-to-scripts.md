---
layout: lesson
root: .
title: Moving to Scripts
---

## Objectives

- Move some of the notebook queries into a script that can be rerun as needed

Assume that in poking around in the data we've found a useful workflow that needs to be extracted every time. For instance, we want to load the data, remove NA values, join to the city names file so results are legible, and write out some tables and charts.

We can open a new text file and save it as 'housing_income.py'. Inside that file, paste the functions we've already used from the notebook. 

```
import pandas as pd
surveys_df = pd.read_csv("surveys.csv")

city_df = pd.read_csv('city.csv')

merged_inner = pd.merge(left=surveySub,right=citySub, left_on='city', right_on='city')

# distribution of tenure by city


```