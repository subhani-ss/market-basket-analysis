# 🛒 Uncovering Shopping Patterns: Market Basket Analysis Using the Apriori Algorithm


## 🧠 Ever walked into a store for just one thing and somehow walked out with five?

Maybe it was a chocolate bar perfectly placed next to the checkout, or a kitchen gadget you didn’t know you needed until you saw it paired with the blender you were buying...

These aren’t random events. They’re the result of a smart, behind-the-scenes data strategy called **Market Basket Analysis (MBA)** — a technique retailers use to uncover the secret connections between what we buy and why we buy it.


![image](https://github.com/user-attachments/assets/22ebe8b9-7c8d-48c4-a598-5326057a3edd)


## 📚 What is Market Basket Analysis?


When customers buy bread, they often end up buying butter too. This buying pattern can be described with a simple rule:


> IF `{bread}` THEN `{butter}`


In simple terms, **MBA is a data mining technique** used to identify patterns in customer purchasing behaviour — helping businesses group products that are frequently bought together. This insight is used in everything from **recommendation engines** and **product bundling**, to **store layout design** and **marketing strategies**.


![image](https://github.com/user-attachments/assets/e771f5ad-de28-4845-8433-3273c266ea52)



## 🔍 Market Basket analysis using Apriori algorithm:

MBA uses association rules — logic-based rules that identify relationships between items. The **Apriori algorithm** is one of the most popular ways to generate these rules.


### 🧮 Key Metrics:


- **Support**: Frequency of items appearing together  
- **Confidence**: Likelihood of item B being bought when item A is bought  
- **Lift**: How much more likely items are bought together compared to being bought independently


To better understand Market Basket Analysis (MBA), imagine a small grocery store where customers purchase everyday items like bread, butter, milk, and tomatoes. In this example, the goal is to determine how often customers who buy bread also purchase butter.


![image](https://github.com/user-attachments/assets/1fba1008-c4c3-40db-9a5c-efeb567ffd53)


1. **Support** — It measures the proportion of transactions in which both bread and butter are purchased together. It is calculated as:
   
![image](https://github.com/user-attachments/assets/d43c2b51-5c50-449d-b032-9faf8e976e24)

This indicates that 60% of all transcation include both bread and butter.


2. **Confidence** — represents the likelihood of purchasing butter given that bread has been purchased.
   
![image](https://github.com/user-attachments/assets/7e6a871e-2e58-4029-9aea-3fa78db24f34)

This implies a 75% probability that customers who buy bread will also purchase butter.


3. **Lift**— assesses the strength of the association between bread and butter, determining how much more likely these items are bought together than would be expected if they were purchased independently.

       Lift< 1, the products are not frequently bought together by consumers.
       Lift> 1, the products are frequently bought together by consumers.
       Lift = 1, the purchase of one product does not affect the purchase of the other.


![image](https://github.com/user-attachments/assets/96e90717-817a-4a0b-bad8-1efd8ce07ced)


A lift of 1.25 means customers who buy Bread are 25% more likely to buy Butter compared to the average. Since Lift > 1, this is a positive association.



Here’s a step-by-step guide to apply MBA using the **Apriori algorithm** in Python:


### Step 1: Install Required Libraries

```python
!pip install apyori
import pandas as pd
import matplotlib.pyplot as plt
from collections import Counter
from apyori import apriori
```


### Step 2: Load Dataset
```python
df = pd.read_csv("dailytransactions.csv")
```


### Step 3: Prepare the Transactions List

```python
transactions = []
for _, row in df.iterrows():
    transaction = [str(item).strip() for item in row if pd.notna(item)]
    if transaction:
        transactions.append(transaction)
```


### Step 4: Apply Apriori Algorithm

```python
results = apriori(transactions, min_support=0.01, min_confidence=0.5, min_lift=1.2))
```


### Step 5: Extract and Format Rules

```python
rule_data = []
for rule in results:
    for stat in rule.ordered_statistics:
        if stat.items_base and stat.items_add:
            rule_data.append({
                'LHS (If bought)': ', '.join(stat.items_base),
                'RHS (Then also bought)': ', '.join(stat.items_add),
                'Support': round(rule.support, 4),
                'Confidence': round(stat.confidence, 2),
                'Lift': round(stat.lift, 2)
            })

df_rules = pd.DataFrame(rule_data)
```


### Step 6: Display Top 10 Rules

```python
top_10_rules = df_rules.sort_values(by='Lift', ascending=False).head(10)
print(top_10_rules.to_string(index=False))
```


### Step 7: Visualize the Rules

```python
plt.figure(figsize=(12, 6))
plt.barh(
    [f"{row['LHS (If bought)']} → {row['RHS (Then also bought)']}" for _, row in top_10_rules.iterrows()],
    top_10_rules['Lift'],
    color='coral'
)
plt.xlabel("Lift")
plt.title("Top 10 Association Rules by Lift")
plt.gca().invert_yaxis()
plt.tight_layout()
plt.show()
```



## Summary

This practical walkthrough demonstrates how Apriori helps uncover hidden patterns in customer purchases. Retailers can use these rules to:

Recommend items (e.g., “Customers who bought bread also bought butter”)
Bundle products for promotions
Organize shelves for convenience and sales optimization
Market Basket Analysis, powered by algorithms like Apriori, transforms raw transaction data into strategic insights — ultimately enhancing the shopping experience and driving revenue growth.

***

I hope you find this article helpful. If I’ve missed anything, let me know in the comment section.

What do you think about this article? Comment!!!

Follow me @ Medium | LinkedIn

Thanks for reading!
























