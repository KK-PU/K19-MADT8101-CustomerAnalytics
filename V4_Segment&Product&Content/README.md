# # Customer Analytics - work 04
 - Customer Segmentation
 - Segment Movement Analysis
 - Product Recommendation
 - Content Recommendation


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

 - `cluster 0` : Starter Group individuals who are in the early stages of their MLM journey. sporadically seek out online shopping opportunities but don't make purchases frequently.
 - `cluster 1` : High Performers The top performers in MLM programs are very responsive to discounts and promotional offers. resulting in more frequent purchases and higher average spending.
 - `cluster 2` : Growing cluster Individuals who fall between the beginner and the high-performing groups. Be price sensitive and only buy when they see a good deal. They are not persuaded by simple marketing or advertising. and tend to have low average spending.
 - `cluster 3` : Potential Growth Maximum number of downline members compared to other clusters Be selective about their buying behavior and have significant spending tendencies when they make purchases. They have a relatively fast return pattern and enjoy the shopping experience at offline stores.

![Alt text](https://github.com/KK-PU/K19-MADT8101-CustomerAnalytics/blob/main/V4_Segment%26Product%26Content/img/cluster2.jpg)

![Alt text](https://github.com/KK-PU/K19-MADT8101-CustomerAnalytics/blob/main/V4_Segment%26Product%26Content/img/cluster.jpg)


## Product Recommendation - Market Basket Recommendation

**Google Colab:** [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1BpDBPxs2togvmgEqFrBTVnskpu77FgfS)

**1) Top Most/Least common items**

  - `cluster 0` : Starter Group

    ![Alt text](https://github.com/KK-PU/K19-MADT8101-CustomerAnalytics/blob/main/V4_Segment%26Product%26Content/img/STARTER-1.jpg)

The graph on the left displays the top 10 best-selling products within the `Starter Group`. On the right-hand side, the graph illustrates the relationship between products when customers choose to purchase. Specifically, when customers select the product `"5C4CCE"` there is approximately a ` 2.5% ` chance that they will also purchase `"6CQC41"` together.

  - `cluster 1` : High Performers

    ![Alt text](https://github.com/KK-PU/K19-MADT8101-CustomerAnalytics/blob/main/V4_Segment%26Product%26Content/img/HighPerformers-1.jpg)

The graph on the left illustrates the top 10 best-selling products within the `"High Performers"` group. On the right-hand side, the graph depicts the relationship between products when customers make purchase decisions. Specifically, when customers opt to buy the product `"5C4CCE"` there is an approximate `4%` likelihood that they will also purchase `"6CQC41"` together.

  - `cluster 2` : Growing cluster

    ![Alt text](https://github.com/KK-PU/K19-MADT8101-CustomerAnalytics/blob/main/V4_Segment%26Product%26Content/img/GrowingCluster-1.jpg)

The graph on the left displays the top 10 best-selling products within the `Intermediate group`. On the right-hand side, the graph illustrates the relationship between products when customers choose to make a purchase. Specifically, when customers decide to buy the product `"5C4CCE"` there is an approximate `4.2%` chance that they will also purchase `"6CQC41"` together.

 - `cluster 3` : Potential Growth

    ![Alt text](https://github.com/KK-PU/K19-MADT8101-CustomerAnalytics/blob/main/V4_Segment%26Product%26Content/img/PotentialGrowth-1.jpg)

The graph on the left showcases the top 10 best-selling products within the `Potential Growth` group. On the right-hand side, the graph illustrates the relationship between products when customers opt to make a purchase. Specifically, when customers choose to buy the product `"KCQCEJ"` there is an approximate `5%` chance that they will also purchase `"KCQCER"` together.

**2) Rules and Metrics**







