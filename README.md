# Instacart Basket Analysis

## Problem description

Whether you shop from meticulously planned grocery lists or let whimsy guide your grazing, our unique food rituals define who we are. Instacart, a grocery ordering and delivery app, aims to make it easy to fill your refrigerator and pantry with your personal favorites and staples when you need them. After selecting products through the Instacart app, personal shoppers review your order and do the in-store shopping and delivery for you. We need to use this anonymized data on customer orders over time to predict which previously purchased products will be in a user’s next order.

The data set can be found [https://www.kaggle.com/competitions/instacart-market-basket-analysis/data](https://www.kaggle.com/competitions/instacart-market-basket-analysis/data).

This project can be found at [https://github.com/lihaoranIcefire/erdosFall2022_Thanos_Haoran](https://github.com/lihaoranIcefire/erdosFall2022_Thanos_Haoran)

## Methodology

- Exploratory analysis via seaborn.
- Principal component analysis (PCA) + K-means.
- Extreme gradient boosting (XGBoost) + GridSearchCV.

## Process

1. We merged the data provided by Kaggle Instacart analysis competition. Replaced the non existent values with zeros. On the final data table we performed the exploratory analysis to visualize the top 10 purchased products of our data set. The department distribution of the purchases. The time and the days of the week that the customers buy the most and how many products do they usually order. Finally, we investigated what products were reordered out of the list.
2. We categorize customers based on their shopping habits. We attempted principal component analysis by grouping customers into clusters. We used principal component analysis, which involves selecting the top six components and plotting them against each other before settling on one most significant pair. Based on that, we can divide customers into three distinct clusters using the K-means method. The clusters that we noticed were one more generic user profile, one with baby included (a lot of baby formula purchased) and one customer profile with a lot more fresh produce purchased.
3. The extreme gradient boosting model (XGBoost) is then used to train models that can be evaluated by generating scores on a few prominent features. In our case, the purchase amount of a specific customer and product, as well as its reorder rate, are the most important factors in predicting reordering patterns. We use grid search cross-validation, which is a common practice for adjusting parameters, to find the appropriate parameters for our modeling. We run XGBoost models on each cluster to get a more targeted model, which proved to be more efficient and accurate in predictions.

## Highlights

- The product people by the most is banana.
- Products no one ever bought: `Protein Granola Apple Crisp`, `Unpeeled Apricot Halves in Heavy Syrup`, `Single Barrel Kentucky Straight Bourbon Whiskey`.
- Bananas were the most popular purchase.
- Produce sales are the highest.
- Monday, Tuesday, and 10 a.m. to 4 p.m. are the most lucrative profits.
- 59% of the products have been reordered.
- Clustered models generally behave better then the non clustered model.


## Result

- Top 10 products
  ![](https://github.com/lihaoranIcefire/erdosFall2022_Thanos_Haoran/blob/main/Pictures%20and%20graphs/barchart.png)

- Department distribution
  ![](https://github.com/lihaoranIcefire/erdosFall2022_Thanos_Haoran/blob/main/Pictures%20and%20graphs/piechart.png)

- K-means clustering on the data set described through PCA
  ![](https://github.com/lihaoranIcefire/erdosFall2022_Thanos_Haoran/blob/main/Pictures%20and%20graphs/clustering.png).

- The accuracies and F1 scores of the the non clustered and clustered models are
  | | Non clustered model | Clustered 0 model | Clustered 1 model | Clustered 2 model |
  | ------------- | ------------- | ------------- | ------------- | ------------- |
  | Number of predictions | 6785793 | 580703 | 15809 | 42369 |
  | Accuracy | 86.30% | 79.46% | 90.33% | 87.89% |
  | F1 score | 0.3712 | 0.2816 | 0.2892 | 0.3566 |

- The accuracies of the non clustered and clustered models on the clustered data are
  | Accuracy  | Non clustered model | Clustered 0 model | Clustered 1 model | Clustered 2 model |
  | ------------- | ------------- | ------------- | ------------- | ------------- |
  | Clustered 0 data | 91.23% | 91.32% | | |
  | Clustered 1 data | 94.01% | | 94.05% | |
  | Clustered 2 data | 90.44% | | | 92.51% |

- Some items that we predicted correctly
  * Organic Grade A Free Range Large Brown Eggs,
  * Organic Yellow Onion,
  * Organic Cucumber,
  * Organic Tomato Cluster,
  * Free & Clear Unscented Baby Wipes,
  * ...

- and a few that we have missed
  * Organic Lemon,
  * Organic Red Onion,
  * Organic Sunday Bacon,
  * ...

[Here](https://github.com/lihaoranIcefire/erdosFall2022_Thanos_Haoran/blob/main/Final%20presentation.pdf) are the slides for final presentation.
