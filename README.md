# Hotel Booking Demand Analysis

## Week 1 Internship Project

This project was completed as part of my **Week 1 Internship Task**.

The project focuses on understanding, analyzing, cleaning, and preparing the **Hotel Booking Demand Dataset** for further data analysis and machine learning work.

The complete workflow was performed using a Jupyter Notebook and includes:

- Data Understanding
- Data Quality Investigation
- Exploratory Data Analysis (EDA)
- Outlier Detection
- Data Cleaning
- Feature Engineering
- Final Dataset Validation

The purpose of the project was not only to analyze the data but also to understand the quality of the dataset, identify problems, make justified cleaning decisions, and produce a reliable final dataset.

---

# 1. Project Overview

Hotel booking data contains information about hotel reservations, guests, stays, room types, booking channels, cancellation status, prices, and other booking-related information.

The dataset used in this project contains booking records from two types of hotels:

- City Hotel
- Resort Hotel

The analysis was mainly focused on understanding booking patterns and cancellation behavior.

Some of the questions explored during the analysis were:

- Which hotel type has more cancellations?
- Does longer lead time relate to higher cancellation?
- Which customer types cancel more?
- Which market segments have higher cancellation rates?
- Does deposit type relate to cancellation behavior?
- Do new guests cancel more than repeated guests?
- Does changing the room type relate to booking behavior?
- Do cancelled bookings generally have longer lead times?

The project also focused on preparing a clean dataset that can be used for future analytical or machine learning tasks.

---

# 2. Project Objectives

The main objectives of this Week 1 project were:

1. Understand the structure and contents of the hotel booking dataset.
2. Identify the different types of variables available.
3. Investigate missing values.
4. Detect duplicate records.
5. Identify inconsistent categorical values.
6. Check data type issues.
7. Identify unnecessary or identifier-like columns.
8. Perform exploratory data analysis.
9. Analyze numerical and categorical variables.
10. Study relationships between booking variables and cancellation.
11. Perform correlation analysis.
12. Detect potential outliers using IQR and Z-score methods.
13. Investigate extreme values before making treatment decisions.
14. Clean the dataset.
15. Correct data types.
16. Standardize categories where required.
17. Remove redundant or unnecessary information where justified.
18. Create useful new features.
19. Validate the final dataset.
20. Export the cleaned dataset for future use.

---

# 3. Dataset

## Source Dataset

The original dataset used in this project is:

`hotel_bookings.csv`

The dataset contains:

- **119,390 rows**
- **32 columns**

The original dataset contains information related to:

- Hotel type
- Booking status
- Lead time
- Arrival dates
- Length of stay
- Number of guests
- Meal type
- Country
- Market segment
- Distribution channel
- Previous booking history
- Room types
- Deposit type
- Customer type
- Average daily rate
- Special requests
- Reservation status

---

# 4. Dataset Structure

The main groups of variables in the dataset are:

### Hotel Information

- `hotel`

This identifies whether the booking belongs to a City Hotel or Resort Hotel.

### Booking Information

- `is_canceled`
- `lead_time`
- `booking_changes`
- `deposit_type`
- `market_segment`
- `distribution_channel`

### Arrival Information

- `arrival_date_year`
- `arrival_date_month`
- `arrival_date_week_number`
- `arrival_date_day_of_month`

### Stay Information

- `stays_in_weekend_nights`
- `stays_in_week_nights`

### Guest Information

- `adults`
- `children`
- `babies`
- `is_repeated_guest`

### Previous Booking Information

- `previous_cancellations`
- `previous_bookings_not_canceled`

### Room Information

- `reserved_room_type`
- `assigned_room_type`

### Customer Information

- `customer_type`
- `country`

### Financial Information

- `adr`

### Other Booking Information

- `required_car_parking_spaces`
- `total_of_special_requests`
- `days_in_waiting_list`

### Reservation Information

- `reservation_status`
- `reservation_status_date`

---

# 5. Tools and Libraries

The analysis was performed using Python in a Jupyter Notebook environment.

The main libraries used were:

### Pandas

Used for:

- Loading the CSV dataset
- Data inspection
- Missing value analysis
- Duplicate detection
- Data cleaning
- Feature engineering
- Data export

### NumPy

Used for numerical operations and working with numerical data.

### Matplotlib

Used for creating visualizations and plots.

### Seaborn

Used for statistical visualizations such as:

- Histograms
- Count plots
- Box plots
- Bar plots
- Correlation heatmaps

### SciPy

Used for statistical analysis, including Z-score based outlier detection.

### Scikit-learn

Used for outlier-related analysis and the `IsolationForest` method during the analytical workflow.

---

# 6. Data Understanding

The first stage of the project was Data Understanding.

The dataset was loaded into a Pandas DataFrame and inspected to understand its structure.

The initial dataset contained:

**119,390 rows × 32 columns**

The following were examined:

- Dataset shape
- First records
- Last records
- Column names
- Data types
- Numerical variables
- Categorical variables
- Summary statistics

This helped establish a clear understanding of the dataset before performing cleaning or analysis.

---

# 7. Data Quality Investigation

After understanding the dataset, I investigated the quality of the data.

The main areas checked were:

- Missing values
- Duplicate records
- Inconsistent categories
- Data type issues
- Identifier-like variables
- Potentially unnecessary columns

---

## 7.1 Missing Value Analysis

Missing values were checked using Pandas.

The main columns containing missing values were:

- `children`
- `country`
- `agent`
- `company`

The number and percentage of missing values were calculated for each column.

The missing values were not removed immediately.

Instead, they were investigated first so that the final treatment could be based on the meaning of each variable.

---

# 8. Duplicate Detection

Duplicate records were an important data quality issue in the original dataset.

The initial duplicate check identified:

**31,994 duplicate rows**

This represented approximately:

**26.80% of the original dataset**

The duplicated rows were inspected before removal.

The duplicates were treated as redundant complete records rather than meaningful separate observations.

They were therefore removed during the cleaning stage.

This significantly reduced the size of the dataset and helped prevent repeated records from affecting the analysis.

---

# 9. Inconsistent Categories

Categorical variables were examined using their unique values and frequency distributions.

Most categories were consistently formatted.

However, some `Undefined` values were found.

Examples included:

- `meal`
- `market_segment`
- `distribution_channel`

The `meal` column contained a larger number of `Undefined` observations, while only a very small number occurred in `market_segment` and `distribution_channel`.

These values were investigated before deciding how they should be handled.

Rare room types were also observed.

Rare categories were not automatically removed because being rare does not necessarily mean that a value is incorrect.

---

# 10. Data Type Investigation

The data types of the variables were examined to identify values that were stored in an unsuitable format.

One important issue was:

`reservation_status_date`

It was initially stored as an object/string variable even though it represented dates.

It was therefore converted to a proper datetime format during cleaning.

The `agent` and `company` variables were also investigated.

Although they were stored as numerical values, they represent identifiers rather than continuous measurements.

The `children` variable was also investigated because it was stored as `float64` due to its missing values.

---

# 11. Exploratory Data Analysis

After data quality investigation, Exploratory Data Analysis (EDA) was performed.

EDA was divided into:

- Univariate Analysis
- Categorical Analysis
- Numerical Distribution Analysis
- Bivariate Analysis
- Correlation Analysis
- Business Questions
- Key Insights

---

# 12. Univariate Analysis

Univariate analysis was used to study individual variables separately.

The numerical variables were identified first.

The analysis included:

- Lead time
- Weekend stay nights
- Weekday stay nights
- Adults
- Children
- Babies
- Booking cancellation status

---

## 12.1 Lead Time

The `lead_time` distribution was strongly right-skewed.

Most bookings had relatively low lead times, while fewer bookings were made many months in advance.

The distribution had a long right tail extending to very high lead-time values.

These extreme values were not removed during EDA because they required further investigation during the outlier analysis.

---

## 12.2 Weekend Stay Nights

Most bookings contained zero weekend nights.

One- and two-night weekend stays were also common.

Longer weekend stays occurred much less frequently.

The variable showed a right-skewed distribution with a small number of longer stays.

---

## 12.3 Weekday Stay Nights

Most bookings had relatively short weekday stays.

The highest concentration was around one to a few weekday nights.

Longer weekday stays were much less common.

The distribution was strongly right-skewed.

---

## 12.4 Adults per Booking

Bookings with two adults were the most common.

Bookings with one adult were also common, while larger groups occurred less frequently.

A small number of bookings contained unusually large numbers of adults.

These values were considered during the later outlier investigation.

---

## 12.5 Children per Booking

The `children` variable was strongly concentrated at zero.

Most bookings did not include children.

Bookings with one or two children occurred less frequently.

There were also a few unusual values, including a booking with 10 children.

The four missing values were identified during the missing-value analysis.

---

## 12.6 Babies per Booking

The `babies` variable was also strongly concentrated at zero.

Most bookings did not include babies.

Bookings containing one or more babies were uncommon.

A few unusually high values were observed and were considered during outlier investigation.

---

## 12.7 Booking Cancellation Status

The `is_canceled` variable was analyzed to understand the overall cancellation pattern.

The analysis showed that both canceled and non-canceled bookings were present in the dataset, with non-canceled bookings forming the larger group.

This variable was also used as the main outcome variable in several bivariate analyses.

---

# 13. Categorical Analysis

Categorical variables were analyzed using frequency counts and visualizations.

The analysis included:

- Hotel type
- Arrival month
- Meal type
- Market segment
- Distribution channel
- Deposit type
- Customer type
- Reservation status
- Country
- Top 10 countries
- Reserved room type
- Assigned room type

These analyses helped identify the most common categories and understand the structure of hotel bookings.

---

# 14. Numerical Distribution Analysis

Numerical variables were further examined using:

- Summary statistics
- Skewness
- Box plots
- Distribution plots

This helped identify:

- Central tendencies
- Spread
- Skewed variables
- Potential extreme values
- Variables with many zero observations

Variables such as lead time, stay duration, adults, children, babies, and ADR showed different distribution patterns and were considered separately rather than assuming all numerical variables followed the same distribution.

---

# 15. Bivariate Analysis

Bivariate analysis was used to study relationships between two variables.

The main focus was the relationship between different booking characteristics and cancellation status.

The following relationships were investigated:

1. Hotel type vs cancellation
2. Lead time vs cancellation
3. Stay duration vs cancellation
4. ADR vs cancellation
5. Market segment vs cancellation
6. Customer type vs cancellation
7. Deposit type vs cancellation
8. Special requests vs cancellation
9. Repeated guest vs cancellation
10. Reserved room type vs assigned room type

---

## 15.1 Hotel Type vs Cancellation

City Hotels had more cancellations than Resort Hotels.

This indicates that hotel type is related to cancellation behavior in the dataset.

---

## 15.2 Lead Time vs Cancellation

Bookings with longer lead times showed a stronger relationship with cancellation.

This suggests that customers who book further in advance may be more likely to cancel.

---

## 15.3 Stay Duration vs Cancellation

Stay duration was compared between canceled and non-canceled bookings.

The analysis helped identify whether longer stays were associated with different cancellation patterns.

---

## 15.4 ADR vs Cancellation

ADR represents the average daily rate.

ADR was compared between canceled and non-canceled bookings to determine whether room price differed between the two groups.

The analysis showed that booking price has a relationship with cancellation behavior, although cancellation cannot be explained by ADR alone.

---

## 15.5 Market Segment vs Cancellation

Different market segments showed different cancellation proportions.

This indicates that the source through which a booking is made can be related to cancellation behavior.

---

## 15.6 Customer Type vs Cancellation

Cancellation behavior differed across customer types.

This helped identify differences between transient, contract, group, and transient-party bookings.

---

## 15.7 Deposit Type vs Cancellation

Deposit type showed a strong relationship with cancellation behavior.

Bookings with different deposit arrangements did not have the same cancellation pattern.

This makes deposit type an important variable when studying hotel cancellations.

---

## 15.8 Special Requests vs Cancellation

The number of special requests was compared with cancellation behavior.

Bookings with more special requests generally showed lower cancellation levels.

This suggests that customers who make more specific requests may be more committed to their bookings.

---

## 15.9 Repeated Guest vs Cancellation

Repeated guests showed lower cancellation behavior compared with new guests.

This indicates that returning customers may be more reliable than first-time guests.

---

## 15.10 Reserved vs Assigned Room Type

Reserved room type was compared with assigned room type.

Most bookings kept the same room type that was originally reserved.

This shows that room assignment generally follows the original reservation.

---

# 16. Correlation Analysis

Correlation analysis was used to understand relationships between numerical variables.

Important relationships examined included:

- Lead time and cancellation
- Previous cancellations and current cancellation
- Total special requests and cancellation
- Previous bookings not canceled and cancellation
- Stay duration variables

The analysis showed that some variables had stronger relationships with cancellation than others.

Lead time showed an important positive relationship with cancellation.

Previous cancellation history was also an important indicator of current cancellation behavior.

Special requests showed an inverse relationship with cancellation.

Weekend and weekday stay nights were positively related because both represent parts of the total stay duration.

Correlation was interpreted as a relationship rather than proof of causation.

---

# 17. Business Questions

The analysis was also used to answer practical business questions.

### 1. Which hotel type has more cancellation?

City Hotels had more cancellations than Resort Hotels.

### 2. Does longer lead time increase cancellation?

Longer lead times were associated with higher cancellation behavior.

### 3. Which customer type cancels the most?

Cancellation patterns differed between customer types, with transient-related bookings showing important cancellation activity.

### 4. Which market segment has the highest cancellation?

Cancellation levels varied across market segments, with some booking channels showing considerably higher cancellation proportions than others.

### 5. Does deposit type affect cancellation?

Yes.

Deposit type showed a strong relationship with cancellation behavior, particularly because different deposit arrangements have very different cancellation patterns.

### 6. Do new guests cancel more than repeated guests?

Yes.

Repeated guests were generally more reliable, while new guests showed higher cancellation behavior.

### 7. Does changing the room type affect bookings?

Room changes were investigated by comparing reserved and assigned room types.

Most bookings kept the room type they originally reserved, while some bookings were assigned a different room type.

### 8. Do cancelled bookings have longer lead times?

Generally, canceled bookings showed longer lead times than non-canceled bookings.

---

# 18. Key Insights

The main insights from the analysis were:

- City Hotels had more cancellations.
- Longer lead time was associated with higher cancellation.
- New guests were more likely to cancel than repeated guests.
- Previous cancellation history was an important indicator of current cancellation.
- Deposit type had a strong relationship with cancellation.
- Special requests were generally associated with lower cancellation.
- Repeated guests appeared more reliable.
- Canceled bookings generally had longer lead times.
- Most bookings kept their originally reserved room type.
- Booking behavior differed across market segments and customer types.

---

# 19. Outlier Detection

Outliers were investigated using two statistical methods:

1. Interquartile Range (IQR)
2. Z-score

The purpose was not to automatically remove every statistical outlier.

Instead, the goal was to identify unusual observations and determine whether they represented genuine hotel booking behavior or possible data-quality problems.

---

# 20. IQR Method

The Interquartile Range method was used to identify potential outliers in numerical variables.

The IQR is calculated as:

**IQR = Q3 - Q1**

The lower and upper boundaries are:

**Lower Bound = Q1 - 1.5 × IQR**

**Upper Bound = Q3 + 1.5 × IQR**

Values outside these boundaries were classified as potential outliers.

The IQR method was useful for identifying extreme values in variables such as:

- Lead time
- ADR
- Stay duration
- Guest counts
- Previous booking variables

---

# 21. Z-score Method

The Z-score method was also used to identify extreme numerical observations.

The formula is:

**Z = (X - μ) / σ**

Where:

- X = observed value
- μ = mean
- σ = standard deviation

A commonly used threshold is:

**|Z| > 3**

Observations beyond this threshold were considered potential extreme values.

---

# 22. IQR and Z-score Comparison

Both methods were compared because they identify unusual observations in different ways.

The IQR method is based on quartiles and is less affected by extreme values.

The Z-score method is based on the mean and standard deviation and can be more sensitive to extreme observations.

The comparison helped determine which variables contained strong extreme values and whether those values required further investigation.

---

# 23. Investigating Outliers

Potential outliers were investigated rather than removed automatically.

Particular attention was given to:

### ADR

Extreme ADR values were examined to determine whether they could represent unusually expensive bookings or possible data errors.

### Lead Time

Very high lead-time values were investigated because they represent bookings made far in advance.

These values were not automatically treated as incorrect simply because they were statistically unusual.

---

# 24. Outlier Treatment Decision

The final outlier treatment followed these principles:

- Outliers were not removed solely because they were classified as outliers.
- Discrete and zero-inflated variables were retained.
- Legitimate extreme values were preserved.
- Potentially erroneous values were investigated separately.
- If outlier treatment is required for a future machine learning model, techniques such as capping or winsorization may be considered for selected continuous variables.
- The cleaned dataset retains valid original observations.

This approach prevents genuine hotel booking behavior from being incorrectly removed.

---

# 25. Data Cleaning

After the investigation and EDA, the dataset was cleaned.

The cleaning process included:

- Missing value treatment
- Duplicate treatment
- Category standardization
- Data type correction
- Unnecessary column handling
- Final quality checking

The cleaning decisions were based on the observations made during the earlier analysis.

---

# 26. Missing Value Treatment

Missing values were handled based on the meaning and role of each variable.

The goal was to produce a complete dataset without introducing misleading values.

After cleaning and validation:

**Final missing values = 0**

This means that no missing values remained in the final dataset.

---

# 27. Duplicate Treatment

The original dataset contained:

**31,994 duplicate rows**

These were removed during the cleaning stage.

After the initial duplicate treatment, the dataset was checked again to confirm that the duplicate records had been removed.

A final quality check later identified a small number of remaining duplicate observations created by identical records after feature engineering.

These were investigated and removed during the final validation process.

The final duplicate check confirmed:

**0 duplicate rows**

---

# 28. Category Standardization

Categorical variables were reviewed for inconsistent values.

The identified categories were checked and standardized where required.

Undefined or inconsistent category values were handled according to their meaning rather than being removed blindly.

Rare but valid categories were retained.

---

# 29. Data Type Correction

The most important data type correction involved:

`reservation_status_date`

The column was converted from an object/string format into a proper datetime format.

This allows the date field to be used correctly for:

- Date-based analysis
- Sorting
- Filtering
- Feature creation
- Future machine learning preprocessing

Identifier-like fields such as `agent` and `company` were treated as identifiers rather than continuous numerical measurements.

---

# 30. Unnecessary Column Handling

The dataset was reviewed for columns that were redundant, unsuitable, or unnecessary for the analysis.

Columns were not removed simply because they had many missing values or low variation.

The decision to retain or remove variables was based on their analytical relevance and usefulness.

---

# 31. Final Data Quality Check

After cleaning, the dataset was checked again.

The following were verified:

- Dataset shape
- Missing values
- Duplicate rows
- Data types
- Feature values
- Feature-engineered columns

During the final duplicate verification, a small number of remaining duplicate records were identified.

The duplicated records were inspected and removed.

The final validation confirmed:

**Missing values: 0**

**Duplicate rows: 0**

---

# 32. Feature Engineering

After cleaning the dataset, four new features were created.

Feature engineering was performed to create variables that provide a more direct representation of booking behavior.

The four engineered features were:

1. `total_stay_nights`
2. `total_guests`
3. `is_family`
4. `is_long_stay`

---

# 33. Feature 1 — Total Stay Nights

The first feature was:

`total_stay_nights`

It combines:

- Weekend nights
- Weekday nights

The calculation is:

**Total Stay Nights = Weekend Nights + Week Nights**

This gives a single variable representing the total length of the hotel stay.

---

# 34. Feature 2 — Total Guests

The second feature was:

`total_guests`

It combines:

- Adults
- Children
- Babies

The calculation is:

**Total Guests = Adults + Children + Babies**

This provides a clearer representation of the total number of guests associated with a booking.

---

# 35. Feature 3 — Family Booking

The third feature was:

`is_family`

This identifies whether a booking includes children or babies.

A booking is considered a family booking when:

**Children > 0 OR Babies > 0**

The feature provides a simple indicator that can be used to compare family and non-family bookings.

---

# 36. Feature 4 — Long Stay

The fourth feature was:

`is_long_stay`

This identifies bookings that have a relatively long stay based on the selected stay-duration threshold.

The feature converts stay duration into a simple indicator that can be used for comparison and future modeling.

---

# 37. Feature Validation

The newly created features were validated to make sure that their values were logically consistent.

### Total Stay Validation

`total_stay_nights` was checked against:

`stays_in_weekend_nights + stays_in_week_nights`

### Total Guest Validation

`total_guests` was checked against:

`adults + children + babies`

### Family Booking Validation

`is_family` was checked against the presence of children or babies.

### Long Stay Validation

`is_long_stay` was checked against the total stay duration and the selected threshold.

These checks confirmed that the engineered features were logically based on the original variables.

---

# 38. Final Dataset

After completing data cleaning and feature engineering, the final dataset contained:

**87,389 rows**

and

**36 columns**

The original dataset had 32 columns.

Four additional features were created:

- `total_stay_nights`
- `total_guests`
- `is_family`
- `is_long_stay`

---

# 39. Final Dataset Quality

The final dataset was checked for the main data quality problems.

| Quality Check | Final Result |
|---|---:|
| Rows | 87,389 |
| Columns | 36 |
| Missing Values | 0 |
| Duplicate Rows | 0 |
| Feature-Engineered Columns | 4 |

The final dataset is therefore complete with respect to missing values and duplicate records and is ready for further analysis or machine learning preprocessing.

---

# 40. Project Files

The GitHub repository contains the following project files:

### `hotel_booking_demand_analysis.ipynb`

This is the complete Jupyter Notebook containing:

- Python code
- Data understanding
- Data quality investigation
- EDA
- Visualizations
- Outlier analysis
- Cleaning
- Feature engineering
- Validation
- Findings

### `hotel_bookings.csv`

This is the original source dataset used for the project.

### `hotel_bookings_cleaned.csv`

This is the final cleaned and feature-engineered dataset.

It contains:

- 87,389 rows
- 36 columns
- 0 missing values
- 0 duplicate rows

### `hotel_booking_demand_technical_report.pdf`

This contains the detailed technical report of the project.

### `README.md`

This file provides an overview and documentation of the project workflow, analysis, cleaning process, and final results.

---

# 41. Project Workflow

The complete Week 1 workflow can be summarized as:

**Source Dataset**

↓

**Data Understanding**

↓

**Data Quality Investigation**

↓

**Exploratory Data Analysis**

↓

**Bivariate & Correlation Analysis**

↓

**Business Questions**

↓

**Outlier Detection**

↓

**Outlier Investigation**

↓

**Data Cleaning**

↓

**Feature Engineering**

↓

**Feature Validation**

↓

**Final Data Quality Check**

↓

**Clean Dataset**

---

# 42. Final Summary

This Week 1 internship project provided a complete practical workflow for working with a real-world hotel booking dataset.

I started by understanding the structure of the dataset and identifying the types of variables available.

I then investigated data quality issues including missing values, duplicate records, inconsistent categories, and incorrect data types.

The dataset originally contained **119,390 records and 32 variables**. A major issue identified during the investigation was the presence of **31,994 duplicate rows**.

After the data quality investigation, I performed exploratory data analysis to understand booking patterns and cancellation behavior.

The analysis included numerical distributions, categorical analysis, bivariate relationships, correlation analysis, and business-focused questions.

I also investigated outliers using both the **IQR method** and the **Z-score method**. Instead of automatically removing statistical outliers, I investigated whether extreme values could represent valid hotel booking behavior.

After completing the analysis, I cleaned the dataset by treating missing values, removing duplicate records, correcting data types, and standardizing categories where necessary.

I then created four new features:

- `total_stay_nights`
- `total_guests`
- `is_family`
- `is_long_stay`

These features provide additional information about the length of stay and guest characteristics.

The final dataset contains:

**87,389 rows × 36 columns**

with:

**0 missing values**

and:

**0 duplicate rows**

The completed dataset, notebook, source data, and technical report are included in this repository as the complete submission for the Week 1 internship task.

---

# 43. Conclusion

The project successfully completed the required data analysis and preparation workflow for the Hotel Booking Demand Dataset.

The analysis showed several important patterns, particularly around cancellation behavior. Hotel type, lead time, customer type, deposit type, market segment, previous cancellation history, repeated guest status, and special requests were among the variables that provided useful information about booking cancellations.

The final cleaned dataset provides a structured foundation for future work such as:

- Cancellation prediction
- Customer behavior analysis
- Hotel demand analysis
- Feature-based machine learning
- Classification modeling
- Business intelligence and visualization

The project demonstrates the complete process of taking a raw dataset, understanding its structure, investigating its quality, analyzing its patterns, cleaning it, creating useful features, and validating the final output.