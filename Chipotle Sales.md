# Challenge 1: Chipotle Sales

## Scenario

I'm a financial data analyst at Chipotle, and my manager has tasked me with analyzing the most recent sales numbers. In this project, I utilized Python and the Chipotle sales dataset to answer several key questions.

## Analysis

First, I imported the necessary libraries and loaded the dataset using the provided URL:

```python
import pandas as pd

url = 'https://raw.githubusercontent.com/justmarkham/DAT8/master/data/chipotle.tsv'
chipo = pd.read_csv(url, sep='\t')
```

I then examined the structure of the dataset using the `info()` and `head()` methods:

```python
chipo.info()
chipo.head()
```

Next, I answered the questions posed by my manager:

1. **Which was the most-ordered item?**
    ```python
    most_ordered_item = chipo['item_name'].value_counts().idxmax()
    print("The most-ordered item:", most_ordered_item)
    ```

2. **For the most-ordered item, how many items were ordered?**
    ```python
    most_ordered_item_count = chipo['item_name'].value_counts().max()
    print("There are", most_ordered_item_count, "of the popular", most_ordered_item, "that were ordered.")
    ```

3. **What was the most ordered item in the choice_description column?**
    ```python
    most_ordered_item_cd = chipo['choice_description'].value_counts().idxmax()
    print("The most-order item from the choice_description:", most_ordered_item_cd)
    ```

4. **How many items were ordered in total?**
    ```python
    total_items_ordered = chipo['quantity'].sum()
    print("The total items ordered is", total_items_ordered)
    ```

5. **Turn the item price into a float**
    ```python
    chipo['item_price'] = chipo['item_price'].replace('[\$]','',regex=True).astype(float)
    ```

6. **How much was the revenue for the period in the dataset?**
    ```python
    total_revenue = round(sum(chipo['quantity']*chipo['item_price']), 2)
    print("The total revenue for the period was", total_revenue)
    ```

7. **How many orders were made in the period?**
    ```python
    total_order = chipo['order_id'].nunique()
    print("The total amount of orders made in the period is", total_order)
    ```

8. **What is the average revenue amount per order?**
    ```python
    average_revenue = round(total_revenue/total_order, 2)
    print("The average revenue amount per order is", average_revenue)
    ```

9. **How many different items are sold?**
    ```python
    num_different_items = chipo['item_name'].nunique()
    print("There were", num_different_items, "different items sold")
    ```

## Key Insights and Findings

Based on my analysis of the Chipotle sales dataset, here are the key insights and findings:

- The most-ordered item: Chicken Bowl.
- Quantity of the most-ordered item: 726.
- The most-ordered item from the choice description: Diet Coke.
- Total items ordered: 4972.
- Total revenue for the period: $39,237.02.
- Total number of orders made in the period: 1834.
- Average revenue amount per order:
