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

    import pandas as pd
    simple_rules = rules[(rules['antecedents'].apply(len) == 1) & (rules['consequents'].apply(len) == 1) & (rules['lift'] > 1.05) & (rules['confidence'] > 0.5)]
    print(simple_rules.shape)
    simple_rules.sort_values('lift', ascending=False).head(20)


Analyze data from rules (rules) obtained from basket analysis by specifying conditions. Store it in the simple_rules variable and display a table showing only the 20 rules with the highest Lift values (ordered by Lift values from highest to lowest).


 - rules table

    ![Alt text](https://github.com/KK-PU/K19-MADT8101-CustomerAnalytics/blob/main/V4_Segment%26Product%26Content/img/rules%20-1.jpg)

- association rule 

    ![Alt text](https://github.com/KK-PU/K19-MADT8101-CustomerAnalytics/blob/main/V4_Segment%26Product%26Content/img/association-rules-2.jpg)

In the context of Association Rule Mining (or Basket Analysis), nodes represent items, and edges represent rules (what comes before ➞ what comes after). The edges' labels provide information about the lift. It's important to note that for a 1-to-1 item set, both directions of the rule (A➞B, B➞A) have the same lift value. Therefore, in this case, we'll always have bidirectional edges (A⬌B).

**3) Item-item collaborative filtering**

    import networkx as nx
    import matplotlib.pyplot as plt
    
    G = nx.Graph()
    G.add_weighted_edges_from([(x['item1'], x['item2'], round(x['sim'], 2)) for i, x in sim_df.iterrows()])

    labels_params = {'font_family': 'K2D', 'alpha': 0.8, 'font_size': 12}

    edgelist, weights = zip(*[((u, v), d['weight']) for u, v, d in G.edges(data=True)])
    width = 1 + ((np.array(weights) - min(weights)) / (max(weights) - min(weights))) * 3

    plt.figure(figsize=(12, 12))
    pos = nx.circular_layout(G, scale=5)
    nx.draw(G, pos, with_labels=True, node_color='darkturquoise',edgelist=edgelist, 
            width=width,edge_color=weights, edge_cmap=plt.cm.autumn_r,**labels_params)

    num_nodes = G.number_of_nodes()
    num_edges = G.number_of_edges()
    print(f"Number of nodes: {num_nodes}")
    print(f"Number of edges: {num_edges}")

    plt.title('Collaborative Filtering - Item Similarity')
    plt.show()
       


The graph shows the similarity between items by analyzing similarity data between items by circular layout method and using weights on the connecting lines between items to show the similarity between items.

A circular arc representing each item. and use lines between items to show similarities between these items. The weights on the edge show the similarity between the items. The line width can be changed according to the similarity value.




