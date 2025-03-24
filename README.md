# Motorcycle-Parts-Sales-Analysis

## Project Overview

This project focuses on analyzing motorcycle parts sales data to provide insights into wholesale revenue trends across different product lines, months, and warehouses. The company operates three warehouses (North, Central, and West) and sells both retail and wholesale. By filtering for wholesale orders, we calculate net revenue while accounting for payment fees.

### Project Workflow

1. Understanding the Sales Data

- Extracted order details including date, warehouse, product line, and payment method.

- Identified wholesale orders to focus on bulk sales analysis.

2. Calculating Net Revenue

- Used SQL aggregation functions to compute total revenue minus payment fees.

- Grouped revenue by product line, month, and warehouse.

- Converted date values into month names (June, July, August 2021) for better readability.

3. Generating Insights

- Monthly Revenue Trends: Compared net revenue across different months.

- Warehouse Performance: Identified which warehouse generated the highest revenue.

- Product Line Analysis: Determined which product lines contributed most to sales.

### Key SQL Query

```sql
SELECT product_line,
    CASE WHEN EXTRACT(MONTH FROM date) = 6 THEN 'June'
         WHEN EXTRACT(MONTH FROM date) = 7 THEN 'July'
         WHEN EXTRACT(MONTH FROM date) = 8 THEN 'August'
    END as month,
    warehouse,
    SUM(total) - SUM(payment_fee) AS net_revenue
FROM sales
WHERE client_type = 'Wholesale'
GROUP BY product_line, month, warehouse
ORDER BY net_revenue DESC;
```

### Technologies Used

SQL (PostgreSQL/MySQL) – Data querying & revenue analysis

Power BI / Tableau – Visualization of sales trends

Excel – Data validation & preprocessing


### Results & Business Impact

Optimized Sales Strategy: Identified high-performing product lines and warehouses.

Better Financial Insights: Calculated net revenue to track actual earnings.

Informed Decision-Making: Helped the board of directors understand sales trends.

### Contribution

We welcome contributions! If you have suggestions or improvements, feel free to submit a pull request.
