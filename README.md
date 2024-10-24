# Coffee Sales Dashboard Project

## Overview
In this project, I created an interactive Coffee Sales Dashboard in Excel. The dashboard utilizes data from coffee sales to derive insights about sales trends, customer behaviors, and regional performance. It features dynamic visualizations and interactive filters for enhanced data analysis.

## Objectives
- Develop a dashboard displaying:
  - Total sales over time by coffee type.
  - Sales by country.
  - Top 5 customers by sales.
- Implement interactive filters (slicers) for:
  - Date range.
  - Coffee roast type.
  - Package size.
  - Customer loyalty card status.
- Utilize advanced formulas (`XLOOKUP`, `INDEX MATCH`) for data manipulation.

## Steps to Create the Dashboard

### 1. Data Overview
I started by examining the data structure, which consisted of three primary tables:
- **Orders Table**: Containing information about orders, including order ID, order date, customer ID, product ID, and quantity.
- **Customers Table**: Containing customer details like customer ID, name, email, country, and loyalty card status.
- **Products Table**: Containing product details such as product ID, coffee type, roast type, package size, unit price, and profit margin.

The dataset had some missing data in certain columns that required lookup formulas to fetch related details from other tables.

### 2. Data Gathering Using Lookup Functions
To prepare the dataset for analysis, I populated the missing columns by extracting information from the Customers and Products tables.

#### A. Using `XLOOKUP` for Customer Information
I used the `XLOOKUP` function to fetch customer names, email addresses, and countries from the Customers table based on the Customer ID.

Example formula to gather customer names:
```excel
=XLOOKUP(C2, Customers!A:A, Customers!B:B)
```

#### B. Error Handling in Lookup Functions
I added an `IF` condition to handle cases with missing values:
```excel
=IF(XLOOKUP(C2, Customers!A:A, Customers!C:C)=0, "", XLOOKUP(C2, Customers!A:A, Customers!C:C))
```

#### C. Using `INDEX MATCH` for Product Information
I utilized the `INDEX MATCH` formula to retrieve product-related details.

Example for retrieving the coffee type:
```excel
=INDEX(Products!B:B, MATCH(D2, Products!A:A, 0))
```

### 3. Data Visualization
Once I gathered all necessary data, I created the visual elements of the dashboard.

#### A. Line Chart for Total Sales by Coffee Type
I used a line chart to display total sales over time, split by coffee type.

#### B. Bar Chart for Sales by Country
A bar chart was created to show sales performance across three countries: the US, Ireland, and the UK.

#### C. Top 5 Customers Bar Chart
Another bar chart was made to display the top 5 customers based on total sales.

### 4. Interactive Slicers and Timelines
To enhance user interaction, I added slicers to the dashboard, allowing users to filter the data in real-time.

- **Timeline Slicer**: Users can filter data by selecting specific date ranges.
- **Roast Type Slicer**: Filters the data by coffee roast type.
- **Size Slicer**: Filters the data based on the coffee bean package size.
- **Loyalty Card Slicer**: Filters customers based on whether they have a loyalty card.

### 5. Enhancing Dashboard Interactivity
- **Adding Loyalty Card Information**: I added a new "Loyalty Card" column to the dataset using `XLOOKUP`.
- **Pivot Table Duplications**: I copied existing pivot tables to ensure interactivity across visuals.

## Conclusion
This project resulted in a fully interactive Coffee Sales Dashboard built in Excel. By leveraging `XLOOKUP` and `INDEX MATCH` formulas, I efficiently gathered data from multiple tables and created dynamic visualizations. The dashboard provides valuable insights into coffee sales trends, customer behavior, and regional performance, and its interactivity allows for deep data exploration.
