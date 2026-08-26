# Exploring the TheLook Ecommerce Dataset

You are going to find and explore a public dataset in BigQuery. The dataset is a simulated ecommerce store - it has orders, products, customers, and more.

## Step 1: Find the dataset

In the BigQuery console, look at the **Explorer** panel on the left.

At the top of the Explorer panel, click the search icon and type:

```
thelook_ecommerce
```

In the results, you should see **thelook_ecommerce** under `bigquery-public-data`. Click the star icon next to it to pin it so it stays in your Explorer panel.

If you do not see a search icon, click **+ ADD DATA** at the top of the Explorer panel, choose **Pin a project**, and type:

```
bigquery-public-data
```

Then expand **bigquery-public-data** in the Explorer panel and scroll down to find **thelook_ecommerce**.

## Step 2: Understand the structure

BigQuery organises everything in three levels:

| Level | What it is | SSMS equivalent |
|-------|-----------|-----------------|
| **Project** | The top-level container - like a workspace or billing account | Server |
| **Dataset** | A collection of related tables | Database |
| **Table** | Rows and columns of data | Table |

In the Explorer panel you can see this hierarchy:
`ingwane-da4m3` > `thelook_ecommerce` > `orders`

That is: project > dataset > table. You will use this three-part path when writing queries.

## Step 3: Explore the tables

Expand the **thelook_ecommerce** dataset. You will see several tables:

| Table                  | What it contains |
|------------------------|------------------|
| `orders`               | One row per order - date, status, customer |
| `order_items`          | One row per item within an order |
| `products`             | The product catalogue - name, category, price |
| `users`                | Customer records |
| `inventory_items`      | Stock records |
| `events`               | Website activity - clicks, page views |
| `distribution_centers` | Warehouse locations |

## Step 4: Look at a table

Click on the **orders** table. You will see three tabs:

- **Schema** - the columns and their data types
- **Details** - row count, size, when it was last updated
- **Preview** - a sample of the actual data

Work through each tab for **orders**, then do the same for **order_items** and **products**.

## Step 5: Questions to think about

As you explore, consider:

- What does one row in `orders` represent?
- What does one row in `order_items` represent?
- How do you think `orders` and `order_items` are connected?
- What columns look useful for analysis?

## Step 6: What else is in BigQuery public data?

If you pinned `bigquery-public-data`, scroll through the list in the Explorer panel - there are hundreds of datasets. You do not need to open them, but notice the range:

- `chicago_crime` - crime reports from Chicago
- `covid19_open_data` - global COVID-19 records
- `london_bicycles` - London cycle hire trips
- `noaa_gsod` - global weather station readings
- `wikipedia` - Wikipedia page view data

This is one of the things that makes BigQuery different from a local database - large, real-world datasets are available to query immediately, with no setup.

## Step 7: Open the query editor

Click on the **orders** table, then click **Query** at the top of the table panel (or click the three dots next to the table and choose **Query**).

A SQL editor will open in the main panel. BigQuery will pre-fill the table name for you.

You do not need to run anything yet - just notice that the editor is there, it looks familiar, and the table reference is already in place. That is where you will work next.
