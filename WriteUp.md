![Header](https://github.com/CeliaSagas/Toxic-Rank/blob/7025a22bbf370fe1d986bbfcab512d8c84b5ce49/img/Toxic%20Rank.jpg)




# Toxic - Rank
Ranking Toxic Comments on Wikipedia Talk Page Comments

**Abstract**

Identifying toxic comments is a data science problem, but deciding what criteria is considered toxic is an ethical one. Historically, applications of data science in the fields of ethics and morality have yielded mixed results: it's hard to teach a machine the nuances of valence, hubris, and internet humor while also monitoring datasets for implicit and explicit bias towards minority groups.

**Design**

This project originated from the Jigsaw Rate Severity of Toxic Comments Competition. The data is provided by Jigsaw, a unit within Google that explores threats to open societies, and builds technology that inspires scalable solutions. The challenge is to rate comments from Wikipedia Talk Pages on toxicity level.


**Data**

his project originated from the Jigsaw Rate Severity of Toxic Comments Competition. The data is provided by Jigsaw, a unit within Google that explores threats to open societies, and builds technology that inspires scalable solutions. The data contains over 200,000 pairs of comments rated as 'less toxic' and 'more toxic', comprising of 14,000+ original comments.

**Algorithms**

**Feature Engineering**

The following transformations were performed on the data in order to support further analysis:

  1.	Generated a classification label based on the amount of times a comment appeared in the 'more toxic' column
  2.	Tokenized, stemmed, and cleaned comments
  3.	Performed TFIDF vectorization on tokenized comments
  4.	Reduced features to a set of 25 using Singular Value Decomposition




**Models**

Logistic Regression, Naïve Bayes, Random Forest, XGBoost, and Extra Trees classifiers were used before choosing Logistic Regression as the model with the strongest performance in cross-validation on F1 and ROC AUC scores.

**Model Evaluation and Selection**

The training set of 14,000+ comments was split into 80/20 train vs. holdout, all features were generated separately for training and testing respectively, and all scores were reported below were calculated with 5-fold cross validation on the training portion only.

The metric used for evaluation was f1 and ROC AUC, which are the closest approximations to the metric used on the Kaggle Competition.

Finally, the training and holdout data were combined to train the model for the Kaggle competition data, consisting of 7,537 original and unique comments.

**Logistic Regression 5-fold CV Scores: 25 Features**

  -	ROC AUC: 64.7%
  -	Precision: 81.8%
  -	Recall: 99.7%
  -	F1: 89.9%

**Holdout**

  -	ROC AUC: 64.2%
  -	Precision: 83.3%
  -	Recall: 96.4%
  -	F1: 89.4%

**Competition Test Data**

  -	Current Kaggle Competition Score: 72.4%


**Tools**

  -	Pandas, Numpy, NLTK, Sklearn, XGBoost, Keras, for text processing
  -	Matplotlib Seaborn for data visualization


**Communication**

Data Visualization and write-up will be shared on Medium, Celiasagastume.com, and in class through PowerPoint presentation.
