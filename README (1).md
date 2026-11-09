# MSCS 634 - Lab 6: Association Rule Mining with Apriori and FP-Growth

## Purpose
This lab uses the Apriori and FP-Growth algorithms to find frequent itemsets and association rules in the Online Retail dataset from the UCI Machine Learning Repository. Each invoice is treated as one shopping basket. I cleaned the data, mined frequent itemsets with both algorithms using the same settings, generated rules with support, confidence, and lift, and made Seaborn visualizations to explain the results.

## Settings Used
- Minimum support: ___
- Maximum itemset size: 3
- Minimum confidence: ___
- Baskets used: ___ baskets and the 100 most popular items

## Results

| Measure | Apriori | FP-Growth |
|---|---|---|
| Frequent itemsets found | ___ | ___ |
| Association rules generated | ___ | ___ |
| Running time (seconds) | ___ | ___ |

## Key Insights
- The most frequently bought items are the white hanging heart t-light holder, the jumbo bag red retrospot, and the regency cakestand 3 tier. Many of the top items are home decor and bag products.
- Apriori and FP-Growth found exactly the same frequent itemsets and the same rules, with identical support, confidence, and lift values. They are both exact methods and only differ in how they search.
- The strongest rule is: if a basket has ___, it also has ___ about ___% of the time (lift ___). A lift above 1 means the items are bought together more often than by chance.
- Many of the strongest rules link very similar products, for example different colors or sizes of the same product line. A store could place these items together, bundle them, or recommend one when the other is in the cart.
- ___ was faster on this dataset. FP-Growth usually has a bigger advantage with more items or lower support values, because it avoids generating and testing many candidate itemsets the way Apriori does.

## Challenges and Decisions
- **Data cleaning:** The raw data has over 500,000 rows. I removed rows with missing item names, cancelled invoices, zero or negative quantities and prices, and non-product rows like postage and bank charges. I kept only United Kingdom invoices so the baskets were consistent.
- **Table size:** Using every product made the basket table too large for Colab, so I kept the 100 most frequent items and removed baskets with fewer than 2 items.
- **Session crash:** A very low minimum support made FP-Growth try to count too many itemsets, and the Colab session crashed. I fixed it by raising the minimum support and limiting itemsets to a maximum of 3 items for both algorithms, so the comparison stayed fair.
- **Lost variables:** After the crash, my variables were lost and I got a NameError. I re-ran the cells from the top in order.
- **Choosing thresholds:** I tested a few values for support and confidence and picked ones that gave a useful number of itemsets and rules.

## Files
- `MSCS_634_Lab_6.ipynb` - notebook with all code, plots, and explanations
- `README.md` - this file
