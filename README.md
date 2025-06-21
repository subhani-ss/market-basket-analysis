# 🛒 Uncovering Shopping Patterns: Market Basket Analysis Using the Apriori Algorithm

**Author:** Subhani Shaik  
**Read Time:** 5 minutes  
**Published:** 2 days ago

---

## 🧠 Ever walked into a store for just one thing and somehow walked out with five?

Maybe it was a chocolate bar perfectly placed next to the checkout, or a kitchen gadget you didn’t know you needed until you saw it paired with the blender you were buying...

These aren’t random events. They’re the result of a smart, behind-the-scenes data strategy called **Market Basket Analysis (MBA)** — a technique retailers use to uncover the secret connections between what we buy and why we buy it.

---

## 📚 What is Market Basket Analysis?

When customers buy bread, they often end up buying butter too. This buying pattern can be described with a simple rule:

> IF `{bread}` THEN `{butter}`

In simple terms, **MBA is a data mining technique** used to identify patterns in customer purchasing behaviour — helping businesses group products that are frequently bought together. This insight is used in everything from **recommendation engines** and **product bundling**, to **store layout design** and **marketing strategies**.

---

## 🔍 Association Rule Mining with Apriori

MBA uses association rules — logic-based rules that identify relationships between items. The **Apriori algorithm** is one of the most popular ways to generate these rules.

### 🧮 Key Metrics:

- **Support**: Frequency of items appearing together  
- **Confidence**: Likelihood of item B being bought when item A is bought  
- **Lift**: How much more likely items are bought together compared to being bought independently

For example:  
> IF `{coffee}` THEN `{sugar}`  
> Support = 0.05, Confidence = 0.6, Lift = 2.0

This means that 5% of all transactions include both, 60% of people who buy coffee also buy sugar, and they are 2x more likely to be bought together than by chance.

---

## 🛠️ Implementation Using Python

Here’s a step-by-step guide to apply MBA using the **Apriori algorithm** in Python:

---

### ✅ Step 1: Install Required Libraries

```python
!pip install apyori
import pandas as pd
import matplotlib.pyplot as plt
from collections import Counter
from apyori import apriori
