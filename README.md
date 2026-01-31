# 🏆 Hackathon Solution: Food Delivery Data Integration & Analysis
This repository contains the solution for the Hackathon challenge. The core problem was to unify fragmented data from three different formats to answer specific business intelligence questions.

# The Problem Statement
In a real-world scenario, data is often siloed across different systems. This challenge provided:

Transactional Data (orders.csv): High-volume sales records.

User Master Data (users.json): Customer profiles and membership tiers.

Restaurant Master Data (restaurants.sql): Restaurant attributes (Cuisine, Rating, City).

The Task: Merge these datasets using a LEFT JOIN strategy to create a single "Source of Truth" and solve 10 complex analytical questions.

# Technical Solution
The solution was implemented in a Jupyter Notebook using the following logic:

Step 1: Handling Multi-Format Data
CSV & JSON: Loaded using standard Pandas parsers.

SQL: To handle the .sql file, I initialized an in-memory sqlite3 database, executed the script to build the tables, and then queried it back into Pandas.

Step 2: Data Merging (Left Join)
I used the pd.merge() function to join the tables sequentially:

orders → users (Key: user_id)

Combined Data → restaurants (Key: restaurant_id)

Join Type: Left Join (to ensure no order record was excluded even if master data was missing).

# Problem Solutions
Multiple Choice Question Results

1. City with highest Gold revenue: Chennai
2. Cuisine with highest AOV: Mexican
3. Distinct users spending > ₹1000: 2544
4. Highest revenue rating range: 4.6-5.0
5. City with highest Gold AOV: Chennai
6. Cuisine with lowest distinct restaurants: Chinese
7. Percentage of Gold orders: 50%
8. Highest AOV Restaurant (<20 orders): Ruchi Foods Chinese
9. Highest revenue combination: Gold + Italian
10. Highest revenue quarter: Q3 (Jul–Sep)

Numerical Answer Key

Total orders by Gold members: 4987  
Total revenue Hyderabad: 1889367  
Distinct users: 2883  
Average order value Gold: 797.15  
Orders with rating >= 4.5: 3374  
Orders in top Gold city (Chennai): 1337  

Fill-in-the-Blank Answers

The column used to join orders.csv and users.json is user_id.  
The dataset containing cuisine and rating information is stored in SQL (or .sql) format.  
The total number of rows in the final merged dataset is 10,000.  
If a user has no matching record in users.json, the merged values will be NaN (or null).  
The Pandas function used to combine datasets based on a key is pd.merge().  
The column membership in the final dataset originates from the users.json file.  
The join key used to combine orders data with restaurant details is restaurant_id.  
The column that helps identify the type of food served by a restaurant is cuisine.  
If a user places multiple orders, their personal details appear multiple times in the final merged dataset.  

# Conclusion
The problem was solved by building a robust data joinery pipeline. By resolving the conflicts between the CSV, JSON, and SQL formats, I was able to generate the final_food_delivery_dataset.csv, which serves as the definitive source for all required metrics.
