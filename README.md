# The Analysis

## What are the most demanding skills for 3 top job roles in US?

Methodology

- Clean-up skill column
- Calculate skill count based on job_title_short
- Calculate skill percentage
- Plot final findings

View my notebook with detailed steps here: [2.Skill Demand.ipynb](3.Projects\2.Skill Demand.ipynb)

### Visualize Data

fig, ax = plt.subplots(len(job_titles), 1)
sns.set_theme(style = 'ticks')

for i, job_title in enumerate(job_titles):
    df_plot = df_skill_percent[df_skill_percent['job_title_short'] == job_title].head(5)
    #df_plot.plot(kind = 'barh', x = 'job_skills', y = 'skill_percent', ax = ax[i], title = job_title)
    sns.barplot(df_plot, x = 'skill_percent', y = 'job_skills', ax = ax[i],  hue = 'skill_count', palette = 'dark:b_r' )
    #ax[i].invert_yaxis()
    ax[i].legend().set_visible(False)
    ax[i].set_ylabel('')
    ax[i].set_xlabel('')
    ax[i].set_xlim(0, 65)
    

![Visualization of 5 top in demand skills for 3 top roles](3.Projects\Images\skill_in_demand_for_three_top_roles.png)

### Insights

High Demand for Python and SQL Across All Roles

SQL appears in all three charts, consistently ranking as one of the most in-demand skills.
Python is also highly sought after, frequently appearing near the top with significant percentages (37%, 57%, 61%).
This suggests that SQL and Python are fundamental for top data-related roles.

