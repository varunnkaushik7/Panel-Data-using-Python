# **📊 Panel Data Analysis in Python — 3-Day Workshop**

Welcome to the repository for the 3-Day Workshop on Panel Data Analysis using Python. The workshop was designed for students, researchers, and analysts who are new to panel data techniques and want to leverage Python for robust empirical analysis.

## **🎯 Objective**
This workshop walks through the theory and hands-on implementation of panel data models using Python. From exploratory data analysis (EDA) to the implementation of Fixed Effects and Random Effects models, the sessions build up your understanding in a structured, intuitive manner.

## **🗓️ Day 1: Getting Started with Panel Data**

On Day 1, we laid the foundation with a gentle introduction to Python and the panel data structure, along with exploratory data analysis techniques.

### ✅ Topics Covered:

**📘 Notebook 1.ipynb**: 
    Data Types & Python Basics - Introduction to variables, data types, and pandas data structures
  
**📘 Notebook 2.ipynb**: 
    Panel Data Structure & Notation - Understanding cross-sectional vs. time-series vs. panel data - Explanation of key notations used in panel regression
  
**📘 Notebook 3.ipynb**: 
    Why Use Panel Data? - Advantages of panel data over pure cross-sectional or time-series data - Real-world examples and model motivation
  
**📘 Notebook on EDA.ipynb**: 
    EDA on Panel Dataset - Data loading, summary statistics, grouping by entities/time - Initial visualization and trends

## **🗓️ Day 2 & Day 3: Panel Data Modeling in Action**

The second and third days of the workshop focused on implementing various panel data models and applying them to real-world datasets. Participants explored estimation techniques, fixed and random effects, and how to choose between them.

### Topics Covered:

**📘 OLS_Basics.ipynb** - Revisiting Ordinary Least Squares (OLS) with cross-sectional data - Establishing the baseline for panel estimators
    
**📘 Day2_Pooled_FD_FE_LSDV_BE.ipynb** - Overview and comparison of key panel data estimators:Pooled OLS, First Differences (FD), Fixed Effects via Within Transformation, Least Squares Dummy Variable (LSDV), Between Estimator (BE) - Use of synthetic firm-level financial data to demonstrate models
    
**📘 Random_Effect.ipynb** - Introduction to Random Effects (RE) models - Use of linearmodels package and comparison with FE - Hausman test to decide between FE and RE

**📘 Sports_Team_Performance.ipynb** - Balanced panel case study - Performance analysis of sports teams over time using FE models
    
**📘 Environment.ipynb** - Unbalanced panel case study - Regional-level environmental indicators and their relation to policy variables
    
**📘 Health_Expenditure.ipynb** - Fixed and random effects applied to health spending data - Controlling for region and year heterogeneity
    
**📘 Dynamic_Economic_Growth.ipynb** - Introduction to Dynamic Panel Models (GMM) - Application to GDP growth using lagged variables
