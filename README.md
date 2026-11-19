# Exploring NYC Public School SAT Scores

A data analysis project in Python and pandas looking at SAT results from New York City public high schools. It finds the strongest schools in math, ranks schools by combined SAT score, and compares how much performance varies across the five boroughs.

*Completed as part of a DataCamp project.*

## Dataset

`schools.csv`: one row per NYC public high school, with these columns:

| Column | Description |
|---|---|
| `school_name` | Name of the school |
| `borough` | NYC borough the school is located in |
| `average_math` | Average SAT math score (max 800) |
| `average_reading` | Average SAT reading score (max 800) |
| `average_writing` | Average SAT writing score (max 800) |

## Questions and Approach

### 1. Which schools have the best math results?
"Best" is defined as at least 80% of the maximum math score (0.8 × 800 = **640**).

- Filtered schools with `average_math >= 640`
- Kept only `school_name` and `average_math`
- Sorted by `average_math` in descending order

**Result:** 10 schools met the threshold. **Stuyvesant High School** ranked first with an average math score of **754**.

### 2. What are the top 10 schools by combined SAT score?
- Created a new column, `total_SAT` = math + reading + writing
- Sorted by `total_SAT` in descending order and kept the top 10

**Result:** **Stuyvesant High School** ranked first with a combined score of **2144**, followed by Bronx High School of Science and Staten Island Technical High School (both **2041**).

### 3. Which borough has the largest standard deviation in combined SAT score?
- Grouped schools by `borough`
- Calculated the number of schools, mean and standard deviation of `total_SAT` for each borough
- Rounded values to two decimals and kept the borough with the highest standard deviation
- Renamed columns to `num_schools`, `average_SAT` and `std_SAT`

**Result:** **[BOROUGH]** shows the largest spread in performance (std: **[STD_SAT]**, across **[NUM_SCHOOLS]** schools, average total SAT: **[AVERAGE_SAT]**). Schools in this borough vary the most in performance, from very strong to much weaker.

## Skills Practised

- Filtering rows with boolean conditions (`>=`, `==`, `&`)
- Selecting multiple columns with `df[["col_a", "col_b"]]`
- Creating calculated columns from existing ones
- Sorting with `sort_values(ascending=False)` and taking top results with `head()`
- Method chaining
- Grouping and aggregation with `groupby()` and `agg(["count", "mean", "std"])`
- Renaming columns with `rename()` and moving the index into a column with `reset_index()`
- Rounding results with `round()`

## Tools

- Python
- pandas
