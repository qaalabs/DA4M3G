# Running Queries in BigQuery

Your trainer will run each query and talk through the results. Follow along in your own editor - run the queries yourself as you go.

!!! warning "Check before you run"
    BigQuery charges based on how much data a query reads. Before you click **Run**, look at the top right of the editor - BigQuery will show you how much data the query will process (for example, "This query will process 1.2 GB when run").

    Always use `LIMIT` when exploring data. A `SELECT *` with no limit on a large table can scan gigabytes unnecessarily.

    For this course, the project has a budget set - but this is a habit worth building now.

---

## Part 1: Exploring the data

How many rows are in each table?

```sql
SELECT COUNT(*) FROM `bigquery-public-data.thelook_ecommerce.users`
```

```sql
SELECT COUNT(*) FROM `bigquery-public-data.thelook_ecommerce.orders`
```

Now preview some actual rows:

```sql
SELECT * FROM `bigquery-public-data.thelook_ecommerce.users` LIMIT 10
```

```sql
SELECT * FROM `bigquery-public-data.thelook_ecommerce.products` LIMIT 10
```

> Notice the backtick syntax - `project.dataset.table`. This is how BigQuery identifies a table.

---

## Part 2: Filtering and sorting

Orders with a specific status:

```sql
SELECT *
FROM `bigquery-public-data.thelook_ecommerce.orders`
WHERE status = 'Shipped'
ORDER BY created_at DESC
LIMIT 20
```

Products in a specific category:

```sql
SELECT name, brand, retail_price
FROM `bigquery-public-data.thelook_ecommerce.products`
WHERE category = 'Jeans'
ORDER BY retail_price DESC
```

> `WHERE` and `ORDER BY` work exactly as they do in SSMS. The SQL is the same - only the table reference has changed.

---

## Part 3: Aggregations

Orders grouped by status:

```sql
SELECT status, COUNT(*) AS total_orders
FROM `bigquery-public-data.thelook_ecommerce.orders`
GROUP BY status
ORDER BY total_orders DESC
```

Average sale price by product category:

```sql
SELECT product_category, ROUND(AVG(sale_price), 2) AS avg_sale_price
FROM `bigquery-public-data.thelook_ecommerce.order_items`
GROUP BY product_category
ORDER BY avg_sale_price DESC
```

Top 10 brands by number of products:

```sql
SELECT brand, COUNT(*) AS num_products
FROM `bigquery-public-data.thelook_ecommerce.products`
GROUP BY brand
ORDER BY num_products DESC
LIMIT 10
```

---

## Part 4: Joining tables

Orders with the customer name added:

```sql
SELECT
  o.order_id,
  u.first_name,
  u.last_name,
  u.country,
  o.status,
  o.created_at
FROM `bigquery-public-data.thelook_ecommerce.orders` o
JOIN `bigquery-public-data.thelook_ecommerce.users` u
  ON o.user_id = u.id
LIMIT 20
```

> The join works just as it does in SSMS - match a key in one table to a key in another. The only difference is the full `project.dataset.table` reference.

---

## What to notice

As you run these queries, think about:

- Does the SQL feel familiar?
- What is different from querying in SSMS?
- What does the result tell you about the data?
