# Capstone-Project
GA DSI Capstone - Amazon Reviews

### Problem Statement + (very) initial EDA

**Problem Statement:**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;If you are anything like me, you like to spend a considerable amount of time reading reviews when deciding to purchase a product or service. The problem with this is that it can be a time consuming process reading through thousands of reviews, which is further complicated by the fact that many of the reviews are unhelpful or at times unrelated to the product in question at all. This creates a situation that can be frustrating for both the consumer and seller, as unfairly biased reviews could cause the seller to miss out on potential revenue or lead the consumer to purchase an inferior product. All of this could potentially lead to increased expenses and lost revenue for Amazon.  

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The goal of this project is to build a model that will be able to predict which reviews are more likely to be flagged as helpful or unhelpful using Natural Language Processing and classification algorithms such as Random Forest or even Neural Nets to group and filter out reviews that are deemed unhelpful. My hope is that this will lead to a better buying experience for the customer, which will in turn lead to an increase in sales for Amazon and sellers alike.

[Data Source](http://jmcauley.ucsd.edu/data/amazon/index_2014.html)  
 have not yet gotten around to deciding on which subset of reviews to use, since they are all very larg files. Based on the data dictionary provided on the page however, I have a good sense of what to expect from the dataset.
 
 **Methodology (rough draft)**  
- EDA (data already has duplicates removed, so that is one less step)
    - remove nulls and try to make sure formatting is consistent (ie. lowercasing, punctuations etc.)
- Group by star rating (positive or negative; will probably have to set a star threshold to demarcate between positive and negative reviews)
- filter reviews by helpful/unhelpful votes to produce 4 classification groups: pos-helpful, pos-unhelpful, neg-helpful, neg-unhelpful
    - use NLP tools and SIA to try to to further refine these classification groups (ie. tokenizing, removing stopwords, polarity scores etc.)
- build classification models using pipeline and gridsearch to find the best hyperparameters to optimize models
- implement appropiate metrics to determine accuracy.