# Panel-Data-using-Python
Python notebooks and synthetic datasets created for a workshop on panel data regression, covering concepts like fixed effects, first differences, Demeaning, LSDV estimation and Random Effects

Unlocking Insights with Panel Data

From Basic Concepts to Modeling Essentials

Welcome to this interactive guide on Panel Data! Panel data, also known as longitudinal data, is a powerful tool in research and analysis. It allows us to observe the same individuals or entities over multiple time periods, offering richer insights than data collected at a single point in time or for a single entity over time. This guide will walk you through the foundational concepts, advantages, and basic modeling ideas related to panel data.
Setting the Stage: Basic Data Types

Before we dive into panel data, let's clarify two fundamental data structures:
1. Cross-Sectional Data

This is like taking a **snapshot in time**. You collect data from many different individuals (people, firms, countries) at a single, specific point in time.

Analogy: Taking a single photo of many different people at a party today.

Example: Surveying 100 different students today about their current study habits and grades.
2. Time-Series Data

This is like watching a **movie of one specific thing over time**. You collect data for a single individual or entity across multiple, sequential time periods.

Analogy: Watching a movie of one person's life unfolding over several years.

Example: Tracking the grades of one specific student over their four years in high school.
What is Panel Data? Combining Dimensions

Panel Data (also known as **Longitudinal Data**) powerfully combines these dimensions. It tracks the **SAME individuals** (or firms, countries, etc.) across **multiple time periods**.

Analogy: Imagine taking a series of photos of the same group of people every year for several years. You get to see both who they are at different points (cross-section) and how each of them changes over time (time-series).

Many Units (Cross-Section) + Multiple Times (Time-Series) = Panel Data Set
Core Concepts of Panel Data

To effectively work with panel data, it's essential to understand its specific terminology and key distinctions from other data structures.
Understanding Panel Data Notation

Researchers use a standard notation to describe variables in a panel dataset:

    Yit: Represents the **Dependent Variable** (the outcome you're studying) for individual unit 'i' at time period 't'.
    Example: The annual income (Y) of person 'i' in year 't'.
    Xit: Represents an **Independent (or Exogenous) Variable** (a factor you believe influences the outcome) for individual unit 'i' at time period 't'. A model usually includes multiple X variables (e.g., X1it, X2it).
    Example: The years of education (X) of person 'i' in year 't'.
    i = 1, ..., N: Denotes the **Cross-Sectional Unit**. 'N' is the total number of distinct individuals or entities in your panel.
    Example: If you are studying 500 individuals, N = 500.
    t = 1, ..., T: Denotes the **Time Unit**. 'T' is the total number of time periods for which you have observations.
    Example: If you have data for 10 years, t = 10.

Panel Data vs. Pooled Data: A Key Distinction

While the terms might sometimes be used loosely, there's a critical difference that impacts the type of analysis you can perform:
Panel Data Set ✔️

The individuals, firms, countries, etc., for which data is collected across the cross-section and time series are the SAME.

Example: Surveying the exact same 100 families every year for five years.
Pooled Data Set ⚠️

The individuals, firms, countries, etc., for which data is collected across the cross-section and time series may be DIFFERENT in each time period (e.g., new random samples are drawn).

Example: Surveying a new random sample of 100 families each year for five years.

The ability to track the *same* entities over time is what gives panel data its unique analytical power.
Why is Panel Data So Powerful? The Advantages

Panel data isn't just a mix of cross-sectional and time-series data; it offers unique analytical strengths that neither can provide alone.
1. Controlling Individual Unobserved Heterogeneity

Panel data helps in controlling for unobserved heterogeneity – those unique, often unmeasurable, characteristics of individuals (like innate talent, a specific company's management style, or a country's unique cultural factors) that are relatively stable over time but can affect outcomes. By observing the *same* individual or entity over time, we can better isolate the impact of variables that *do* change, as these constant "hidden traits" are implicitly accounted for.

Analogy: If a student's "natural intelligence" is constant, we can better isolate the impact of *changes* in their study habits on *changes* in their grades by looking at their own progress over time.
2. More Informative Data & Enhanced Analytical Power

Panel data provide a richer dataset, leading to several analytical benefits:

    More informative data: We get a more complete story for each individual/entity.
    More variability: Observing changes over time *and* differences across individuals provides a wider range of data points, which is good for statistical analysis.
    Less collinearity among variables: It's often easier to separate the individual effects of explanatory variables that might appear highly correlated in a single cross-section.
    More degrees of freedom: Generally, more data points ($N \times T$) lead to more reliable and robust statistical results.
    More efficiency: Statistical estimates (like the impact of a policy) are often more precise.

3. Studying the Dynamics of Change

This is a key strength! By studying the repeated observations of the same entities, Panel Data Analysis is exceptionally well-suited to study the dynamics of change – how and why things evolve over time.

Analogy: Panel data is like having a **movie** of many individuals, allowing you to see their individual stories unfold, rather than just a single **photograph** (cross-section) or a movie of only one person (time-series).

This allows researchers to more confidently identify cause-and-effect relationships by observing what happens to the same entities before and after certain events, interventions, or policy changes.
Visualizing Panel Data: An Illustration

Let's imagine a small panel dataset: We track the R&D Spending (in $ Thousands) for 3 distinct tech startups (Alpha, Beta, Gamma) over 3 years (2021, 2022, 2023).
Startup 	Year 	R&D Spending ($K)
Alpha Tech	2021	50
Alpha Tech	2022	65
Alpha Tech	2023	60
Beta Solutions	2021	40
Beta Solutions	2022	45
Beta Solutions	2023	55
Gamma Innovations	2021	70
Gamma Innovations	2022	75
Gamma Innovations	2023	80

From this panel, we can analyze the data from different perspectives:
Time-Series View: Alpha Tech's R&D
Cross-Sectional View: R&D in 2022
The "Why" Behind Data: Data Generating Process (DGP)

To choose the right analytical methods, it's helpful to think about how your data came to be. This involves understanding the Data Generating Process (DGP).
What is the Data Generating Process (DGP)?

The DGP refers to the **true, underlying real-world phenomenon or system that is creating the data** we observe. The statistical models we build are our (often simplified and imperfect) attempts to describe and emulate this complex phenomenon.
Why is understanding the DGP important?

    It helps in appreciating and understanding the nature and characteristics of the data we have.
    It guides us in making a proper model that attempts to reflect the underlying reality hidden behind the data.
    It assists in making appropriate and justifiable assumptions about the model we choose to use.

Nature of DGP for Different Data Types
Cross-Sectional Data DGP:

The data is typically considered a result of a random and independent sampling process from a population at a single point in time.
Time-Series Data DGP:

The data is seen as one "realization" of a stochastic process – a sequence of observations evolving, often with some randomness, over time. The order of observations matters.
Panel Data DGP: ✔️

This is a combination: It typically involves an initial random and independent sampling of cross-sectional units, and then each of these units is observed over time, with their sequence of observations being a realization of a stochastic process.
Modeling Panel Data

Panel data allows for the development of sophisticated statistical models to understand complex relationships.
The Basic Panel Data Regression Model

A general way to represent a relationship in a panel data context using a linear regression model is (hover over terms for details):

Yit = β0it + β1itX1it + β2itX2it + ... + βkitXkit + εit

One of the biggest challenges in estimating such a general model is the potentially very large number of parameters (all the β's) to estimate if they are allowed to vary for every individual 'i' and every time 't'. This can lead to a significant loss of degrees of freedom. Therefore, specific panel data models (like Fixed Effects or Random Effects) make simplifying assumptions about these parameters.
Types of Panel Datasets

Panel datasets can be characterized based on their structure, which can influence the choice of analytical methods.
Balanced vs. Unbalanced Panels
Balanced Panel: Each cross-sectional unit (e.g., person, firm) has the same number of time-series observations. The data forms a complete, rectangular structure.
Unbalanced Panel: Cross-sectional units have different numbers of time-series observations. This is common in real-world data due to factors like individuals entering or leaving a study (attrition) or new firms being established.
Simple Illustration:
Person A: Y1, Y2, Y3
Person B: Y1, Y2, Y3
Person X: Y1, Y2, Y3
Person Y: Y1, Y2 (Missing Y3)

Balanced Example

Unbalanced Example
Short vs. Long Panels
Short Panel: The number of individuals or units (N) is typically **very large**, while the number of time periods (t) is **small**.
Example: A survey of thousands of households (large N) for 2-3 years (small t).
Focus: Often leverages variation *across individuals*.
Long Panel: The number of individuals or units (N) is **small**, while the number of time periods (t) is **very large**.
Example: Economic data for 5-10 countries (small N) over 50+ years (large t).
Focus: Often leverages variation *over time* for each individual.
📘 Notebook 1: Understanding Data Types in Python

This notebook introduces three fundamental data types used in panel data analysis:

    Cross-Sectional Data
    Time-Series Data
    Panel Data

We use a synthetic dataset containing financial data of five Indian firms from 2015 to 2023. The dataset includes revenue, R&D spend, employee count, and profit.
🔹 Step 1: Load and Inspect the Dataset


# Import necessary libraries
import pandas as pd  # Imports the pandas library and assigns it the alias 'pd' for data manipulation and analysis.
import matplotlib.pyplot as plt # Imports the pyplot module from the matplotlib library for visualisations.

# Load the dataset
df = pd.read_csv("synthetic_indian_firms_panel_data.csv") # Reads data from the specified CSV file into a pandas DataFrame called 'df'.

# Convert important columns to numeric to avoid type issues during plotting
df['Revenue_Cr'] = pd.to_numeric(df['Revenue_Cr'], errors='coerce') # Converts the 'Revenue_Cr' column to a numeric
df['RD_Spend_Cr'] = pd.to_numeric(df['RD_Spend_Cr'], errors='coerce') # Converts the 'RD_Spend_Cr' column to a numeric
df['Employees'] = pd.to_numeric(df['Employees'], errors='coerce') # Converts the 'Employees' column to a numeric
df['Profit_Cr'] = pd.to_numeric(df['Profit_Cr'], errors='coerce') # Converts the 'Profit_Cr' column to a numeric

# Display first few rows of the dataset
df.head() # Displays the first five rows of the DataFrame 'df' to provide a quick overview of the data.
                    

	Firm 	Year 	Revenue_Cr 	RD_Spend_Cr 	Employees 	Profit_Cr
0 	Tata 	2015 	25795.000000 	1360.000000 	46624 	6355.856746
1 	Tata 	2016 	27035.935025 	1388.167938 	49602 	6661.621632
2 	Tata 	2017 	30175.623068 	1464.404549 	47843 	7435.236962
3 	Tata 	2018 	29997.364272 	1479.214781 	49643 	7391.314211
4 	Tata 	2019 	29989.199169 	1499.711555 	48482 	7389.302339

Note: If the 'synthetic_indian_firms_panel_data.csv' file is not present in the same directory when you run this code locally, you will encounter a FileNotFoundError. The output above assumes the file was loaded successfully.
📊 2. Cross-Sectional Data

A snapshot of revenue for all firms in a single year (2023).


# Filter data for the year 2023
cross_section = df[df['Year'] == 2023] # Creates a new DataFrame 'cross_section' containing 
                                       # only rows where the 'Year' is 2023.

# Plot revenue for each firm as a bar chart
plt.figure(figsize=(8, 5)) # Creates a new figure for the plot with a specified size (8 inches by 5 inches)
plt.bar(cross_section["Firm"], cross_section["Revenue_Cr"], color='steelblue')  # Generates a bar chart with 'Firm' on the x-axis and 'Revenue_Cr' on the y-axis, using a steel blue color.
plt.title("Cross-Sectional Data: Revenue of Firms in 2023")  # Sets the title of the plot.
plt.ylabel("Revenue (₹ Cr)")  # Sets the label for the y-axis.
plt.xlabel("Firm")  # Sets the label for the x-axis.
plt.grid(True)  # Adds a grid to the plot for better readability.
plt.tight_layout()  # Adjusts plot parameters for a tight layout, preventing labels from overlapping.
plt.show() # Displays the generated plot.
                    

Cross-Sectional Data: Revenue of Firms in 2023
📈 3. Time-Series Data

Tata’s revenue over time from 2015 to 2023.


# Filter data for Tata and sort by year
tata_df = df[df['Firm'] == 'Tata'].sort_values("Year") # Creates 'tata_df' by selecting rows where 'Firm' is 'Tata', then sorts these rows by the 'Year' column.

# Extract year and revenue as numeric arrays
years = tata_df["Year"].values.astype(float) # Extracts the 'Year' column from 'tata_df', converts it to a NumPy array, and casts its data type to float.
revenues = tata_df["Revenue_Cr"].values.astype(float) # Extracts the 'Revenue_Cr' column from 'tata_df', converts it to a NumPy array, and casts its data type to float.

# Plot line graph for Tata's revenue trend
plt.figure(figsize=(8, 5)) # Creates a new figure for the plot with a specified size (8 inches by 5 inches)
plt.plot(years, revenues, marker="o", color="green")  # Plots a line graph with 'years' on the x-axis and 'revenues' on the y-axis, using circular markers and green color.
plt.title("Time-Series Data: Tata's Revenue Over Time") # Sets the title of the plot.
plt.xlabel("Year") # Sets the label for the x-axis.
plt.ylabel("Revenue (₹ Cr)") # Sets the label for the y-axis.
plt.grid(True) # Adds a grid to the plot for better readability.
plt.tight_layout() # Adjusts plot parameters to ensure all elements fit neatly within the figure area.
plt.show() # Displays the generated plot.
                    

Time-Series Data: Tata's Revenue Over Time
🧩 4. Panel Data

Revenue trends for all firms from 2015 to 2023.


# Plot each firm's revenue trend on the same graph
plt.figure(figsize=(10, 6)) # Creates a new plot figure with a width of 10 inches and a height of 6 inches.
for firm in df['Firm'].unique(): # Loops through each unique firm name found in the 'Firm' column of the 'df' DataFrame.
    firm_data = df[df['Firm'] == firm].sort_values("Year") # Filters 'df' for data of the current 'firm' and sorts it by 'Year'.
    years = firm_data['Year'].values.astype(float) # Extracts the 'Year' column for the current firm, converts to a NumPy array, and ensures it's float type.
    revenues = firm_data['Revenue_Cr'].values.astype(float) # Extracts 'Revenue_Cr' for the current firm, converts to a NumPy array, and ensures it's float type.
    plt.plot(years, revenues, marker='o', label=firm)  # Plots a line graph for the current firm's revenue over years, with circle markers and a label for the legend.

# Add title, labels, legend, and formatting
plt.title("Panel Data: Revenue Trends of Indian Firms (2015–2023)") # Sets the main title for the plot.
plt.xlabel("Year") # Sets the label for the x-axis.
plt.ylabel("Revenue (₹ Cr)") # Sets the label for the y-axis.
plt.legend(title="Firm") # Displays a legend on the plot, with "Firm" as its title, to identify each firm's line.
plt.grid(True) # Adds a grid to the background of the plot for easier value reading.
plt.tight_layout() # Automatically adjusts subplot parameters to give a tight layout.
plt.show() # Renders and displays the complete plot.
                    

Panel Data: Revenue Trends of Indian Firms (2015–2023)
✅ Summary

Here's a quick comparison of the data types:
Data Type 	Description 	Analogy
Cross-Sectional 	Many firms at one time 	A photo
Time-Series 	One firm over many years 	A movie of one firm
Panel Data 	Many firms over many years 	A movie of multiple firms

Panel data is powerful because it captures both individual variation and time-based change.
📘 Notebook 2: Core Concepts and Notation in Panel Data

This notebook builds on the previous session by introducing:

    Panel data notation
    Difference between Panel Data and Pooled Data
    Why tracking the same entities over time adds analytical power

We'll use the same synthetic dataset of Indian firms from 2015–2023.
🔹 Step 1: Load and Prepare the Dataset


# Import required packages
import pandas as pd

# Load the dataset into a pandas DataFrame
df = pd.read_csv("synthetic_indian_firms_panel_data.csv")  # Dataset contains financial panel data for Indian firms

# Convert necessary columns to numeric format for safety
df['Revenue_Cr'] = pd.to_numeric(df['Revenue_Cr'], errors='coerce')
df['RD_Spend_Cr'] = pd.to_numeric(df['RD_Spend_Cr'], errors='coerce')
df['Employees'] = pd.to_numeric(df['Employees'], errors='coerce')
df['Profit_Cr'] = pd.to_numeric(df['Profit_Cr'], errors='coerce')

# Preview the data
df.head()  # Show first few rows to confirm structure
                    

	Firm 	Year 	Revenue_Cr 	RD_Spend_Cr 	Employees 	Profit_Cr
0 	Tata 	2015 	25795.000000 	1360.000000 	46624 	6355.856746
1 	Tata 	2016 	27035.935025 	1388.167938 	49602 	6661.621632
2 	Tata 	2017 	30175.623068 	1464.404549 	47843 	7435.236962
3 	Tata 	2018 	29997.364272 	1479.214781 	49643 	7391.314211
4 	Tata 	2019 	29989.199169 	1499.711555 	48482 	7389.302339

Note: If the 'synthetic_indian_firms_panel_data.csv' file is not present in the same directory when you run this code locally, you will encounter a FileNotFoundError. The output above assumes the file was loaded successfully.
✏️ Step 2: Panel Data Notation

Panel data uses specific notation to describe observations.

Let’s define the core notation used in panel datasets:

    Yit → Dependent variable (e.g. Revenue_Cr) for firm i in year t
    Xit → Independent variables (e.g. RD_Spend_Cr, Employees) for firm i in year t
    i → Cross-sectional unit (Firm name)
    t → Time unit (Year)

This structure allows us to model not just variation across firms, but also how the same firm changes over time.
🔍 Step 3: Panel vs Pooled Data

In Panel Data, we track the same firms across time.
In Pooled Data, we observe a new sample each year — we lose the ability to track specific changes in entities.
👇 Example:

    Panel: Tata, Infosys, HDFC from 2015 to 2023 — we see how each changes.
    Pooled: A new sample of firms every year — different firms may appear/disappear.

Let’s simulate and compare the structures below.


# 📊 Panel Data View: Same firms (Tata, Infosys) over time

# Filters 'df' for rows where 'Firm' is 'Tata' or 'Infosys', 
# then sorts the result first by 'Firm' and then by 'Year'.
panel_sample = df[df['Firm'].isin(['Tata', 'Infosys'])].sort_values(['Firm', 'Year'])

print("📘 Panel Data Sample (Tata & Infosys over time):") # Prints a descriptive message to the console.
# Displays the 'Firm', 'Year', and 'Revenue_Cr' columns of the 'panel_sample' DataFrame 
# (typically for rich output in environments like Jupyter).
display(panel_sample[['Firm', 'Year', 'Revenue_Cr']])
                    

📘 Panel Data Sample (Tata & Infosys over time):

	Firm 	Year 	Revenue_Cr
9 	Infosys 	2015 	13005.000000
10 	Infosys 	2016 	13518.665546
11 	Infosys 	2017 	14012.022150
12 	Infosys 	2018 	14419.647891
13 	Infosys 	2019 	15791.409085
14 	Infosys 	2020 	16238.490861
15 	Infosys 	2021 	16556.855537
16 	Infosys 	2022 	15294.525635
17 	Infosys 	2023 	18704.187590
0 	Tata 	2015 	25795.000000
1 	Tata 	2016 	27035.935025
2 	Tata 	2017 	30175.623068
3 	Tata 	2018 	29997.364272
4 	Tata 	2019 	29989.199169
5 	Tata 	2020 	37769.472063
6 	Tata 	2021 	28289.112025
7 	Tata 	2022 	33799.338894
8 	Tata 	2023 	34212.852976


# ⚠️ Pooled Data View: Different firms each year, so trends can't be tracked
# This line defines a list of years from which data will be sampled. 
# It's setting up the specific time points for creating the pooled dataset.
years_to_sample = [2015, 2016, 2017]

# This initializes an empty list called 'pooled_rows'. 
# This list will be used to store the sampled DataFrames from each year before they are combined.
pooled_rows = []

# This begins a loop that will iterate through each year specified in the 'years_to_sample' list. 
# For each year, it will perform sampling operations.
for yr in years_to_sample:
    # This line filters the main DataFrame 'df' to get data only for the current year 'yr'. 
    # Then, it randomly samples 2 rows (firms) from that year's data.
    # The 'random_state=yr' ensures that if the code is run again, the same "random" sample 
    # will be chosen for that year, making the results reproducible.
    sample = df[df['Year'] == yr].sample(n=2, random_state=yr)
    # This line appends the 'sample' DataFrame (containing data for 2 firms from the current year 'yr') 
    # to the 'pooled_rows' list.
    pooled_rows.append(sample)

# This line concatenates (combines) all the small DataFrames stored in the 'pooled_rows' 
# list into a single DataFrame called 'pooled_sample'.
# After concatenation, it sorts this new DataFrame first by 'Year' and then by 'Firm' name.
pooled_sample = pd.concat(pooled_rows).sort_values(['Year', 'Firm'])

# This line prints a descriptive message to the console, indicating that the following output 
# is a sample of pooled data.
print("⚠️ Pooled Data Sample (different firms in each year):")

# This line displays selected columns ('Firm', 'Year', 'Revenue_Cr') from the 'pooled_sample' DataFrame.
# The 'display()' function is typically used in environments like Jupyter Notebooks 
# or IPython for a more formatted output of DataFrames.
display(pooled_sample[['Firm', 'Year', 'Revenue_Cr']])
                    

⚠️ Pooled Data Sample (different firms in each year):

	Firm 	Year 	Revenue_Cr
9 	Infosys 	2015 	13005.000000
36 	Wipro 	2015 	26157.000000
10 	Infosys 	2016 	13518.665546
1 	Tata 	2016 	27035.935025
2 	Tata 	2017 	30175.623068
38 	Wipro 	2017 	29164.325913
✅ Summary: Why Panel Structure Matters

    Panel datasets allow you to control for hidden traits of firms (like management quality).
    Panel data helps us understand changes within the same unit over time.
    Pooled data may look like panel data, but does not retain the entity identity across time.

This distinction is crucial for making valid causal inferences in modeling.
📘 Notebook 3: Advantages of Panel Data

This notebook demonstrates the core advantages of using panel data over purely cross-sectional or time-series data. We use the same synthetic dataset of Indian firms.

Key concepts covered:

    Controlling for unobserved heterogeneity
    Gaining more variability and degrees of freedom
    Observing dynamic changes in behavior or outcomes over time

🔹 Step 1: Load and Inspect the Dataset


import pandas as pd
import matplotlib.pyplot as plt

# Load the dataset
df = pd.read_csv("synthetic_indian_firms_panel_data.csv")

# Ensure data types are correct
df['Revenue_Cr'] = pd.to_numeric(df['Revenue_Cr'], errors='coerce')
df['RD_Spend_Cr'] = pd.to_numeric(df['RD_Spend_Cr'], errors='coerce')
df['Employees'] = pd.to_numeric(df['Employees'], errors='coerce')
df['Profit_Cr'] = pd.to_numeric(df['Profit_Cr'], errors='coerce')

# Preview data
df.head()
                    

	Firm 	Year 	Revenue_Cr 	RD_Spend_Cr 	Employees 	Profit_Cr
0 	Tata 	2015 	25795.000000 	1360.000000 	46624 	6355.856746
1 	Tata 	2016 	27035.935025 	1388.167938 	49602 	6661.621632
2 	Tata 	2017 	30175.623068 	1464.404549 	47843 	7435.236962
3 	Tata 	2018 	29997.364272 	1479.214781 	49643 	7391.314211
4 	Tata 	2019 	29989.199169 	1499.711555 	48482 	7389.302339

Note: If the 'synthetic_indian_firms_panel_data.csv' file is not present when you run this code locally, you will encounter a FileNotFoundError. The output above assumes successful loading.
🧠 1. Controlling for Unobserved Heterogeneity

Each firm might have unique, stable characteristics — like management style or brand power — that affect outcomes (e.g., revenue). These are unobserved and firm-specific.

Panel data helps control for these by comparing each firm with itself over time, rather than against others.

Let’s plot firm-wise average revenue vs deviation over time.


# Calculate firm average and deviation from average per year
# Calculate the mean revenue for each firm and broadcast it to all its rows.
df['Firm_Avg_Revenue'] = df.groupby('Firm')['Revenue_Cr'].transform('mean')
# Calculate the difference between annual revenue and the firm's average revenue.
df['Deviation'] = df['Revenue_Cr'] - df['Firm_Avg_Revenue']

# Plot deviation trends to visualize changes over time
plt.figure(figsize=(10, 6)) # Create a new plot figure with a specific size.

# Iterate over each firm and plot deviation from firm average revenue
for firm in df['Firm'].unique(): # Loop through each unique firm.
    firm_data = df[df['Firm'] == firm] # Filter data for the current firm.
    # Extract 'Year' values as a float NumPy array for plotting.
    years = firm_data['Year'].values.astype(float)
    # Extract 'Deviation' values as a float NumPy array for plotting.
    deviations = firm_data['Deviation'].values.astype(float)
    # Plot the deviation trend for the current firm.
    plt.plot(years, deviations, marker='o', label=firm)

# Reference line at zero deviation
plt.axhline(0, color='black', linestyle='--') # Add a horizontal dashed line at y=0.

# Plot formatting
plt.title("Firm-Level Revenue Deviation from Their Own Average") # Set the plot title.
plt.xlabel("Year") # Set the x-axis label.
plt.ylabel("Deviation from Firm Avg Revenue (₹ Cr)") # Set the y-axis label.
plt.legend(title="Firm") # Add a legend with the title "Firm".
plt.grid(True) # Display a grid on the plot.
plt.tight_layout() # Adjust plot to ensure everything fits without overlapping.
plt.show() # Display the plot.
                    

Firm-Level Revenue Deviation from Their Own Average
Understanding Revenue Volatility

The chart clearly shows that firms experience different levels of volatility in their annual revenues compared to their own typical performance.
Reliance (Red) and Wipro (Purple) exhibit the most significant volatility,

with large swings above and below their average revenue. This suggests periods of exceptionally strong performance interspersed with others that might be closer to or even below their norm, or that their growth trajectory was not smooth year on year.
Infosys (Orange) appears relatively more stable, especially from 2019 onwards,

showing a more consistent positive deviation from its average.
Tata (Blue) and HDFC (Green) show moderate volatility.
Performance Relative to Own Average

No firm consistently stays far above or far below its average for the entire period, which is expected since the comparison is against their own multi-year average. However, many firms show periods of sustained performance above their average, particularly in the later years (e.g., Infosys from 2020-2023, Wipro from 2020-2023). This often indicates that revenues in these later years were significantly higher, pulling up their overall average and thus making earlier years appear as negative deviations.
Impact of Specific Years

Early Period (2015-2018 approx.): Many firms (Tata, Reliance, Wipro, and initially Infosys & HDFC) started below or fluctuated around their average. This could imply that these were years of relatively lower revenue compared to the growth seen in subsequent years that shaped their overall average.
2020:

This year stands out as a period of strong positive deviation for Tata, HDFC, and Reliance, all peaking significantly above their averages. Infosys also performed well above its average. This might suggest favorable market conditions for these specific companies/sectors or strong individual performances.
2021:

This was a year of dramatic and mixed results. Wipro (Purple) experienced an exceptionally large positive deviation, hitting the highest peak on the chart. Conversely, Tata's (Blue) revenue dipped below its average. Reliance's deviation decreased from its 2020 peak but remained positive. This highlights that firm-specific factors were highly influential in 2021.
Later Period (2022-2023):

Trends continued to be mixed. Infosys maintained a strong positive deviation. Reliance saw another peak in 2022 before its deviation dropped significantly in 2023, going below its average. Wipro's and Tata's deviations remained positive but were lower than their respective peaks.
Individual Firm Trajectories
Tata (Blue):

Showed recovery from below-average performance in early years to a peak in 2020, followed by a dip and then another recovery to above-average revenues in 2022-2023.
Infosys (Orange):

Demonstrated a steady improvement, consistently performing above its average revenue from 2020 onwards, indicating robust and sustained growth relative to its historical norm.
HDFC (Green):

Generally performed above its average from 2016 to 2020, peaked in 2020, and then showed smaller positive deviations in subsequent years.
Reliance (Red):

Experienced the most dramatic swings, with very high peaks in 2020 and 2022, but also started significantly below average and ended 2023 below average. This indicates periods of very strong revenue growth that significantly outperformed its norm, but also variability.
Wipro (Purple):

After being below average for several initial years, it showed a sharp increase in positive deviation from 2020, culminating in an extremely strong performance in 2021 relative to its average. It remained well above average in 2022-2023.
In summary

The chart reveals that while most firms experienced revenue growth (as indicated by later years often being above their overall average), the path of this growth and its consistency varied significantly. Some firms had smoother upward trends in deviation, while others saw boom-and-bust cycles relative to their own average performance. The years 2020 and 2021 were particularly noteworthy for distinct, and sometimes divergent, firm performances.
📊 2. More Variability & Degrees of Freedom

Panel data combines cross-sectional and time-series variation, increasing the number of useful observations.

Let’s compare:

    Number of rows in cross-section (2023 only)
    Number of rows in full panel (all years)


# Cross-sectional only: one year
# Filter the DataFrame to include only data from the year 2023.
cross_section = df[df['Year'] == 2023]
# Print the number of rows (observations) in the cross-sectional data for 2023.
print("📸 Cross-sectional rows (2023):", len(cross_section))

# Panel: all years
# Print the total number of rows (observations) in the original panel DataFrame.
print("🎥 Panel data rows (all years):", len(df))

# Calculate effective degrees of freedom
# Count the number of unique firms (entities) in the DataFrame.
n_entities = df['Firm'].nunique()
# Count the number of unique years in the DataFrame.
n_years = df['Year'].nunique()
# Print the number of unique entities, unique years, and the total potential observations if the panel were balanced.
print(f"Entities: {n_entities}, Years: {n_years}, Total Observations: {n_entities * n_years}")
                    

📸 Cross-sectional rows (2023): 5
🎥 Panel data rows (all years): 45
Entities: 5, Years: 9, Total Observations: 45

🔁 3. Studying the Dynamics of Change

Let’s analyze how R&D spending over time correlates with revenue. This reveals dynamics that are not visible in static cross-sectional views.


# Create a new plot figure with a specified size (10 inches wide, 6 inches high).
plt.figure(figsize=(10, 6))

# Loop through each unique firm name present in the 'Firm' column of the DataFrame.
for firm in df['Firm'].unique():
    # Filter the DataFrame to get data only for the current 'firm' being processed in the loop.
    firm_data = df[df['Firm'] == firm]

    # Ensure both variables are clean 1D numeric arrays
    # Extract the 'RD_Spend_Cr' column for the current firm, convert its values to a NumPy array, and ensure the data type is float.
    rd_spend = firm_data['RD_Spend_Cr'].values.astype(float)
    # Extract the 'Revenue_Cr' column for the current firm, convert its values to a NumPy array, and ensure the data type is float.
    revenue = firm_data['Revenue_Cr'].values.astype(float)

    # Plot firm trajectory
    # Plot the R&D spending against revenue for the current firm, using circular markers and labeling the line with the firm's name for the legend.
    plt.plot(rd_spend, revenue, marker='o', label=firm)

# Add titles and formatting
# Set the main title for the plot.
plt.title("R&D Spending vs Revenue Over Time (Firm Trajectories)")
# Set the label for the x-axis.
plt.xlabel("R&D Spend (₹ Cr)")
# Set the label for the y-axis.
plt.ylabel("Revenue (₹ Cr)")
# Add a legend to the plot, with "Firm" as its title, to identify lines for different firms.
plt.legend(title="Firm")
# Add a grid to the background of the plot for better readability.
plt.grid(True)
# Adjust plot parameters to ensure all elements fit neatly within the figure area.
plt.tight_layout()
# Render and display the complete plot.
plt.show()
                    

R&D Spending vs Revenue Over Time (Firm Trajectories)
Axes:

The X-axis shows "R&D Spend (₹ Cr)". As you move to the right, R&D spending increases.
The Y-axis shows "Revenue (₹ Cr)". As you move upwards, revenue increases.
Trajectories: Each colored line with circle markers represents a different firm (identified in the "Firm" legend: Tata, Infosys, HDFC, Reliance, Wipro). The line connects points that represent the firm's R&D spend and revenue, likely for consecutive years (though the year itself is not an axis, the line implies a temporal sequence).
General Observations from the Chart:
Positive Correlation:

For most firms depicted (Tata, Infosys, Reliance, Wipro), there appears to be a general positive relationship between R&D spending and Revenue. As firms invest more in R&D (moving right on the chart), their revenue also tends to increase (moving up on the chart). This is seen by the general bottom-left to top-right direction of their trajectories.
Firm-Specific Paths:

Each firm has its own unique trajectory, indicating different strategies or outcomes regarding their R&D investments and revenue generation over time.

    Reliance (Red): Shows a significant increase in revenue corresponding to increases in R&D spend. It appears to reach some of the highest revenue figures on the chart, often associated with substantial R&D investment. Its path has some noticeable shifts.
    Wipro (Purple): Also demonstrates a strong positive trend, particularly its movement towards higher revenue with increased R&D, placing it in the higher spectrum for both metrics.
    Tata (Blue): Shows a generally upward trend. It operates in a mid to high range for both R&D and revenue compared to all firms shown.
    Infosys (Orange): Operates with generally lower R&D spend compared to Reliance or Wipro. Its revenue also reflects this, though there's a visible positive relationship between its R&D and revenue.
    HDFC (Green): Consistently shows the lowest R&D spend and, correspondingly, is in the lower range of revenue among the firms presented. Its trajectory is more clustered in the lower-left area of the plot.

Scale of Operations:

The plot highlights that firms operate at different scales. Reliance and Wipro, for example, are shown with R&D spending exceeding 1400 Cr and revenues reaching above 35000-40000 Cr. HDFC, on the other hand, has R&D spend mostly below 1000 Cr and revenues around 10000-15000 Cr.
"Over Time" Implication:

The lines connecting the dots for each firm suggest a progression. For a firm whose line moves from the bottom-left towards the top-right, it implies that over the years, both its R&D spending and revenue have generally increased. Fluctuations or changes in the slope of the line for a specific firm can indicate varying effectiveness or focus of R&D in generating revenue during different periods.
✅ Summary

Panel data allows us to:

    Control for hidden but stable traits within firms
    Leverage more data and improve estimate efficiency
    Observe how variables change together over time

Next, we'll introduce the basic structure of panel regression models using this foundation.
