# Capstone-Project
GA DSI Capstone - Amazon Reviews

### Problem Statement

**Problem Statement:**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;If you are anything like me, you like to spend a considerable amount of time reading reviews when deciding to purchase a product or service. The problem with this is that it can be a time consuming process reading through thousands of reviews, which is further complicated by the fact that many of the reviews are unhelpful or at times unrelated to the product in question at all. This creates a situation that can be frustrating for both the consumer and seller, as unfairly biased reviews could cause the seller to miss out on potential revenue or lead the consumer to purchase an inferior product. All of this could potentially lead to an increase in expenses and lost revenue for Amazon.  

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The goal of this project is to build a model that will be able to predict which reviews are more likely to be flagged as helpful or unhelpful using Natural Language Processing and classification algorithms such as Random Forest or even Neural Nets to group and filter out reviews that are deemed unhelpful. My hope is that this will lead to a better buying experience for the customer, which will in turn lead to an increase in sales for Amazon and sellers alike.

[Data Source](http://jmcauley.ucsd.edu/data/amazon/index_2014.html)  

## Data Dictionary

|Feature|Type|Dataset|Description|
|---|---|---|---| 
|asin|object|votes_df|Unique ID of the product being reviewed,|
|helpful|list|votes_df|A list containing the number of users that voted helpful, and the total number of users that voted on the review|
|overall|int64|votes_df|The reviewer's rating of the product|
|reviewText|object|votes_df|review text|
|reviewerID|object|votes_df|Unique ID of the reviewer|
|reviewerName|object|votes_df|Name of the reviewer|
|summary|object|votes_df|heading summary of review|
|unixReviewTime|object|votes_df|Unix Time of when the review was posted|


 **Methodology **  
- EDA (data already has duplicates removed, so that is one less step)
    - remove nulls and try to make sure formatting is consistent (ie. lowercasing, punctuations etc.)
- Group by star rating (positive or negative; will probably have to set a star threshold to demarcate between positive and negative reviews)
- filter reviews by helpful/unhelpful votes to produce 4 classification groups: pos-helpful, pos-unhelpful, neg-helpful, neg-unhelpful
    - use NLP tools and SIA to try to to further refine these classification groups (ie. tokenizing, removing stopwords, polarity scores etc.)
- build classification models using pipeline and gridsearch to find the best hyperparameters to optimize models
- implement appropiate metrics to determine accuracy.


