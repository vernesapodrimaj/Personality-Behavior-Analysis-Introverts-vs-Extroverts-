# 📊 Personality Behavior Analysis: Introverts vs Extroverts (+ Ambiverts)

## 📁 Dataset
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


## 🎯 Project Overview

This project explores how **introverts** and **extroverts** differ in behavior across various real-world and online settings. It also defines and identifies a third group—**ambiverts**—based on behavioral balance.

The project includes:

- Data cleaning and analysis in **Python**
- Behavioral trait comparison across personality types
- Rule-based classification of **ambiverts**
- An **interactive dashboard** using **Looker Studio**
- A clean **GitHub repository** with code and visuals


## ✅ Objectives

- Clean and explore a real-world personality dataset  
- Compare introverts vs extroverts across behavioral metrics  
- Define **ambiverts** using a custom rule  
- Visualize insights using Python and Looker Studio  
- Share findings in a portfolio-ready format

---

## 🧰 Tools Used

- `pandas` – data manipulation  
- `seaborn` & `matplotlib` – visualization  
- `Tableau` – dashboard for stakeholder presentation  
- `Jupyter Notebook` – analysis & documentation  
- `GitHub` – version control and sharing

---

## 📊 Key Insights

- **Introverts** spend more time alone and attend fewer events  
- **Extroverts** post more frequently and have larger social circles  
- **Ambiverts** balance both sides, showing middle-range behavior across traits  
- Stage fear and post-social fatigue are more common among introverts

---
# 1. Import Libraries
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# 2. Load Dataset
df = pd.read_csv("personality_datasert.csv")  # Change path if needed

# 3. Inspect Dataset
df.head()
df.tail()
df.info()
df.describe()
df.isnull().sum()

# 4. Check Unique Values
df['Personality'].unique()
df['Stage_fear'].unique()
df['Drained_after_socializing'].unique()
df['Personality'].value_counts()
df['Stage_fear'].value_counts()

# 5. Clean Column Values (Whitespace + Capitalization)
df['Personality'] = df['Personality'].astype(str).str.strip().str.title()
df['Stage_fear'] = df['Stage_fear'].astype(str).str.strip().str.title()
df['Drained_after_socializing'] = df['Drained_after_socializing'].astype(str).str.strip().str.title()


