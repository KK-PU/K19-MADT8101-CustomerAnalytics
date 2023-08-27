# # Customer Analytics - work 03
 - Customer Scoring
 - Churn Scoring
 - Campaign Response Scoring

**Customer travel Churn Prediction**
Introduction: 

Take the data set that is included in the lesson and add it to the code section to provide a variety of viewable information.

**About Dataset**
This dataset is for Customertravel.csv with following columns:
 - Age
 - Frequent Flyer : (No , Yes , No Record)
 - Annual Income Class : (High Income , Low Income , Middle Income)
 - Services Opted : (0-6)
 - Account Synced To Social Media	: (No , Yes)
 - Booked Hotel Or Not : (No , Yes)
 - Target : (0-1)


## Load dataset and libraries required

    import pandas as pd
    import matplotlib.pyplot as plt
    import seaborn as sns
    sns.set()

**Explore Services Opted by Target**

![Alt text](https://github.com/KK-PU/K19-MADT8101-CustomerAnalytics/blob/main/V3_Customer%26Churn%26Campaign/img/Distributionof%20ServicesOptedbyTarget.jpg)

Displays graphs that classify ServicesOpted is issued according to Target (0 , 1), showing the number on the y-axis and the type on the x-axis, showing the relationship between ServicesOpted and Target results can be obtained from this graph.

**Average ServicesOpted by Target**
Group the data by "Target" and calculate the average of ServicesOpted and store the result in a variable avg_services_by_target.

 **Group the data**
 
    avg_services_by_target = df.groupby("Target")["ServicesOpted"].mean()

![Alt text](https://github.com/KK-PU/K19-MADT8101-CustomerAnalytics/blob/main/V3_Customer%26Churn%26Campaign/img/AverageServicesOpted%20byTarget.jpg)
