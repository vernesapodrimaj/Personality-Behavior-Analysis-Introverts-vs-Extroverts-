# Personality Behavior Analysis: Introverts vs Extroverts (+ Ambiverts)

## Dataset
**Source:** [Kaggle - Extrovert vs Introvert Behavior Data](https://www.kaggle.com/datasets/rakeshkapilavai/extrovert-vs-introvert-behavior-data)  
**Description:**  
A behavioral survey dataset of ~2,900 participants with traits such as:

- Time spent alone  
- Social event attendance  
- Friends circle size  
- Stage fear  
- Feeling drained after socializing  
- Post frequency online  
- Personality type: `Introvert` or `Extrovert`


##  Project Overview

This project explores how **introverts** and **extroverts** differ in behavior across various real-world and online settings. It also defines and identifies a third group—**ambiverts**—based on behavioral balance.

The project includes:

- Data cleaning and analysis in **Python**
- Behavioral trait comparison across personality types
- Rule-based classification of **ambiverts**
- An **interactive dashboard** using **Looker Studio**
- A clean **GitHub repository** with code and visuals


## Objectives

- Clean and explore a real-world personality dataset  
- Compare introverts vs extroverts across behavioral metrics  
- Define **ambiverts** using a custom rule  
- Visualize insights using Python and Looker Studio  
- Share findings in a portfolio-ready format

---

## Tools Used

- `pandas` – data manipulation  
- `seaborn` & `matplotlib` – visualization  
- `Tableau` – dashboard for stakeholder presentation  
- `Jupyter Notebook` – analysis & documentation  
- `GitHub` – version control and sharing

---

## Key Insights

- **Introverts** spend more time alone and attend fewer events  
- **Extroverts** post more frequently and have larger social circles  
- **Ambiverts** balance both sides, showing middle-range behavior across traits  
- Stage fear and post-social fatigue are more common among introverts

---
## Import Libraries and data cleaning
```Python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

Load Dataset
df = pd.read_csv("")

Inspect Datasetv
df.head()
df.tail()
df.info()
df.describe()
df.isnull().sum()

Check Unique Values
df['Personality'].unique()
df['Stage_fear'].unique()
df['Drained_after_socializing'].unique()
df['Personality'].value_counts()
df['Stage_fear'].value_counts()

Clean Column Values (Whitespace + Capitalization)
df['Personality'] = df['Personality'].astype(str).str.strip().str.title()
df['Stage_fear'] = df['Stage_fear'].astype(str).str.strip().str.title()
df['Drained_after_socializing'] = df['Drained_after_socializing'].astype(str).str.strip().str.title()

Convert Numeric Columns to Integers
df['Social_event_attendance'] = df['Social_event_attendance'].astype(int)
df['Going_outside'] = df['Going_outside'].astype(int)
df['Friends_circle_size'] = df['Friends_circle_size'].round().astype(int)
df['Post_frequency'] = df['Post_frequency'].round().astype(int)

### Data Visualization
sns.histplot(data=df, x='Time_spent_Alone', bins=12, kde=True)
plt.title('Distribution of Time Spent Alone')
plt.show()

### Compare Averages per Personality
df.groupby('Personality')[[
    'Time_spent_Alone',
    'Friends_circle_size',
    'Social_event_attendance',
    'Post_frequency',
    'Going_outside'
]].mean().round(2)


### Countplot
sns.countplot(data=df, x='Stage_fear', hue='Personality')
plt.title('Stage Fear by Personality')
plt.show()

sns.countplot(data=df, x='Drained_after_socializing', hue='Personality')
plt.title('Feeling Drained After Socializing by Personality')
plt.show()

### Define Ambivert Group
df['Ambivert'] = (
    (df['Time_spent_Alone'].between(4, 7)) &
    (df['Social_event_attendance'].between(4, 7)) &
    (df['Post_frequency'].between(4, 7))
)

df['Ambivert'] = df['Ambivert'].map({True: 'Ambivert', False: 'Not Ambivert'})

### View Ambiverts
df[df['Ambivert'] == 'Ambivert'][[
    'Personality',
    'Time_spent_Alone',
    'Social_event_attendance',
    'Post_frequency',
    'Ambivert'
]].head()

### Export Cleaned Dataset
df.to_csv("personality_cleaned.csv", index=False)


## Tableau Dashboard
https://public.tableau.com/views/PersonalityBehaviorAnalysisIntrovertsvsExtroverts/Dashboard1?:language=en-GB&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link



