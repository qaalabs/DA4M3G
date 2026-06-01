# Day 2 - BigQuery Solutions

All tables are in `bigquery-public-data.thelook_ecommerce`.

---

## Level 1: Exploration

**Task 1** - How many users?

```sql
SELECT COUNT(*)
FROM `bigquery-public-data.thelook_ecommerce.users`;
```

**Task 2** - How many products?

```sql
SELECT COUNT(*)
FROM `bigquery-public-data.thelook_ecommerce.products`;
```

**Task 3** - First 20 products

```sql
SELECT *
FROM `bigquery-public-data.thelook_ecommerce.products`
LIMIT 20;
```

**Task 4** - Order statuses

```sql
SELECT status, COUNT(*) AS total
FROM `bigquery-public-data.thelook_ecommerce.orders`
GROUP BY status
ORDER BY total DESC;
```

**Task 5** - Users from Germany

```sql
SELECT *
FROM `bigquery-public-data.thelook_ecommerce.users`
WHERE country = 'Germany';
```

---

## Level 2: Filtering and sorting

**Task 6** - Jeans sorted by price

```sql
SELECT *
FROM `bigquery-public-data.thelook_ecommerce.products`
WHERE category = 'Jeans'
ORDER BY retail_price DESC;
```

**Task 7** - Returned orders

```sql
SELECT *
FROM `bigquery-public-data.thelook_ecommerce.orders`
WHERE status = 'Returned';
```

**Task 8** - 10 most expensive products

```sql
SELECT *
FROM `bigquery-public-data.thelook_ecommerce.products`
ORDER BY retail_price DESC
LIMIT 10;
```

**Task 9** - Female users who joined after 2020

```sql
SELECT *
FROM `bigquery-public-data.thelook_ecommerce.users`
WHERE gender = 'F'
  AND created_at > '2020-12-31';
```

**Task 10** - Order items with sale price > 100

```sql
SELECT *
FROM `bigquery-public-data.thelook_ecommerce.order_items`
WHERE sale_price > 100;
```

---

## Level 3: Aggregations

**Task 11** - Orders per user, top 20

```sql
SELECT user_id, COUNT(*) AS order_count
FROM `bigquery-public-data.thelook_ecommerce.orders`
GROUP BY user_id
ORDER BY order_count DESC
LIMIT 20;
```

**Task 12** - Total revenue by product category

```sql
SELECT product_category, ROUND(SUM(sale_price), 2) AS total_revenue
FROM `bigquery-public-data.thelook_ecommerce.order_items`
GROUP BY product_category
ORDER BY total_revenue DESC;
```

**Task 13** - Average sale price per order status

```sql
SELECT status, ROUND(AVG(sale_price), 2) AS avg_sale_price
FROM `bigquery-public-data.thelook_ecommerce.order_items`
GROUP BY status
ORDER BY avg_sale_price DESC;
```

**Task 14** - Country with most users

```sql
SELECT country, COUNT(*) AS user_count
FROM `bigquery-public-data.thelook_ecommerce.users`
GROUP BY country
ORDER BY user_count DESC
LIMIT 1;
```

**Task 15** - Brands with more than 10 products

```sql
SELECT brand, COUNT(*) AS num_products
FROM `bigquery-public-data.thelook_ecommerce.products`
GROUP BY brand
HAVING COUNT(*) > 10
ORDER BY num_products DESC;
```

---

## Level 4: Joins

**Task 16** - Orders with customer name

```sql
SELECT
  o.order_id,
  u.first_name,
  u.last_name,
  o.status,
  o.created_at
FROM `bigquery-public-data.thelook_ecommerce.orders` o
JOIN `bigquery-public-data.thelook_ecommerce.users` u
  ON o.user_id = u.id
LIMIT 20;
```

**Task 17** - Order items with product name and category

```sql
SELECT
  oi.order_id,
  p.name,
  p.category,
  oi.sale_price
FROM `bigquery-public-data.thelook_ecommerce.order_items` oi
JOIN `bigquery-public-data.thelook_ecommerce.products` p
  ON oi.product_id = p.id
LIMIT 20;
```

**Task 18** - Users who have never placed an order

```sql
SELECT
  u.id,
  u.first_name,
  u.last_name
FROM `bigquery-public-data.thelook_ecommerce.users` u
LEFT JOIN `bigquery-public-data.thelook_ecommerce.orders` o
  ON u.id = o.user_id
WHERE o.order_id IS NULL;
```

**Task 19** - Top 10 customers by total spent

```sql
SELECT
  u.first_name,
  u.last_name,
  ROUND(SUM(oi.sale_price), 2) AS total_spent
FROM `bigquery-public-data.thelook_ecommerce.order_items` oi
JOIN `bigquery-public-data.thelook_ecommerce.users` u
  ON oi.user_id = u.id
GROUP BY u.id, u.first_name, u.last_name
ORDER BY total_spent DESC
LIMIT 10;
```

**Task 20** - Orders with customer name, product name, sale price

```sql
SELECT
  o.order_id,
  u.first_name,
  u.last_name,
  p.name AS product,
  p.category,
  oi.sale_price
FROM `bigquery-public-data.thelook_ecommerce.orders` o
JOIN `bigquery-public-data.thelook_ecommerce.users` u
  ON o.user_id = u.id
JOIN `bigquery-public-data.thelook_ecommerce.order_items` oi
  ON o.order_id = oi.order_id
JOIN `bigquery-public-data.thelook_ecommerce.products` p
  ON oi.product_id = p.id
LIMIT 20;
```

---

## Level 5: Stretch

**Task 21** - Most popular product category per country

Uses a CTE and `RANK()` window function to find the top category per country.

```sql
WITH ranked AS (
  SELECT
    u.country,
    p.category,
    COUNT(*) AS items_sold,
    RANK() OVER (PARTITION BY u.country ORDER BY COUNT(*) DESC) AS rnk
  FROM `bigquery-public-data.thelook_ecommerce.order_items` oi
  JOIN `bigquery-public-data.thelook_ecommerce.users` u ON oi.user_id = u.id
  JOIN `bigquery-public-data.thelook_ecommerce.products` p ON oi.product_id = p.id
  GROUP BY u.country, p.category
)
SELECT country, category, items_sold
FROM ranked
WHERE rnk = 1
ORDER BY country;
```

**Task 22** - Percentage of orders returned

`COUNTIF` is a BigQuery-specific function.

```sql
SELECT
  ROUND(100.0 * COUNTIF(status = 'Returned') / COUNT(*), 2) AS pct_returned
FROM `bigquery-public-data.thelook_ecommerce.orders`;
```

**Task 23** - Month-by-month revenue trend

```sql
SELECT
  FORMAT_TIMESTAMP('%Y-%m', created_at) AS month,
  ROUND(SUM(sale_price), 2) AS revenue
FROM `bigquery-public-data.thelook_ecommerce.order_items`
GROUP BY month
ORDER BY month;
```

**Task 24** - Distribution centre with most products

```sql
SELECT
  dc.name,
  COUNT(*) AS num_items
FROM `bigquery-public-data.thelook_ecommerce.inventory_items` ii
JOIN `bigquery-public-data.thelook_ecommerce.distribution_centers` dc
  ON ii.product_distribution_center_id = dc.id
GROUP BY dc.name
ORDER BY num_items DESC;
```

**Task 25** - Create a view of completed orders

The view is created in the course project, not in `bigquery-public-data`. The `thelook` dataset must exist in `ingwane-da4m3` first (create it in the console, location: US).

```sql
CREATE VIEW `ingwane-da4m3.thelook.completed_orders` AS
SELECT
  o.order_id,
  u.first_name,
  u.last_name,
  p.name AS product,
  p.category,
  oi.sale_price,
  o.created_at
FROM `bigquery-public-data.thelook_ecommerce.orders` o
JOIN `bigquery-public-data.thelook_ecommerce.users` u ON o.user_id = u.id
JOIN `bigquery-public-data.thelook_ecommerce.order_items` oi ON o.order_id = oi.order_id
JOIN `bigquery-public-data.thelook_ecommerce.products` p ON oi.product_id = p.id
WHERE o.status = 'Complete';
```
