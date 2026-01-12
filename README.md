# Inventory Dashboard (Power BI)

## Overview

This project is a beginner-level Power BI dashboard focused on basic inventory control.
It shows current stock levels, identifies products below minimum stock, and provides a quick overview by product and category.

## Project Objectives

- Monitor current stock per product
- Detect products below minimum stock
- Visualize inventory by category
- Provide quick KPIs for decision making

## Dataset

The dataset contains a single table called Data with the following fields:

<img width="1152" height="510" alt="data table" src="https://github.com/user-attachments/assets/f242014d-8206-4df5-8b92-acbd13380e97" />

The dataset was manually created for learning purposes and includes:

- Multiple categories
- Different suppliers
- Products both above and below minimum stock

## Data Model

Single-table model:

- Inventory

No relationships were required for this beginner project.

## Calculated Columns (DAX)

### Stock Status

Determines whether a product is below the minimum stock:

```DAX
Stock Status = IF(Data[Current Stock]<Data[Minimum Stock],"Below Minimum", "Ok")
```

### Stock Difference

Shows how far a product is from its minimum stock:

```DAX
Stock Difference = Data[Current Stock]-Data[Minimum Stock]
```

## Measures (DAX)

### Total Stock

```DAX
Total Stock = SUM(Data[Current Stock])
```

### Average Stock

```DAX
Average Stock = AVERAGE(Data[Current Stock]) 
```

### Products Below Minimum

```DAX
Products Below Minimum = CALCULATE(COUNT(Data[Product]),Data[Current Stock]<Data[Minimum Stock])
```

## Visualizations

The dashboard includes:

- KPI Cards
- Bar Chart – Stock per Product
- Bar Chart – Stock per Category
- Alert Table – Products Below Minimum

<img width="968" height="543" alt="dashboard view" src="https://github.com/user-attachments/assets/61c0e849-b875-429f-8fd9-c2e696c415aa" />

## Business Logic

- Products below minimum stock are considered critical
- Conditional colors help identify problems instantly
- Alert table simulates a real operational action list

## Future Improvements

Possible next steps:
- Add dates and stock movement history
- Create rotation metrics (stock turnover)
- Add slicers for category and supplier
- Use multiple tables and relationships

## License

This project is for educational and portfolio purposes under the [MIT Licence](https://choosealicense.com/licenses/mit/).
