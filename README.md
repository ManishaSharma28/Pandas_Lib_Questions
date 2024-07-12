# Pandas_Lib_Questions
# 1. What is Pandas, and how do you install it?
Answer:

# Pandas is an open-source data analysis and manipulation library for Python. 
# It provides data structures and functions needed to work with structured data seamlessly.

# pip install pandas

# 2. How do you create a DataFrame in Pandas?
Answer:

# We can create a DataFrame from various data structures like dictionaries, lists, or CSV files.

# From a dictionary:
import pandas as pd

data = {
    'Name': ['shiv', 'ram', 'gauri', 'sita'],
    'Age': [28, 24, 35, 33],
    'Gender':['Male','Male','Female','Female']
}

df = pd.DataFrame(data)
print(df)


# df = pd.read_csv("")
# print(df)

# 3. How do you manipulate and access data in a DataFrame?
Answer:

# Use indexing and slicing to access specific rows and columns.

# Using column names:
print(df['Name'])

# Using .loc[] for label-based indexing:
print(df.loc[0, 'Name'])

# Using .iloc[] for integer-based indexing:
print(df.iloc[3, 1])

# 4. How do you handle missing data in Pandas?
Answer:

# Identify missing data using:
print(df.isnull())

# Handle missing data using:

# Drop missing values:
df_cleaned = df.dropna()

# Fill missing values:
df_filled = df.fillna(0)

# 5. How do you perform data cleaning and preprocessing in Pandas?
Answer:

# Use various functions for data cleaning and preprocessing.

# Apply a function to each element:
df['Age'] = df['Age'].apply(lambda x: x + 1)

print(df)

# Map values:
df['Gender'] = df['Gender'].map({'Male': 0, 'Female': 1})

# Change data type:
df['Age'] = df['Age'].astype(float)

df.head(3)

# 6. How do you merge, join, and concatenate DataFrames?
Answer:

import pandas as pd

# Creating two DataFrames
df1 = pd.DataFrame({'Name': ['shiv', 'ram', 'sita', 'gauri']})
df2 = pd.DataFrame({'Age': [23, 33, 20, 31]})

# Adding a common key column to both DataFrames to merge them on
df1['Key'] = [1, 2, 3, 4]
df2['Key'] = [1, 2, 3, 4]

# Merging the DataFrames on the 'Key' column
merged_df = pd.merge(df1, df2, on='Key')

# Dropping the 'Key' column after merging
merged_df.drop('Key', axis=1, inplace=True)

# Display the merged DataFrame
print(merged_df)


# Merge DataFrames:
# df_merged = pd.merge(df1, df2, on='key')

# Join DataFrames:
# df_joined = df1.join(df2, on='key')

# Concatenate DataFrames:
# df_concat = pd.concat([df1, df2])

# 7. How do you perform group operations and aggregations in Pandas?
Answer:

# Group data using .groupby():
# grouped = df.groupby('Category')

# Perform aggregations:
# grouped_sum = grouped['Value'].sum()
# grouped_mean = grouped['Value'].mean()

import pandas as pd

# Creating a sample DataFrame
data = {
    'Category': ['A', 'B', 'A', 'B', 'A', 'B', 'A', 'B'],
    'Value': [10, 20, 30, 40, 50, 60, 70, 80]
}

df = pd.DataFrame(data)

# Grouping the data by 'Category'
grouped = df.groupby('Category')

# Performing aggregations
grouped_sum = grouped['Value'].sum()
grouped_mean = grouped['Value'].mean()

# Display the results
print("Sum of Values by Category:")
print(grouped_sum)
print("\nMean of Values by Category:")
print(grouped_mean)


# 8. How do you sort and filter data in a DataFrame?
Answer:

# # Sort data:
# df_sorted = df.sort_values(by='Age')

# # Filter data:
# df_filtered = df[df['Age'] > 30]

import pandas as pd

# Sample DataFrame
data = {
    'Name': ['shiv', 'ram', 'sita', 'gauri','krishan'],
    'Age': [23, 33, 20, 31, 30]
}

df = pd.DataFrame(data)
print("Original DataFrame:")
print(df)


# Sort the DataFrame by 'Age'
df_sorted = df.sort_values(by='Age')

print("\nSorted DataFrame by Age:")
print(df_sorted)


# Filter the DataFrame to include only rows where 'Age' > 30
df_filtered = df[df['Age'] > 30]

print("\nFiltered DataFrame (Age > 30):")
print(df_filtered)


# 9. How do you visualize data in Pandas?
Answer:

# Create basic plots:
# df['Age'].plot(kind='hist')


# 'line': Line plot
# 'bar': Vertical bar plot
# 'barh': Horizontal bar plot
# 'pie': Pie chart
# 'scatter': Scatter plot
# 'box': Box plot
# 'kde': Kernel Density Estimate plot
# 'area': Area plot
# 'hexbin': Hexbin plot (for bivariate data)


# Integrate with Matplotlib for advanced visualizations:
import matplotlib.pyplot as plt

df['Age'].plot(kind='line')
plt.show()

# 10. How do you export data from a DataFrame?
Answer: 

# Export data to different formats.

# To CSV:
df1.to_csv('output.txt', index=False)

# To Excel:
# df1.to_excel('output.xlsx', index=False)

# To SQL:
from sqlalchemy import create_engine

engine = create_engine('sqlite:///:memory:')
df.to_sql('table_name', engine)


