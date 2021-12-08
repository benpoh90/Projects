# Executive Summary: NLP Classification of Sub-Reddits

### Introduction

**Sub-reddit chosen**: r/britishproblems and r/BritishSuccess

You are working for SGAG in Singapore and have been tasked to explore new social media engagement channels via Reddit. Since Singaporeans are known to complain a lot, you are thinking of creating sub-reddits that would encourage users to post about the travails of daily life in humourous ways. 

You are aware of two sub-reddits from the UK that fit your idea (r/britishproblems and r/BritishSuccess). On the surface, they appear to be distinct topics (complaining about problems vs. celebrating success). However, taken in the context of british humour, they could potentially be quite similar in terms of their linguistic construct. 

To explain, british humour is largely based on sarcasm and satire and is aimed at the absurdity of everyday life. As such, ironic language is often deployed in its execution. Naturally, this means that such humour is highly context-based and could potentially be difficult to distinguish for a non-human reader. For example, in the context of our sub-reddits, consider the statement below:

*'I am excited to be taking a nice stroll in the rain again...'*

Would the machine learning algorithm classify this as a 'success' since you have words associated with positive sentiments (e.g. excited, nice stroll)? The poster - living in wet and cold London - is most likely complaining about having to go out in the rain. 

*Note: This is project 3 for General Assembly Singapore's DSI24 course.*

---

### Problem Statement

You are also considering the idea of creating two sub-reddits - *SingaporeanProblems* and *SingaporeanSuccess*. However, you want to avoid the two sub-reddits cannablising viewership from each other in the event that they both end up being very similar. Like British humour, Singlish is also a highly dynamic language form. Therefore, by investigating the differentiating features in the two sub-reddits, you want to find out if humour (especially ironic language) can be differentiated by the model. This will then allow you to decide whether to set up one or two sub-reddits.

---

### Datasets

#### Data scraped from Reddit 

Using the Pushshift API, I scraped 2000 posts from each sub-reddit (r/britishproblems and r/BritishSuccess). Being more popular, the 2000 posts from BritishProblems are all from September while the 2000 posts from BritishSuccess are from April to September.

---

### Findings

My methodology is as follows:

**Lemmatization $\rightarrow$ Vectorization $\rightarrow$ Modelling (train dataset) $\rightarrow$ Predicting**

I have trained several models (Logistic Regression, Random Forest and Multinomial Naive Bayes) and tuned the parameters with `GridSearchCV`.

The best model from my project is: **Lemmatization + Count Vectorizer x Multinomial Naive Bayes**. This model has an accuracy score of 79% and F1 score of 77.5%.

*Summary of scores:*
|CVEC x NB|Score|
|---|---|
|Best Score|0.749|
|Accuracy Score|0.792|
|Precision|0.771|
|Recall|0.781|
|F1|0.775|

Key Points:
   - Removing lemmatization does not improve the model
   - Words that distinguish both models: 'crane (flies)', 'unable', 'arse', 'mask', 'nhs', 'finally'
   - Misclassification due to sarcasm, irony, coincidence
  
---

### Conlusion

Our model performed fairly accurately in predicting posts belonging to each sub-reddit. Creating a **SingaporeanProblems** and **SingaproeanSuccess** would probably not cannabalise viewership from each other. However, there are limitations to our model - sentence embedding tools such as BERT and a larger dataset can help improve our model.

---
