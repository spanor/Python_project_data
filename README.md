# Overview

Welcome to my project of analyzing data in the job market of data, network, software engineering. I got inspired about this project for as I started looking for job market in different states of the world.

The data is sourced from huggingface technology, specifically from Luke Barousse, who was one of my mentors through data world exploring with Python.

In this project I started by answering couple of questions about the skills in demand for the job roles I was looking in the job market, focusing in Scandinavia, EMEA and after in the United States. 

## The Questions

Questions I want to answer in my project are:

What are the skills most in demand for the 3 Scandinavian states and most popular data roles?
How are in-demand skills trending for Data Analysts?
How well do jobs and skills pay for Data Analysts?
What are the optimal skills for data analysts to learn? 

## Tools I Used


**Python**: The foundation of my analysis, enabling me to examine the data and uncover key insights.

I also used the following Python libraries:

**Pandas Library**: This was used to analyze the data.
**Matplotlib Library**: Used to visualize data.
**Seaborn Library**: Helped me create more advanced visuals.

**Jupyter Notebooks**: The platform I used to execute Python scripts, seamlessly integrating notes and analysis.

**Visual Studio Code**: My go-to for executing my Python scripts.

**Git & GitHub**: Crucial for version control and code sharing, enabling collaboration and efficient project tracking.

# Data Preparation and Cleanup

This section details the data preparation process, ensuring accuracy and usability for analysis.

## Import & Clean Up Data

I begin by importing the required libraries and loading the dataset, then perform initial cleaning to maintain data quality.

```# Importing Libraries
import ast
import pandas as pd
import seaborn as sns
from datasets import load_dataset
import matplotlib.pyplot as plt  

# Loading Data
dataset = load_dataset('C:\Users\Nora\Documents\Python_project_data\data_jobs.csv')
df = dataset['train'].to_pandas()

# Data Cleanup
df['job_posted_date'] = pd.to_datetime(df['job_posted_date'])
df['job_skills'] = df['job_skills'].apply(lambda x: ast.literal_eval(x) if pd.notna(x) else x)
```

## Filter Scandinavian Jobs
To tailor my analysis to the Scandinavian job market, I filter the dataset to include only roles located within Scandinavian countries.

```

df_Scand = df[df['job_country'].isin(['Norway', 'Sweden', 'Finland'])].copy().dropna(subset ='salary_year_avg')

```

## The Analysis

### First I answered the question: 

What are the top paid job roles in Scandinavia? 

I filtered out job roles which were most popular in Scandinavia (Sweden, Norway, Finland) and then categorized them by the highest salaries in that market. 

My notebook with detailed steps here: [Project Start](https://www.example.com)

Methodology

- Clean-up skill column
- Calculate skill count based on job_title_short
- Calculate skill percentage
- Plot final findings

View my notebook with detailed steps here: [2.Skill Demand.ipynb](3.Projects\2.Skill Demand.ipynb)

### Visualize Data

```
fig, ax = plt.subplots(len(job_titles), 1)
sns.set_theme(style = 'ticks')

for i, job_title in enumerate(job_titles):
    df_plot = df_skill_percent[df_skill_percent['job_title_short'] == job_title].head(5)
    #df_plot.plot(kind = 'barh', x = 'job_skills', y = 'skill_percent', ax = ax[i], title = job_title)
    sns.barplot(df_plot, x = 'skill_percent', y = 'job_skills', ax = ax[i],  hue = 'skill_count', palette = 'dark:b_r' )
```
    

![Visualization of 5 top in demand skills for 3 top roles](3.Projects\Images\skill_in_demand_for_three_top_roles.png)

### Insights

High Demand for Python and SQL Across All Roles

SQL appears in all three charts, consistently ranking as one of the most in-demand skills.
Python is also highly sought after, frequently appearing near the top with significant percentages (37%, 57%, 61%).
This suggests that SQL and Python are fundamental for top data-related roles.


