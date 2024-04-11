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
- Data - Python, Jupyter Notebook, Pandas, NumPy, SciPy
- Visualization - Matplotlib, mpl_toolkits.mplot3d
- Machine Learning - scikit-learn
- Streamlit - Python, Pandas
- Version Control and CI/CD - GitHub Projects, GitHub Actions

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


### Discussion of the Bill dimensions Table
Overall, Adelie has the lowest Bill Length regardless of gender, and its length is the most varied among the three species. The chin chinstrap has the longest culmen length when compared within each gender. However, it is important to note that the length of the Chinstrap and Gentoo culmen do not differ much from each other.
On the other hand, Gentoo has the lowest Bill Depth regardless of gender, and its depth is the most varied among the three species. Chinstrap and Adelie have very similar culmen depths, so the data does not provide valuable insight into which species has a greater culmen depth.
In general, male Bill is larger in both length and depth.

## Species size Table

This table provides a summary of the average body mass and flipper length measurements for three different species of penguins: Adelie, Chinstrap, and Gentoo. The data presented here is crucial for understanding the physical distinctions among these species, which can be insightful for ecological and biological studies.

| Species   | Body Mass (g) | Flipper Length (mm) |
|-----------|--------------:|--------------------:|
| Adelie    |        3706.2 |               190.1 |
| Chinstrap |        3733.1 |               195.8 |
| Gentoo    |        5092.4 |               217.2 |

### Conclusion of the Species size Table

**Species Size Variation.** Gentoo penguins are significantly larger than both Adelie and Chinstrap penguins in terms of body mass. With an average mass of 5092.4 grams, they are about 36% heavier than Adelie and 36% heavier than Chinstrap penguins.
In terms of flipper length, Gentoos also possess longer flippers, averaging 217.2 mm, which is approximately 14% longer than those of Chinstrap penguins and 14% longer than those of Adelie penguins.
**Adaptations and Habitat.** The larger body mass and longer flipper lengths of Gentoo penguins suggest adaptations to a different or a more demanding environment, possibly involving deeper or more prolonged diving when compared to the Adelie and Chinstrap penguins. Flipper length, in particular, can be correlated with swimming speed and agility, which might indicate Gentoos are better suited to environments requiring these traits.
**Ecological Implications.**
The differences in body mass and flipper length can also be indicators of dietary habits, breeding locations, and overall ecological niches occupied by these species. For instance, larger body size in Gentoos might suggest a higher intake of food or access to richer food sources, which is consistent with their known preference for different types of prey compared to the other two species.
**Conservation and Study.** Understanding these morphological differences can be crucial for conservation efforts. Each species might respond differently to climate change impacts, such as changes in sea ice patterns and fish populations. Monitoring body mass and flipper length over time can provide valuable data on the health and viability of penguin populations.
**Comparative Analysis.** Although Adelie and Chinstrap penguins have similar body masses, the slight difference in their flipper lengths could be significant in terms of their swimming mechanics and thermal regulation capabilities. This suggests subtle but potentially important ecological distinctions between these two closely related species.
This data not only enriches our understanding of the physical and perhaps behavioral distinctions between these species but also underscores the importance of morphological studies in ecological and conservation research.

# Plots

## Body Mass, Grouped by Species and Sex
This bar graph shows the number of individuals by penguin species on three different islands: Biscoe, Dream, and Torgersen. Each penguin species is represented by a separate column color: Adelie (blue), Chinstrap (gray), and Gentoo (green).

<img src="https://github.com/ShamansIT/Data_Analytics_Research_Project/blob/main/species_sex_plot.png?raw=true" style="width: 80%;">

Conclusions that can be drawn from this graph:

**Number of individuals by species.** Adelie penguins are found on all three islands, with the largest population observed on Biscoe Island. Chinstrap penguins are only found on Dream Island. Gentoo penguins are also found on Biscoe Island and in smaller numbers on Dream Island.

**Distribution of species by island.** Biscoe is home to two penguin species, Adelie and Gentoo, with the population of Adelie significantly exceeding Gentoo. Dream Island is inhabited by Adelie and Chinstrap penguins, with the prevalence of Adelie. Torgersen is the only island with only one species, Adelie, and the number of individuals is the smallest.

**Possible environmental impacts.** The distribution of penguins may indicate the different environmental conditions or resources available on each island. For example, the presence or absence of certain species may be related to types of nesting sites, food availability, predators, or anthropogenic impacts.

**Conservation.** This data can be useful for environmental monitoring and conservation of penguins. If the graph reflects changes over time, it can indicate trends in populations that may require conservation measures.

Obviously, more information needs to be taken into account for a complete analysis and conclusions, such as historical data, changes in island ecosystems, and possible changes in penguin populations due to natural or human influences.

## Number of Individuals by Species per Island
<img src="https://github.com/ShamansIT/Data_Analytics_Research_Project/blob/main/species_per_Island_plot.png?raw=true" style="width: 80%;">

## Body Mass per Flipper Size by Species

In this graph, the dots represent individual penguins, and the regression lines show the trend between flipper length and body weight for each species. For example, you can see that penguins of the species Gentoo usually have a higher body mass at a given flipper length compared to the other two species, because their points are concentrated higher on the graph and the regression line has a steeper slope.

The graph also shows that there is a positive linear relationship between flipper length and body weight for all three species: generally, the longer the fin length, the higher the body mass. The length of the flipper seems to be a good indicator of penguin body weight.

<img src="https://github.com/ShamansIT/Data_Analytics_Research_Project/blob/main/body_mass_per_flipper_size.png?raw=true" style="width: 80%;">

Based on the presented scattered graph with regression lines, several conclusions can be drawn:

**Positive relationship between size.** There is a positive correlation between flipper length and body weight for all three penguin species. This means that usually penguins with longer flippers have a higher body mass.

**Differences between species.** Each species has its own unique relationship between flipper length and body weight, which is reflected in the slope of the regression lines. Gentoo penguins, according to this graph, appear heavier at certain flipper lengths compared to Adelie and Chinstrap penguins.

**Potential differentiation of species by morphology.** The regression lines do not intersect, suggesting that these morphological traits (flipper length and body weight) may aid in separating species from one another.

**Scattering of data.** Some species have more dispersion of data around the regression line, which may indicate greater variability in their physical characteristics or possibly the influence of other unaccounted factors.

**Potential use for health determination.** If the length of the flipper is known, a regression line can be used to predict expected body weight, which can be useful for assessing the health and well-being of penguins.

**Exclusion of anomalies.** If there are points that differ significantly from the regression (deviation) line, it is possible that these are anomalies or measurement errors that may need additional consideration.


## Body Mass vs Flipper Length (Polynomial Regression)

The graph you provided shows the polynomial regression between body weight and flipper length in mm. The dots represent individual observations for male (blue) and female (red) individuals, and trend lines (blue and red, respectively) indicate an overall upward or downward trend.

<img src="https://github.com/ShamansIT/Data_Analytics_Research_Project/blob/main/body_mass_per_flipper_length(polynomial_regression).png?raw=true" style="width: 80%;">

Several conclusions can be drawn from the graph:

**Correlation between body weight and flipper length.** There is a positive correlation between body weight and flipper length for both males and females, which means that as body weight increases, so does the length of flippers.

**Difference between the sexes.** There is an obvious difference in the distribution of points between males and females. Males tend to have a higher body mass and longer flippers, indicating sexual dimorphism (differences in size or shape between the sexes).

**Regression trends.** Trend lines show that the increase in flipper length in line with weight gain is not linear, and polynomial regression can better describe the relationship between these variables. Polynomial trend lines can reflect, for example, accelerated growth or decrease in size with increasing mass.

With the help of statistical methods, such as correlation coefficients, it would be possible to give a more accurate estimate of the strength and form of this relationship. From this graph, it can also be deduced that when analyzing the data, it is important to take into account sex differences, since they can influence the relationships between different biological variables.

## Correlation Heatmap

The correlation matrix quantifies the relationship among continuous variables in the dataset, which varies between -1 and 1. Values above zero denote a direct correlation, while values below zero indicate an inverse relationship. A correlation value near 1 or -1 indicates a stronger relationship.

<img src="https://github.com/ShamansIT/Data_Analytics_Research_Project/blob/main/heatmap.png?raw=true" style="width: 60%;">

The correlation matrix quantifies the relationship among continuous variables in the dataset, which varies between -1 and 1. Values above zero denote a direct correlation, while values below zero indicate an inverse relationship. A correlation value near 1 or -1 indicates a stronger relationship.

Culmen Length & Flipper Length (r=0.65): This indicates a relatively strong direct correlation between the length of the bill and the length of the flippers, showing that penguins with longer bills tend to also have longer flippers.

Culmen Length & Body Mass (r=0.59): This relationship is also moderately strong and positive, showing that bigger penguins usually have longer bills.

Flipper Length & Body Mass (r=0.87): This strong positive correlation suggests that the length of the flippers can reliably predict the body mass of the penguin, or the other way around.

Culmen Depth & Body Mass (r=-0.47): A moderate inverse correlation exists here, indicating that penguins with deeper bills tend to weigh less, though this relationship is not as pronounced as that between flipper length and body mass.

Culmen Length & Culmen Depth (r=-0.23): A weak inverse correlation, suggesting a slight but insignificant relationship.

Culmen Depth & Flipper Length (r=0.49): Here, a moderate inverse correlation suggests that deeper bills might be associated with shorter flippers, though other factors might influence this relationship.

To conclude, the length of the flippers demonstrates the strongest correlations with other measurements, especially body mass, making it an essential indicator for predicting the physical attributes of penguins. Conversely, the length and depth of the bill exhibit moderate to weak correlations with other physical characteristics, highlighting their role in identifying different physical traits of penguins.

## Resourse reference

[Pandas Category Data Type](https://pbpython.com/pandas_dtypes_cat.html)

[Data cleaning with Pandas](https://www.kdnuggets.com/data-cleaning-with-pandas)

[Introduction to Regression Analysis](https://www.kellerbiostat.com/introregression/introduction-and-example-datasets#fig:bb-scatter-lspeed-hitdist)

[seaborn.heatmap](https://seaborn.pydata.org/generated/seaborn.heatmap.html)

[Matplotlib plot layout](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.tight_layout.html)

[Colors for Matplotlib](https://blog.finxter.com/how-to-plot-matplotlibs-color-palette-and-choose-your-plot-color/)

[3D wireframe plots for Matplotlib](https://matplotlib.org/stable/gallery/mplot3d/wire3d_zero_stride.html#sphx-glr-gallery-mplot3d-wire3d-zero-stride-py)

