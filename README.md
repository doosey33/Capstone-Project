# Capstone-Project
GA DSI Capstone - Amazon Reviews

## Problem Statement
  
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


## Methodology  
- EDA (data already has duplicates removed, so that is one less step)
    - remove nulls and try to make sure formatting is consistent (ie. lowercasing, punctuations etc.)
- Define target variable and look at distribution.
    - Since target variable was presented as a list of two numbers, the ratio was going to be a continuos variable. To make it fit a classification problem, I picked an arbitrary threshold of 70% to divde variables into one class or another.
    - original dataset had 'helpful' class as minority class, but after dropping about half of the dataset that did not contain scores for helpful column, new dataset had 'helpful' as majority class.
- Created custom cleaning function to clean the reviews to remove any uunewanted characters.
- Deal with class imbalance in target column
    - Create a function to undersample the majority class because of class imbalance, which might cause model to overfit, but also because dataset size was too large to run many functions.
- Word embedding of reviews using Count and TFIDF vectorizers.
- Topic Modeling using Latent Dirichlet Allocation(LDA)
    - grouping into similar categories did not yield the separation that I had hoped for within the target class.
- Modeling:
    - Logistic Regression, Multinomial Naive Bayes, Decision Tree Classifier, Bagging Classifier, Random Forest Classifier, AdaBoost Classifier, Support Vector Classifier.

## Analysis
- In order to try and correctly predict as many 'helpful' reviews as possible, we want to reduce the number of False Positives. In other words, even though we would like to be able to accurately predict each class, it is more preferable for a 'helpful' review to be misclassified as 'unhelpful', than for an 'unhelpful' review to be classified as 'helpful'. Therefore the metric we want to optimize for is: Recall(Sensitivity)
    - the precicion and f1 score would also be good metrics to look at.
- of all the models run, the Logistic Regression and MNB models with TFIDF had the highest recall scores, with both at 61%
- Not the greatest improvement over the baseline prediction of 50%, but I believe I would have been able to get a better score had I been able to word embed my corpus on word2vec. 
    - I don't think the count and tfidf vectorizers were able to represent the text vectors as well as word2vec coudl have.
- I believe a neural net model would have also fared better at classifying the word vectors than the ohter classification models I tried.

## Conclusions/Reccs
- Natural Language Processing is very difficult to model, because of the many different ways humans use language. There are no set number of patterns that a model can learn because the language is ever changing.
    - An example from the dataset that caught my eye was the fact that the most helpful rated review was a pretty funny sarcastic review of a banana slicer. A model woudl have a very hard time trying to pick up on that, and would most likely misclassify it as a helpful review, when any human reading it would say otherwise.
- There are other processing techniques that I would like to try such as spaCY for named entity recognition of parts of speech tags.
    - other processing techniques that woudl help to reduce the dimensions of the corpus and provide some kind of distinction between the target classes, before feeding them into my models.
- Gridsearching over model hyperparameters woudl also help in increasing the accuracy of the models as well.
- These are just some of the steps I plan to impement in the near future, as I work to improve my model.