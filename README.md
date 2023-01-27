# Emotion-Detection-through-Text

![1_NF6AdPk6sOMNNbQE5glvEQ](https://user-images.githubusercontent.com/108106393/214875843-4d6e4687-4933-465c-ba89-b1e4ad765a95.png)

# Objectives 
This text based emotion detection project aims to clean, parse and analyze textual data from twitter to predict user emotions using Natural Language Processing. Another objective of this project is to use different classification models to figure out which one produces the best metric score. Picking the best classification model will provide us with the least emotion misclassification. This dataset contains tweet ids, tweets and the sentiment for each tweets. 

# Business Problem 
A social media company wants to improve user engagement on their platform by better understanding the emotions their users are expressing in their posts using a text based recognition system. This system aims to automatically classify emotions as positive or negative. It will be used to identify trending user topics and user sentiments. 

# Data 
This project used the Emotion Detection from Text dataset from Kaggle. It contained 40,000 datapoints, 3 rows and 13 unique sentiments.
https://www.kaggle.com/datasets/pashupatigupta/emotion-detection-from-text

# Methods
The first step in conducting this emotion detection project is to preprocess the text data. Before preprocessing, I looked at some tweets grouped by sentiment and noticed that there are a lot of misclassified tweets especially the short ones so I decided to drop all rows with a length of less than 100, filtered it to just 4 sentiments combined as positive and negative. There is a step by step preprocessing technique that needs to be followed when cleaning, considering that I'm working with a twitter dataset, I have to lowercase the entire dataset, find urls, hashtags, mentions and strip whitespace. This process also includes tokenizing the texts, removing stop word, removing non-english patterns and lemmatizing it before plugging into a vectorizer. I conducted an EDA before modeling and my visuals include:

This graph shows the distribution of positive and negative sentiment: 
![sentiment](https://user-images.githubusercontent.com/108106393/214896837-af3bf4f0-f9a8-49e8-9613-d9806b71f544.png)

There's a little bit of class imbalance between the 2 classes, Class 0: 60% and Class 1: 40%

These 2 visuals shows the top 20 words in each sentiment
![positivetop20](https://user-images.githubusercontent.com/108106393/214898406-0236ef37-657f-4353-a31e-ff5d088076fb.png)
![negativetop20](https://user-images.githubusercontent.com/108106393/214898437-0b45150c-691e-4b53-968b-64ce297c26dc.png)

I also generated a wordcloud for the positive (1) and negative (0) sentiment:

Wordcloud of Positive Sentiments:
![wcpos](https://user-images.githubusercontent.com/108106393/214899981-d82d8b0e-2532-4fd3-b75c-a1c45f0f6b06.png)

Wordcloud of Negative Sentiments:
![wcneg](https://user-images.githubusercontent.com/108106393/214900018-22f0e211-f2f9-4ee8-9ad6-dda040ffbe50.png)

Producing the wordcloud is the last part of my EDA before I started Modeling. I created 7 models starting with a simple Logistic Regression model, I also used a bunch of Tree Based Classification Models and some Boosting Classifiers. The stacked Multionomial Naive Bayes and XGBoost ended up having the best f1 score out of all the models. I picked the f1 score as my metric to balance out my false negatives and false positives. Depending on your dataset and what the objective of the model is, you can focus on either recall or precision. 

# Summary of Best Models
![Screenshot (7)](https://user-images.githubusercontent.com/108106393/214905702-48fc7560-4cae-40f4-a6e7-02b3aea86056.png)
 
# Stacking Classifier
After tuning a bunch of classification models, I picked the Stacking Classifier as my best model
![CONF](https://user-images.githubusercontent.com/108106393/214907053-b0bffe2b-4f3c-417a-aaf1-1de5b54ce45c.png)

This model produced an AUC of 0.76
![AUC](https://user-images.githubusercontent.com/108106393/214907125-a200d092-a293-4869-85b4-69e4bc2aad55.png)

# Recommendations
1. Gather more properly classified data and with these we would be able to drastically lower the misclassification between classes
2. Try to use more advanced preprocessing procedures like bigrams/trigrams to get more contextual information than just individual words





