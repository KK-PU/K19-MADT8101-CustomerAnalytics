# # Customer Analytics - work 03
 - Customer Scoring
 - Churn Scoring
 - Campaign Response Scoring

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1xCf9wOiVfyl2-W0QO8W2PmFThLQJjV7X)

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

**Annual Income Class by Target**

The annual income level of the target group

![Alt text](https://github.com/KK-PU/K19-MADT8101-CustomerAnalytics/blob/main/V3_Customer%26Churn%26Campaign/img/AnnualIncomeClass.jpg)

**Account Synced To SocialMedia**

Social media synced accounts

![Alt text](https://github.com/KK-PU/K19-MADT8101-CustomerAnalytics/blob/main/V3_Customer%26Churn%26Campaign/img/AccountSyncedToSocialMedia.jpg)

**Booked Hotel Or Not**

![Alt text](https://github.com/KK-PU/K19-MADT8101-CustomerAnalytics/blob/main/V3_Customer%26Churn%26Campaign/img/BookedHotelOrNot.jpg)


## Data Processing
Take the F1-scores of all models to collect and display the values.

from sklearn.feature_selection import SelectKBest, f_classif
    from sklearn.model_selection import KFold, GridSearchCV
    from sklearn.metrics import make_scorer, f1_score
    import xgboost as xgb

    # Define our search space for grid search
    search_space = [{
    'clf__n_estimators': [100, 200, 300, 400],
    'clf__learning_rate': [0.01, 0.1],
    'clf__max_depth': [3, 4, 5],
    'clf__colsample_bytree': [i/10.0  for i in  range(2, 5)],
    'clf__gamma': [i/10.0  for i in  range(3)],
    'fs__score_func': [f_classif],
    'fs__k': ['all'],
    }]
    
    # Define cross validation
    kfold = KFold(n_splits=5)
    
    # Define grid search
    grid = GridSearchCV(
	    pipe,
	    param_grid=search_space,
	    cv=kfold,
	    scoring=scoring,
	    refit='F1 score',
	    verbose=1,
	    n_jobs=-1
	    )
	# Fit grid search
	xgb_model_clv_GS = grid.fit(X_train, y_train)
	
	# Get best parameters and best F1 score
	best_params = xgb_model_clv_GS.best_params_
	best_score = xgb_model_clv_GS.best_score_
	
	# Print best parameters and best F1 score
	print("Best Parameters:", best_params)
	print("Best F1 Score:", best_score)


 Use the F1 Score to measure the performance of all models.

**Best Parameters:**

-   'clf__colsample_bytree': 0.4
-   'clf__gamma': 0.1
-   'clf__learning_rate': 0.1
-   'clf__max_depth': 5
-   'clf__n_estimators': 200
-   'fs__k': 'all'
-   'fs__score_func': f_classif at 0x7bc7a3436200

**Best F1 Score:**

-   The best F1-Score value obtained from the test is 0.7884057971014492 (Efficiency value ranges between 0-1)
-   Total number of trials totaling 1080 fits






