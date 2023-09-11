# # Customer Analytics - work 05
 - Voice of Customer Analytics


## Import Dataset

  Data shows messages that were talked about in Social regarding the economy (Economy) in 2021.
  https://storage.googleapis.com/depa_social_data/aggregated/public/economy.csv


## Topic Modeling

![Alt text](https://github.com/KK-PU/K19-MADT8101-CustomerAnalytics/blob/main/V5_VoiceOfCustomerAnalytics/df.jpg)


## Document Clustering

Segment customers by clustering, dividing the data points into subgroups. Then group the same data points into the same group. A popular technique is `K-Means` Clustering.

The features of each clusters are `4 clusters` :

 - `cluster 0` : Starter Group individuals who are in the early stages of their MLM journey. sporadically seek out online shopping opportunities but don't make purchases frequently.
 - `cluster 1` : High Performers The top performers in MLM programs are very responsive to discounts and promotional offers. resulting in more frequent purchases and higher average spending.
 - `cluster 2` : Growing cluster Individuals who fall between the beginner and the high-performing groups. Be price sensitive and only buy when they see a good deal. They are not persuaded by simple marketing or advertising. and tend to have low average spending.
 - `cluster 3` : Potential Growth Maximum number of downline members compared to other clusters Be selective about their buying behavior and have significant spending tendencies when they make purchases. They have a relatively fast return pattern and enjoy the shopping experience at offline stores.

![Alt text](https://github.com/KK-PU/K19-MADT8101-CustomerAnalytics/blob/main/V4_Segment%26Product%26Content/img/cluster2.jpg)

![Alt text](https://github.com/KK-PU/K19-MADT8101-CustomerAnalytics/blob/main/V4_Segment%26Product%26Content/img/cluster.jpg)
