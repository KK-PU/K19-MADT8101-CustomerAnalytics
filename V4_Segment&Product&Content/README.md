# # Customer Analytics - work 04
 - Customer Segmentation
 - Segment Movement Analysis
 - Product Recommendation
 - Content Recommendation

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1BpDBPxs2togvmgEqFrBTVnskpu77FgfS)

## Customer Segmentation

**1) Data overview**

HDI is a Social Network Marketing organisation that offers a wide range of premium bee-based nutritional and skin care products as well as a unique opportunity to learn about entrepreneurship. The Company has 200,000 more Enterprisers with 6 representative offices in America, Singapore, Malaysia, Indonesia , Hong Kong and the Philippines.

**2) Import Dataset**

The data consists of the past 3 years of customer transactions, which includes the following relevant information:
- ent
- original status
- join month
- join year
- sponsor
  
Data is compiled in csv file format.

**3) K-Means Clustering**

Segment customers by clustering, dividing the data points into subgroups. Then group the same data points into the same group. A popular technique is `K-Means` Clustering.

The features of each clusters are `4 clusters` :

 - cluster 0 : Starter Group individuals who are in the early stages of their MLM journey.
 - cluster 1 : High Performers the top-performing individuals in the MLM program.
 - cluster 2 : Growing Cluster individuals who fall between the Starter Group and the High Performers.
 - cluster 3 : Potential Growth highest number of downline members compared to other clusters.


