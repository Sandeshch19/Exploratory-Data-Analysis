# Exploratory Data Analysis (EDA) for "cetrisured"

## Project Overview

The project involved conducting an EDA for "cetrisured," who organized a 9-day workshop in a college. During the workshop, students took 5 quizzes, and feedback forms were collected on instructor knowledge, overall ratings, and individual help provided. The primary objectives were to identify the top 6 students for an internship and to analyze feedback ratings.

## Data Preparation

### Merging Feedback Data

```python
# Merging data from "FDF1.xlsx" and "FDF2.xlsx"
file_1 = pd.read_excel('D:\FDF1.xlsx')
file_2 = pd read_excel('D:\FDF2.xlsx')
concatenated_data = pd.concat([file_1, file_2], ignore_index=True)

# Remove duplicate entries, drop unnecessary columns, and rename columns
concatenated_data.drop_duplicates(subset="Email address", inplace=True)
concatenated_data = concatenated_data.rename(columns={...})

# Replace missing values with 0
concatenated_data["Avg_Ratings"] = concatenated_data["Avg_Ratings"].fillna(0) 
```
### Attendance Data Analysis

```python
import pandas as pd

# Read attendance data from "Score_Table (1).xlsx"
work_sheet = pd.read_excel("D:\Score_Table (1).xlsx")

# Drop rows with missing values
work_sheet.dropna(inplace=True)

# Group data by email addresses to count the number of timestamps for each student
Attendence_count = work_sheet.groupby('Email Adress')['Time stamps'].count().reset_index()
Attendence_count.columns = ['Email Adress', 'AttendanceCount']

# Create a DataFrame to store students who attended all 5 quizzes
student_with_4_att = Attendence_count[Attendence_count['AttendanceCount'] == 5]

# Perform an inner join to combine attendance data with students who attended all 5 quizzes
result = pd.merge(work_sheet, student_with_4_att, on='Email Adress', how='inner')

# Save the result to a new Excel file, "result.xlsx"
result.to_excel('D:/result.xlsx', index=False)
```
### Selecting the Top 6 Students for Internship

```python
# Read the "result.xlsx" file into a DataFrame
result_1 = pd.read_excel('D:/result.xlsx')

# Group data by email addresses and calculate the total score for each student
total_score = result_1.groupby('Email Adress')['Score'].sum().reset_index()

# Sort the students by total score in descending order
total_score = total_score.sort_values by 'Score', ascending=False)

# Select the top 6 students with the highest total scores for the internship
top_6_students = total_score.head(6)
```
### Conclusion
The EDA process successfully prepared the data for further analysis, making it structured and ready for insights and visualization. The top 6 students were selected for the internship based on quiz scores and attendance. Additional analysis can be performed on feedback ratings to provide further insights and recommendations.

Please note that the actual data and results are not provided to maintain data privacy and confidentiality.

Repository Structure
data: Contains the Excel data files used in the project.
code: Includes Jupyter Notebook or Python script files with the code snippets.
documentation: Contains the full EDA report in a separate Markdown file.
results: Holds the resulting data files like "result.xlsx."
How to Replicate the Analysis
To replicate this analysis, you can follow the code and instructions in the provided Jupyter Notebook or Python script files in the "code" folder. Additionally, refer to the full EDA report in the "documentation" folder for a comprehensive understanding of the project.

Contributors
Sandesh N Christy and AmithRaj k
Feel free to explore the code, data, and full report to gain insights into the analysis and findings of this project.

Note: The actual data and results are not provided in the repository to maintain data privacy and confidentiality.
