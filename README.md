# Adventure Work Store 

### Dashboard Link : "https://drive.google.com/file/d/1mZHwODKIz0iRZEp2dOthK2XTv2BSJZim/view?usp=drive_link"
## Problem Statement

This dashboard helps the Adventure Works Bike Store understand their customers better. It helps the store know if their customers are satisfied with their products and services. Through different metrics and ratings, they can identify areas for improvement, thus enhancing their offerings. It also provides insights into return rates, revenue, profit, and order trends, enabling the store to address any issues that might be impacting sales performance.


### Steps followed 

- Step 1 : Load data into Power BI Desktop, dataset is a csv file.
- Step 2 :  Open the Power Query Editor to clean and transform the data.
- Step 3 : Perform data cleaning and transformation.
Check Data Types: Ensure all columns have the correct data types.
Remove Duplicates: Look for and remove duplicate values if any.
Add Columns: Create additional columns for analysis, such as Start of Month, Day, and Year.
- Step 4 :  Load the transformed data back into Power BI.
- Step 5 : Create calculated measures for key metrics.
Details:
Total Profit: Total Profit = SUM(Sales[Profit])

Total Revenue: Total Revenue = SUM(Sales[Revenue])

Total Orders: Total Orders = COUNT(Sales[OrderID])

Additional measures for metrics like Return Rate, Average Delay, etc.
- Step 6 : Create the Executive Summary View
Design the Executive Summary dashboard.

High-Level KPIs: Include visualizations for revenue, orders,return and return rate.
Weekly Revenue Trending Chart: Create a line chart showing weekly revenue trends.
Interactive Elements: Add a zoom slider to focus on specific time periods and a custom filter pane for detailed filtering.
- Step 7 :Enable drill-through functionality.
Details:
Add a drill-through page focused on product details.
Include visuals for monthly orders, revenue, and profit targets.
Set up drill-through options to allow users to navigate from high-level views to detailed product performance. 
- Step 8 : Implement a "What-If" scenario for price adjustments.
Create a parameter for price adjustment.
Use DAX to calculate the impact on total profit based on the price adjustment parameter
- Step 9 : Use field parameters to make charts more interactive.
Create field parameters to allow dynamic switching of chart metrics.
- Step 10 :  Implement mapping and geospatial tools.

Create maps to visualize customer locations and performance.
Drill into performance at the individual customer level
    
  
For creating new column following DAX expression was written;
       
   A Day of Week = 
WEEKDAY(
    'Calendar Lookup'[Date],
    2
),
        
Month Number (SWITCH) = 
SWITCH(
    'Calendar Lookup'[Month Name],
    "January", "1",
    "February", "2",
    "March", "3",
    "April", "4",
    "May", "5",
    "June", "6",
    "July", "7",
    "August", "8",
    "September", "9",
    "October", "10",
    "November", "11",
    "December", "12"
),
        
Month Short = 
UPPER(
    LEFT(
        'Calendar Lookup'[Month Name],
        3
    )
)

       
- Step 11 : Some important measure was created to find total revenue,total profit,total Returns,Total Orders.

Following DAX expression was written for the same,
        
    
Total Revenue = SUMX( 'Sales Data', 'Sales Data'[OrderQuantity] * RELATED( 'Product Lookup'[ProductPrice] ) )


Total Returns = 
COUNT(
    'Returns Data'[ReturnQuantity]
)

Total Profit = 
[Total Revenue] - [Total Cost]

Total Orders = 
DISTINCTCOUNT(
    'Sales Data'[OrderNumber]
)
        
 - Step 12 : New measure was created to find targets and ALso the previous mon,
 
Order Target = 
[Previous Month Orders] * 1.1
 
 Profit Target = 
[Previous Month Profit] * 1.1

Revenue Target = 
[Previous Month Revenue] * 1.1
 


 Previous Month Orders = 
CALCULATE(
    [Total Orders],
    DATEADD(
        'Calendar Lookup'[Date],
        -1,
        MONTH
    )
)
 
 Previous Month Profit = 
CALCULATE(
    [Total Profit],
    DATEADD(
        'Calendar Lookup'[Date],
        -1,
        MONTH
    )
)

Previous Month Revenue = 
CALCULATE(
    [Total Revenue],
    DATEADD(
        'Calendar Lookup'[Date],
        -1,
        MONTH
    )
)

Previous Month Returns = 
CALCULATE(
    [Total Returns],
    DATEADD(
        'Calendar Lookup'[Date],
        -1,
        MONTH
    )
)
 

 
# Insights

The insights derived from the visualizations and reports will aid in making informed decisions to enhance profitability and customer satisfaction.


Snapshots of the PowerBI Dashboard:--

 # Report Snapshot (Power BI DESKTOP)

![Image1](https://github.com/user-attachments/assets/13583c45-3fcb-4248-a1b9-3997c2298dbb)
![image2](https://github.com/user-attachments/assets/42122d3c-7912-43c9-b21a-6a2424f6605b)
![Image3](https://github.com/user-attachments/assets/0abc9538-9495-4b84-ad4d-9b244e37963f)
![Image4](https://github.com/user-attachments/assets/537df18d-7a98-4bf8-af67-62f4fb0ecc75)






           
  
