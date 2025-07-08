# Python Data Analysis: Pandas Library Exploration

## Overview

This repository contains a Google Colab notebook (`pandas day 1 Mitchel.ipynb`) that serves as a comprehensive introduction and hands-on exploration of the Pandas library in Python. It covers fundamental data manipulation techniques, essential for anyone working with structured datasets, and demonstrates practical applications through various exercises. This project showcases my foundational skills in data analysis, data cleaning, and feature understanding using Python.

## Objective

The primary objective of this notebook was to thoroughly explore the core functionalities of the Pandas library. This includes creating and importing DataFrames, performing essential exploratory data analysis (EDA), subsetting data, handling missing values, and applying various data filtering and sorting techniques.

## Key Skills Demonstrated

* 🐍 **Python Programming:** Foundational scripting and data handling.
* 🐼 **Pandas Library Proficiency:** Extensive use of DataFrame and Series objects for data manipulation.
* 📊 **Data Loading & Inspection:** Importing data from various formats (`.xlsx`, `.csv`) and quick data overview (`.head()`, `.tail()`, `.sample()`).
* 🔍 **Exploratory Data Analysis (EDA):** Understanding dataset structure (`.shape`, `.info()`, `.dtypes`), identifying missing values (`.isnull().sum()`), and summarizing numerical data (`.describe()`).
* 🧹 **Data Cleaning Basics:** Identifying and understanding the presence of missing values and duplicates.
* 🎯 **Data Subsetting & Indexing:** Advanced techniques for selecting data using both label-based (`.loc`) and integer-location based (`.iloc`) indexing.
* 📈 **Data Aggregation:** Calculating key statistics such as maximum, mean, and median values.
* ⚙️ **Conditional Filtering & Sorting:** Applying complex logical conditions to filter DataFrames and ordering results based on specific criteria.

## Notebook Highlights & Python Syntax Insights

This notebook systematically walks through key Pandas operations, providing clear examples and insights into their utility:

### 1. Initial Setup & DataFrame Creation

* **Importing Pandas:**
    ```python
    import pandas as pd
    ```
    *Insight:* Standard practice for aliasing Pandas as `pd` for conciseness.
* **Checking Version:**
    ```python
    pd.__version__
    ```
    *Insight:* Verifying the installed library version is a good habit for reproducibility.
* **Creating DataFrame from Dictionary:**
    ```python
    data = {"calories":[420, 380, 390], "duration": [50, 40, 45]}
    df = pd.DataFrame(data)
    print(df)
    ```
    *Insight:* Demonstrates the fundamental way to construct a DataFrame from Python dictionaries, mapping keys to column names.

### 2. Importing External Datasets

* **Google Colab File Upload:**
    ```python
    from google.colab import files
    uploaded = files.upload()
    ```
    *Insight:* Shows familiarity with environment-specific tools for data ingestion in cloud notebooks.
* **Reading Excel Files:**
    ```python
    df = pd.read_excel('student.xlsx')
    ```
    *Insight:* Essential for handling common data formats. The comment `"#excel format"` indicates clear understanding.

### 3. Exploratory Data Analysis (EDA)

* **Viewing Data Subsets:**
    ```python
    df.head() # First 5 rows
    df.tail(10) # Last 10 rows
    df.sample(5) # 5 random rows
    ```
    *Insight:* These methods are crucial for quickly inspecting data, understanding its structure, and identifying potential issues without printing the entire dataset.
* **DataFrame Dimensions & Information:**
    ```python
    df.shape # (rows, columns)
    df.info() # Non-null counts, dtypes, memory usage
    df.columns # Column names
    df.dtypes # Data types of each column
    ```
    *Insight:* `df.info()` is particularly powerful for a quick summary of data types and missing values, which is highlighted by the comment: "*if any of the columns has non-null count less than number of entries, that column has null (missing) values*".
* **Statistical Summary:**
    ```python
    df.describe()
    ```
    *Insight:* Provides descriptive statistics for numerical columns (count, mean, std, min, max, quartiles), crucial for understanding data distribution and identifying outliers, as noted: "*if std is very close or bigger than mean, there are outliers*".
* **Missing Values & Duplicates:**
    ```python
    df.isnull().sum() # Counts missing values per column
    df.duplicated().sum() # Counts duplicate rows
    ```
    *Insight:* Essential steps in data cleaning to assess data quality.

### 4. Subsetting DataFrames

* **Column Selection (Series vs. DataFrame):**
    ```python
    df['name'] # Returns a Series
    df[['id', 'name', 'gender', 'mark']] # Returns a DataFrame
    ```
    *Insight:* Clear distinction between selecting a single column (resulting in a Series) and multiple columns (resulting in a DataFrame), using single vs. double brackets.
* **Label-based Indexing with `.loc`:**
    ```python
    df.loc[0, "name"] # Selects a single cell
    df.loc[0:2, ["name", "gender"]] # Selects rows 0 to 2 (inclusive) and specific columns
    df.loc[df["class"]=="Four", ["name", "class", "gender"]] # Combines filtering with column selection
    ```
    *Insight:* `.loc` is emphasized for its label-based indexing, including its inclusive nature for slicing (`0:2` includes index `2`). This is a powerful and flexible method for complex data queries.
* **Integer-location based Indexing with `.iloc`:**
    ```python
    df.iloc[0:5, [0, 1]] # Selects first 5 rows (exclusive of 5) and first two columns by index
    ```
    *Insight:* `.iloc` is demonstrated for its integer-position based indexing, highlighting the exclusive nature of the stop index in slicing (e.g., `0:5` does not include index `5`).

### 5. Data Aggregation and Filtering

* **Basic Aggregations:**
    ```python
    df["mark"].max()
    df['mark'].mean()
    df['mark'].median()
    ```
    *Insight:* Fundamental statistical operations to summarize numerical data.
* **Conditional Filtering:**
    ```python
    df[df["gender"]=="female"] # Filter for female students
    df[df["class"]=="Six"] # Filter for students in 'Six' class
    ```
    *Insight:* Shows effective use of boolean indexing for filtering rows based on single conditions.
* **Combined Filtering and Sorting:**
    ```python
    df[(df["gender"] == "female") & (df["mark"] > df["mark"].mean())].sort_values(by="mark", ascending=False)
    ```
    *Insight:* This advanced query demonstrates combining multiple boolean conditions using `&` (AND operator) and then sorting the filtered results. This is a practical example of a multi-step data analysis workflow.
* **Sorting Data:**
    ```python
    df.sort_values(by="name") # Sorts alphabetically by name
    df.sort_values(by="mark") # Sorts numerically by mark (ascending by default)
    df.sort_values(by="mark", ascending=False) # Sorts numerically by mark (descending)
    ```
    *Insight:* Essential for organizing data for better readability and analysis.
* **Counting Unique Values:**
    ```python
    df["gender"].value_counts()
    ```
    *Insight:* Provides a quick summary of categorical data distribution, such as the count of male and female students.

## Tools and Environment

* 🐍 **Python:** The core programming language.
* 🐼 **Pandas:** The primary library used for all data manipulation and analysis.
* ☁️ **Google Colab:** The cloud-based Jupyter notebook environment used for developing and executing the code, facilitating collaborative and accessible data exploration.

## Conclusion

This Pandas exploration notebook serves as a strong foundation in data analysis using Python. It demonstrates a practical understanding of key Pandas functionalities, from initial data inspection and cleaning to advanced subsetting, aggregation, and conditional filtering. These skills are directly transferable to a wide range of data-centric roles, highlighting my ability to extract, transform, and derive meaningful insights from complex datasets.

---

![image](https://github.com/user-attachments/assets/d245f62c-40ba-4288-881b-7d44ca0edb59)
