# TP7: Northwind Order Details Dashboard

## Objective

This practical work aims to guide you through the process of creating your first interactive dashboard using the Northwind data mart, specifically focusing on the `fct_order_details` fact table and its related dimensions: `dim_customers`, `dim_employees`, `dim_products`, `dim_suppliers`, and `dim_categories`. The goal is to visualize key business metrics and allow for insightful exploration through various charts and filters, all consolidated into a single, cohesive dashboard.

## Running Metabase with Docker Compose

To run Metabase and its PostgreSQL database, navigate to the `TP7` directory in your terminal and execute the following command:

```bash
docker compose up -d
```

This command will start both the Metabase and PostgreSQL services in detached mode. Metabase will be accessible at `http://localhost:8000`.

To stop the services, use:

```bash
docker compose down
```

## Dashboard Requirements

To achieve a comprehensive and user-friendly dashboard, consider incorporating the following elements:

### 1. Key Performance Indicators (KPIs)

*   **Total Revenue:** Display the sum of `extended_price` from `fct_order_details`.
*   **Total Orders:** Count of unique `order_id` from `fct_order_details`.
*   **Average Order Value:** `Total Revenue` / `Total Orders`.
*   **Total Quantity Sold:** Sum of `quantity` from `fct_order_details`.

### 2. Suggested Charts and Visualizations

*   **Sales Trend Over Time:** A line chart showing `Total Revenue` or `Total Orders` by `order_date` (e.g., by month, quarter, or year). This will help identify seasonal patterns or growth trends.
*   **Sales by Product Category:** A bar chart or pie chart displaying `Total Revenue` or `Total Quantity Sold` grouped by `dim_categories.category_name`. This highlights top-performing product categories.
*   **Top N Products by Revenue:** A bar chart showing the top N products (e.g., top 10) based on `extended_price`, linked to `dim_products.product_name`.
*   **Sales by Customer Country/City:** A map or bar chart visualizing `Total Revenue` by `dim_customers.country` or `dim_customers.city`. This helps understand geographical sales distribution.
*   **Employee Performance:** A bar chart showing `Total Revenue` or `Total Orders` attributed to `dim_employees.employee_full_name`. This can help identify high-performing employees.
*   **Shipping Performance:** A scatter plot or bar chart showing `shipping_delay_days` from `fct_order_details` against `order_date` or grouped by `dim_employees.employee_full_name` or `dim_customers.country`.

### 3. Interactive Filters

To enable dynamic analysis and drill-down capabilities, include the following filters:

*   **Date Range Filter:** Allow users to select a specific `order_date` range (e.g., start date and end date).
*   **Product Category Filter:** A dropdown or multi-select filter for `dim_categories.category_name`.
*   **Customer Country Filter:** A dropdown or multi-select filter for `dim_customers.country`.
*   **Employee Filter:** A dropdown or multi-select filter for `dim_employees.employee_full_name`.
*   **Product Name Filter:** A search box or dropdown for `dim_products.product_name`.

### 4. Dashboard Layout

Organize all charts, KPIs, and filters on a single dashboard page for a cohesive user experience. Consider a layout that prioritizes key information and allows for logical flow when exploring the data.

## Data Source

The data for this dashboard will be sourced from the `northwind_warehouse` schema in your Supabase PostgreSQL database, which was populated and transformed in TP6 using `dlt` and `dbt`. The core tables to be utilized are:

*   **Fact Table:** `fct_order_details`
*   **Dimension Tables:** `dim_customers`, `dim_employees`, `dim_products`, `dim_suppliers`, `dim_categories`

## Conclusion

By successfully creating this dashboard, you will demonstrate your ability to leverage a structured data mart for business intelligence, providing valuable insights into Northwind's order details through interactive visualizations and filters.

