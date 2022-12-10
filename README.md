# Instacart basket analysis

## Problem description

Whether you shop from meticulously planned grocery lists or let whimsy guide your grazing, our unique food rituals define who we are. Instacart, a grocery ordering and delivery app, aims to make it easy to fill your refrigerator and pantry with your personal favorites and staples when you need them. After selecting products through the Instacart app, personal shoppers review your order and do the in-store shopping and delivery for you. We need to use this anonymized data on customer orders over time to predict which previously purchased products will be in a user’s next order.

The data set can be found [here](https://www.kaggle.com/competitions/instacart-market-basket-analysis/data)

## Methodology

- Principal component analysis (PCA) + K-means
- Extreme gradient boosting (XGBoost) + GridSearchCV

## Process

1. We categorize customers based on their shopping habits. We attempted principal component analysis by grouping customers into clusters. We used principal component analysis, which involves selecting the top six components and plotting them against each other before settling on one most significant pair. Based on that, we can divide customers into three distinct clusters using the K-means method. The clusters that we noticed were one more generic user profile, one with baby included (a lot of baby formula purchased) and one customer profile with a lot more fresh produce purchased.
2. The extreme gradient boosting model (XGBoost) is then used to train models that can be evaluated by generating scores on a few prominent features. In our case, the purchase amount of a specific customer and product, as well as its reorder rate, are the most important factors in predicting reordering patterns. We use grid search cross-validation, which is a common practice for adjusting parameters, to find the appropriate parameters for our modeling. We run XGBoost models on each cluster to get a more targeted model, which proved to be more efficient and accurate in predictions.

## Highlights

- The product people by the most is banana
- Products no one ever bought: `Protein Granola Apple Crisp`, `Unpeeled Apricot Halves in Heavy Syrup`, `Single Barrel Kentucky Straight Bourbon Whiskey` 
- b3

## Result

The accuracies are

| Accuracy  | Unclustered model | Clustered 0 model | Clustered 1 model | Clustered 2 model |
| ------------- | ------------- | ------------- | ------------- | ------------- |
| Clustered 0 data | 91.23% | 91.32% | | |
| Clustered 1 data | 94.01% | | 94.05% | |
| Clustered 2 data | 90.44% | | | 92.51 %


Here are some bullet points
- b1
- b2

Insert picture

<picture>
  <img src="https://github.com/lihaoranIcefire/erdosFall2022_Thanos_Haoran/blob/main/xgboost_illustration.png">
</picture>
