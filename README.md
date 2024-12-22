# Faasos Roll Data Analysis

This repository contains SQL queries and data analysis related to Faasos roll orders. The analysis includes metrics like customer order patterns, driver efficiency, and roll preferences. The project showcases data cleaning, aggregation, and insights generation using SQL.

## Project Structure

The repository consists of SQL scripts that answer specific business questions, optimize operations, and provide insights. Below is a breakdown of the queries and their purposes:

### Verification Queries
- **Table Data**: View all records from `customer_orders`, `driver_order`, `ingredients`, `driver`, `rolls`, and `rolls_recipes` tables.

### Business Questions Answered

1. **How many rolls were ordered?**
   ```sql
   SELECT count(roll_id) FROM customer_orders;
   ```

2. **How many unique customer orders were made?**
   ```sql
   SELECT count(DISTINCT customer_id) FROM customer_orders;
   ```

3. **How many successful orders were delivered by each driver?**
   ```sql
   SELECT driver_id, count(DISTINCT order_id) FROM driver_order WHERE cancellation NOT IN ('Cancellation', 'Customer Cancellation') GROUP BY driver_id;
   ```

4. **How many of each type of roll were delivered?**
   Cleaned the `driver_order` table for null values and identified successful deliveries.

5. **How many veg and non-veg rolls were ordered by each customer?**
   Performed joins with the `rolls` table to map roll types to customer orders.

6. **Maximum number of rolls delivered in a single order?**
   Used ranking to identify the order with the highest count of rolls.

7. **For each customer, how many delivered rolls had at least one change and how many had no change?**
   Created temporary tables to classify orders into "Change" and "No Change" categories.

8. **How many rolls were delivered with both exclusions and extras?**
   Filtered data to find orders with both customizations.

9. **Total rolls ordered for each hour of the day?**
   Grouped orders by hourly time buckets.

10. **Number of orders for each day of the week?**
    Grouped orders by day of the week.

### Additional Insights

- **Driver and Customer Experience**:
  - Calculated the average time it took for drivers to reach the HQ for order pickup.
  - Explored the relationship between the number of rolls in an order and preparation time.

- **Ingredients Optimization**:
  - Data cleaning ensured accurate insights on ingredient usage and roll preparation.

- **Pricing and Ratings**:
  - Analyzed metrics to guide pricing strategies and understand customer satisfaction.

### Data Cleaning

Performed transformations to:
- Standardize null or empty fields.
- Extract numerical values from string columns like `distance`.
- Use temporary tables and common table expressions (CTEs) for better query readability.

## Technologies Used

- **SQL**: Core language for querying and analyzing data.
- **MySQL**: Database management system used for storing and querying the data.

## Getting Started

1. Clone the repository:
   ```bash
   git clone https://github.com/dhyeyinf/RollMetrics-Data-Insights-for-Orders-andCancellations.git
   ```

2. Import the SQL script into your MySQL environment.

3. Execute the queries in the provided order to replicate the analysis.

## Contributions

Feel free to fork the repository, make changes, and submit a pull request. Suggestions and improvements are welcome!

## License

This project is licensed under the [MIT License](LICENSE).

---

For any queries, contact dhyey.inf323@gmail.com
