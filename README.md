<img width="198" height="88" alt="image" src="https://github.com/user-attachments/assets/100950eb-9c79-49f8-81b6-dbd2166774a2" /><img width="198" height="88" alt="image" src="https://github.com/user-attachments/assets/abbeb71f-4cfe-437c-ba0e-5fc6ccd3639a" /># 🏠 Airbnb Listings Data Analysis

## 📊 Exploratory Data Analysis using Python, Pandas, NumPy, Matplotlib & Seaborn

This project presents an **Exploratory Data Analysis (EDA)** of an Airbnb listings dataset. The analysis focuses on understanding Airbnb listing characteristics, pricing patterns, availability, reviews, room types, neighbourhood-level differences, and relationships between numerical variables.

The project demonstrates a complete data analysis workflow using Python, starting from dataset loading and data inspection to data cleaning, preprocessing, visualization, statistical analysis, and insight generation.

---


## 📌 Project Overview

Airbnb datasets contain valuable information about properties, hosts, locations, prices, reviews, room types, and availability.

In this project, the dataset was analyzed to explore questions such as:

- How is Airbnb listing price distributed?
- Are there significant price differences across neighbourhood groups?
- How does room type affect listing prices?
- Which neighbourhood groups have higher average prices?
- How does price per bed vary across locations?
- What is the distribution of listing availability throughout the year?
- Is there a relationship between price and the number of beds?
- How are Airbnb listings geographically distributed?
- What relationships exist between price, reviews, minimum nights, and availability?

The project follows a structured data analysis workflow:

> **Data Import → Data Inspection → Data Cleaning → Data Preprocessing → Univariate Analysis → Bivariate Analysis → Multivariate Analysis → Correlation Analysis → Insights**

---


# 🎯 Project Objectives

The main objectives of this project are:

1. Understand the structure and characteristics of the Airbnb dataset.
2. Identify and handle missing values.
3. Detect and remove duplicate records.
4. Inspect and prepare appropriate data types.
5. Analyze Airbnb price distributions.
6. Identify extreme values and potential price outliers.
7. Analyze listing availability.
8. Compare average prices across neighbourhood groups.
9. Analyze pricing differences across room types.
10. Calculate and analyze average price per bed.
11. Explore the relationship between reviews and listing prices.
12. Visualize the geographical distribution of Airbnb listings.
13. Analyze correlations among important numerical variables.
14. Generate meaningful insights from the dataset.

---


# 🗂️ Dataset Description

The dataset contains Airbnb listing information, including property details, host information, geographical information, pricing, reviews, and availability.

The initial dataset contains:

| Dataset Metric | Value |
|---|---:|
| Initial Records | 20,770 |
| Initial Columns | 22 |
| Memory Usage | Approximately 3.5 MB |

The original dataset contains the following major categories of variables:

### 🏠 Property Information

- `name`
- `room_type`
- `bedrooms`
- `beds`
- `baths`

### 👤 Host Information

- `host_id`
- `host_name`
- `calculated_host_listings_count`

### 📍 Location Information

- `neighbourhood_group`
- `neighbourhood`
- `latitude`
- `longitude`

### 💰 Pricing Information

- `price`

### ⭐ Review Information

- `number_of_reviews`
- `number_of_reviews_ltm`
- `reviews_per_month`
- `last_review`
- `rating`

### 📅 Availability Information

- `availability_365`

### 📄 Other Information

- `id`
- `minimum_nights`
- `license`

---


# 🛠️ Technologies & Libraries Used

The project was developed using Python and the following libraries:

| Technology / Library | Purpose |
|---|---|
| Python | Programming language |
| Pandas | Data manipulation and analysis |
| NumPy | Numerical operations |
| Matplotlib | Data visualization |
| Seaborn | Statistical visualization |
| Jupyter Notebook | Development and analysis environment |

### Libraries Imported

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```


________________________________________
🔄 Project Workflow
The project follows the following workflow:
                ┌─────────────────────┐
                │   Import Libraries  │
                └──────────┬──────────┘
                           ↓
                ┌─────────────────────┐
                │    Import Dataset   │
                └──────────┬──────────┘
                           ↓
                ┌─────────────────────┐
                │   Data Exploration  │
                └──────────┬──────────┘
                           ↓
                ┌─────────────────────┐
                │    Data Cleaning    │
                └──────────┬──────────┘
                           ↓
                ┌─────────────────────┐
                │ Data Type Handling  │
                └──────────┬──────────┘
                           ↓
                ┌─────────────────────┐
                │   Univariate EDA    │
                └──────────┬──────────┘
                           ↓
                ┌─────────────────────┐
                │   Bivariate EDA     │
                └──────────┬──────────┘
                           ↓
                ┌─────────────────────┐
                │ Multivariate EDA    │
                └──────────┬──────────┘
                           ↓
                ┌─────────────────────┐
                │ Correlation Analysis│
                └──────────┬──────────┘
                           ↓
                ┌─────────────────────┐
                │   Key Insights      │
                └─────────────────────┘
________________________________________
🔍 1. Data Import
The dataset was imported using Pandas:
```data = pd.read_csv("datasets.csv")
```
The initial dataset was inspected using:
```data.head()
```
This allowed the structure and sample records of the dataset to be reviewed before beginning the analysis.
________________________________________
🔎 2. Data Exploration
Several Pandas functions were used to understand the dataset:
View the first records
data.head()
Check dataset dimensions
data.shape
The initial shape was:
(20770, 22)
Inspect data types and missing values
data.info()
The dataset initially contained:
•	20,770 records
•	22 columns
•	10 float64 columns
•	2 int64 columns
•	10 string columns
________________________________________
📈 3. Descriptive Statistics
The describe() function was used to obtain descriptive statistics for numerical variables:
data.describe()
Important numerical variables included:
•	price
•	minimum_nights
•	number_of_reviews
•	reviews_per_month
•	calculated_host_listings_count
•	availability_365
•	number_of_reviews_ltm
•	beds
Selected statistics
Variable	Mean	Median	Maximum
Price	187.71	125.00	100,000
Minimum Nights	28.56	30.00	1,250
Number of Reviews	42.61	14.00	1,865
Reviews per Month	1.26	0.65	75.49
Availability (365)	206.07	215.00	365
Beds	1.72	1.00	42
The price variable shows a substantial difference between the mean and median, indicating a strongly right-skewed distribution.
________________________________________
🧹 4. Data Cleaning
Data cleaning was performed before conducting the main analysis.
4.1 Missing Value Detection
Missing values were identified using:
data.isnull().sum()
Some variables contained missing values, including:
•	neighbourhood
•	latitude
•	longitude
•	room_type
•	price
•	minimum_nights
•	number_of_reviews
•	last_review
•	reviews_per_month
•	availability_365
________________________________________
4.2 Handling Missing Values
Rows containing missing values were removed using:
data.dropna(inplace=True)
The number of records decreased from:
20,770
to:
20,736
________________________________________
♻️ 5. Duplicate Record Detection
Duplicate records were identified using:
data.duplicated().sum()
The dataset contained:
12 duplicate records
The duplicate records were removed using:
data.drop_duplicates(inplace=True)
After removing duplicates:
data.duplicated().sum()
returned:
0
The cleaned dataset contained:
20,724 records
________________________________________
💡 6. Key Insights
Based on the exploratory analysis, several observations were identified.
1. Price Distribution
Airbnb prices are strongly right-skewed, with most observations concentrated at lower-to-moderate price levels and a smaller number of high-price listings.
2. Location Matters
Average listing prices differ considerably across neighbourhood groups.
Manhattan recorded the highest average price among the five neighbourhood groups analyzed.
3. Price per Bed
Manhattan also recorded the highest average price per bed.
4. Room Type
Listing prices vary according to both neighbourhood group and room type.
5. Availability
Airbnb listings show substantial variation in annual availability.
6. Beds and Price
The number of beds has the strongest positive correlation with price among the selected numerical variables.
7. Reviews and Price
The number of reviews has only a very weak correlation with price in the analyzed dataset.
8. Geographical Distribution
Airbnb listings are geographically concentrated across different locations, with room types distributed throughout the analyzed area.
________________________________________
📌 Summary of Findings
Analysis Area	Main Finding
Dataset Size	20,770 initial records
Cleaned Dataset	20,724 records
Duplicate Records	12 removed
Price Distribution	Strong right skew
Highest Average Price	Manhattan
Lowest Average Price	Bronx
Highest Price per Bed	Manhattan
Strongest Price Correlation	Beds (0.415)
Price vs Reviews	Very weak correlation
Price vs Availability	Very weak correlation
________________________________________
🧰 Skills Demonstrated
This project demonstrates practical skills in:
Python
•	Variables
•	Functions
•	Data structures
•	Basic data manipulation
Pandas
•	Reading CSV files
•	DataFrame exploration
•	head()
•	shape
•	info()
•	describe()
•	Missing value detection
•	dropna()
•	Duplicate detection
•	drop_duplicates()
•	groupby()
•	Creating calculated columns
•	Correlation analysis
NumPy
•	Numerical operations
•	Supporting data analysis workflows
Seaborn
•	Boxplots
•	Histograms
•	Barplots
•	Scatterplots
•	Pairplots
•	Heatmaps
Matplotlib
•	Figure sizing
•	Titles
•	Axis labels
•	Plot customization
•	Visualization presentation
________________________________________
📁 Project Structure
A recommended GitHub repository structure is:
Airbnb-Data-Analysis/
│
├── 📓 Airbnb_Data_Analysis.ipynb
│
├── 📊 datasets.csv
│
├── 🖼️ images/
│   ├── price_distribution.png
│   ├── availability_distribution.png
│   ├── average_price_by_neighbourhood.png
│   ├── price_per_bed.png
│   ├── room_type_price.png
│   ├── geographical_distribution.png
│   ├── pairplot.png
│   └── correlation_heatmap.png
│
├── 📄 Airbnb_Data_Analysis_Report.pdf
│
└── README.md
The exact filenames can be changed according to the files included in the repository.
________________________________________
▶️ How to Run the Project
1. Clone the Repository
git clone YOUR_GITHUB_REPOSITORY_URL
2. Navigate to the Project Directory
cd Airbnb-Data-Analysis
3. Install Required Libraries
pip install pandas numpy matplotlib seaborn jupyter
4. Open the Jupyter Notebook
jupyter notebook
or:
jupyter lab
5. Open
Airbnb_Data_Analysis.ipynb
Run the notebook cells sequentially to reproduce the analysis.
________________________________________
📷 Project Visualizations
Price Distribution
The price distribution demonstrates a strongly right-skewed pattern, with a large concentration of listings at lower price levels and a long tail of expensive listings.
Availability Distribution
The availability analysis shows considerable variation in the number of days listings are available throughout the year.
Neighbourhood Pricing
Average listing prices vary significantly across neighbourhood groups, with Manhattan showing the highest average price.
Price per Bed
Price-per-bed analysis provides an additional perspective for comparing accommodation costs across neighbourhood groups.
Geographical Distribution
Latitude and longitude were used to visualize the geographical distribution of Airbnb listings and room types.
Correlation Heatmap
The correlation heatmap provides an overview of relationships among price, beds, reviews, availability, minimum nights, latitude, and longitude.
________________________________________
📚 Analysis Approach
The project follows a structured EDA methodology:

1. Import Python Libraries

          ↓

2. Load Dataset

          ↓

3. Explore Dataset

          ↓

4. Check Data Types

          ↓

5. Identify Missing Values

          ↓

6. Remove Missing Records

          ↓

7. Detect & Remove Duplicates

          ↓

8. Prepare Data Types

          ↓

9. Univariate Analysis

          ↓

10. Outlier Analysis

          ↓

11. Bivariate Analysis

          ↓

12. Multivariate Analysis

          ↓

13. Geographical Analysis

          ↓

14. Correlation Analysis

          ↓

15. Generate Insights
________________________________________
🚀 Future Improvements
The current project focuses primarily on exploratory data analysis. The project can be extended in several directions.
Possible future work:
•	Build an interactive dashboard using Power BI
•	Perform advanced statistical analysis
•	Apply feature engineering
•	Analyze neighbourhood-level trends in greater detail
•	Perform time-series analysis using review dates
•	Develop a machine learning model for price prediction
•	Compare different regression algorithms
•	Perform model evaluation using RMSE, MAE and R²
•	Develop an interactive web-based visualization dashboard
________________________________________
🎓 Learning Outcomes
Through this project, the following practical data analysis concepts were applied:
•	Dataset exploration
•	Data cleaning
•	Missing value handling
•	Duplicate detection
•	Data type conversion
•	Descriptive statistics
•	Outlier identification
•	Univariate analysis
•	Bivariate analysis
•	Multivariate analysis
•	GroupBy analysis
•	Feature engineering
•	Data visualization
•	Correlation analysis
•	Insight generation
________________________________________
👨‍💻 Author
MD Nur Hossain Joy
Data Analyst | Python | SQL | Power BI | Excel
Technical Interests
•	Data Analytics
•	Data Visualization
•	Python
•	SQL
•	Business Intelligence
•	Machine Learning
________________________________________
⭐ If You Find This Project Useful
If you find this project useful or interesting, feel free to:
⭐ Star the repository
🍴 Fork the repository
💬 Share your feedback
🔗 Connect with me on LinkedIn: https://www.linkedin.com/in/md-nur-hossain-joy-0b0bb9190/
