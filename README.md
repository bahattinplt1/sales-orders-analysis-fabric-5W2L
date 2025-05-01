# Sales Orders Analysis with Microsoft Fabric & Apache Spark

This project demonstrates a full data analysis workflow using **Microsoft Fabric**, **Apache Spark**, and **PySpark**. It includes ingesting CSV data, transforming it using DataFrame operations, querying with Spark SQL, and visualizing results with both built-in Fabric charts and Python libraries like matplotlib and seaborn.

## 🔧 Technologies
- Microsoft Fabric (Lakehouse, Notebooks)
- Apache Spark (PySpark)
- Spark SQL
- matplotlib, seaborn (for visualizations)

## 📁 Dataset
Sales order data for 2019–2021 in CSV format.

Source:  
[orders.zip](https://github.com/MicrosoftLearning/dp-data/raw/main/orders.zip)

Files included:
- `2019.csv`
- `2020.csv`
- `2021.csv`

## 📌 Key Steps

1. **Create Workspace and Lakehouse** in Microsoft Fabric
2. **Upload CSV files** to Lakehouse (in `/orders` folder)
3. **Create and configure a Notebook**
4. **Load data using PySpark** and define schema
5. **Explore data**: filtering, grouping, and aggregations
6. **Transform data**: add `Year`, `Month`, `FirstName`, `LastName`
7. **Save as table** using Delta format (`salesorders`)
8. **Query with Spark SQL** (e.g., yearly revenue, item counts)
9. **Visualize data**:
   - Built-in Fabric bar charts
   - `matplotlib` bar and line plots
   - `seaborn` styled visualizations

## 🧪 Example SQL Query

```sql
%%sql
SELECT YEAR(OrderDate) AS OrderYear,
       SUM((UnitPrice * Quantity) + Tax) AS GrossRevenue
FROM salesorders
GROUP BY YEAR(OrderDate)
ORDER BY OrderYear;
