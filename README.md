# Data_Analytics_Research_Project

** by Serhii Spitsyn**

I work at [ATU](https://www.atu.ie/).

![Penguins](https://allisonhorst.github.io/palmerpenguins/reference/figures/lter_penguins.png)

## About the data
Data were collected and made available by [Dr. Kristen
Gorman](https://www.uaf.edu/cfos/people/faculty/detail/kristen-gorman.php)
and the [Palmer Station, AntarcticaLTER](https://pallter.marine.rutgers.edu/), a member of the [Long Term
Ecological Research Network](https://lternet.edu/).


## Goals
- To accurately segment penguins into distinct clusters
- To develop skills in data preprocessing, feature selection, and the application of unsupervised learning techniques
- To establish a versatile clustering pipeline applicable to subsequent projects

## Stack
- API - Python, Flask
- Data - Python, Jupyter Notebook, Pandas
- Streamlit - Python, Pandas
- Other tools - GitHub Projects, GitHub Actions

## Imports
Use pandas for the DataFrame data structure. It allows us to investigate CSV files amongst amongst other features!

## Data preparation
The purpose of this project is to assess the performance of a supervised machine learning classifier in categorizing the three species of Pygoscelis penguins based on their body measurements. Consequently, categorical features that appear to contribute little to the model's effectiveness will be excluded.

## Data modeling
Changing the data type of DataFrames is typically driven by the need for memory efficiency, faster calculations, and suitability for different operations or analytical methods. When making decisions about converting data types, you should consider your specific analysis requirements, the nature of the data in each column, and your overall data processing strategy.

When processing and analyzing data, the type of data stored in each DataFrame column is critical, as it determines what operations can be performed on the data. The decision to change the data type of a column from one type to another is often related to the need to optimize data processing, enable certain features, or align the data with the most appropriate analytical methods. 

Explanation of the reasons for the change in the data type:
- species, island, sex (object):
Convert to Category: These columns are currently of type object, which is a generic type for storing rows in pandas. If these columns contain a limited number of unique rows (as is often the case with categorical data such as species names or gender), it is useful to convert them to a category type. Categories use memory more efficiently and speed up operations such as sorting and grouping. 

- bill_length_mm, bill_depth_mm, flipper_length_mm, body_mass_g (float64):
Handling NULL values: These columns contain floating-point numbers but have missing values (the number of non-zero values is less than 344). Before any type conversion or analytic operations, it is important to eliminate these missing values, either by substituting them (replacing them with an average, median, or calculated value) or by removing rows with missing values, depending on your analysis requirements.

- Data Scaling or Normalization (float64 columns):
While this isn't a type conversion, scaling or normalizing can be critical for certain statistical analyses or machine learning models. This does not change the data type, but the data values are adjusted to the standard scale.

Benefits of Converting to Category
Memory Efficiency: The category dtype stores the data using integers and maintains a separate mapping of categories to integers. This typically uses less memory than strings, especially when the number of unique categories is small relative to the total number of data points.
Performance Improvement: Operations like groupby, sort, and other vectorized operations on categorical data are faster than operations on string data.
Semantic Clarity: Converting to category makes it clear to anyone reading the code that the column contains categorical data, which can only take a limited set of values.

## Bill dimensions Tables
Explore how the mean values vary by each group. The table outputs from this function will assist in gaining a deeper understanding of the penguin dataset.

| Species   | Sex    | Bill Length (mm) | Bill Depth (mm) |
|-----------|--------|:----------------:|:---------------:|
| Adelie    | FEMALE |       37.26       |       17.62      |
| Adelie    | MALE   |       40.39       |       19.07      |
| Chinstrap | FEMALE |       46.57       |       17.59      |
| Chinstrap | MALE   |       51.09       |       19.25      |
| Gentoo    | FEMALE |       45.56       |       14.24      |
| Gentoo    | MALE   |       49.47       |       15.72      |

In the penguin data, the culmen—referred to as the bill—is the upper ridge of a bird's bill. To make the data more intuitive, culmen length and depth are renamed as variables bill_length_mm and bill_depth_mm.
For this data, the bill length and depth are measured as follows:

<img src="https://allisonhorst.github.io/palmerpenguins/reference/figures/culmen_depth.png" style="width: 60%;">


### Discussion of the PivotTable
Overall, Adelie has the lowest Bill Length regardless of gender, and its length is the most varied among the three species. The chin chinstrap has the longest culmen length when compared within each gender. However, it is important to note that the length of the Chinstrap and Gentoo culmen do not differ much from each other.
On the other hand, Gentoo has the lowest Bill Depth regardless of gender, and its depth is the most varied among the three species. Chinstrap and Adelie have very similar culmen depths, so the data does not provide valuable insight into which species has a greater culmen depth.
In general, male Bill is larger in both length and depth.


## Plots


## Resourse reference

[Pandas Category Data Type](https://pbpython.com/pandas_dtypes_cat.html)

[Data cleaning with Pandas](https://www.kdnuggets.com/data-cleaning-with-pandas)

