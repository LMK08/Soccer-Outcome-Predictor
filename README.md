# NLP Classification

**Author**: Lucas Kimball

# Business Problem

The New York Times is writing an article comparing Apple and Google. They want cold hard data to back up what they say about public sentiment towards these companies and they've hired me to provide them that information. They want a model that can classify tweets as positive, negative, or neutral towards these companies and one that will work on the much larger database or tweets NYT has already got their hands on. 

# Data Source

The dataset comes from CrowdFlower via data.world. Human raters rated the sentiment in over 9,000 Tweets as positive, negative, or neither.

## Modeling

For our modeling we iterated through a series of different models, lemming or stemming, and count vectorization or TF-IDF vectorization to find out which combination gave the best results. We picked AUC ROC score to measure results as we wanted our model to classify data the best, rather than focus on any one label. Our business problem is not sensitive towards positive, negative, or neutral results. For the same reason we displayed the average AUC ROC scores for different models across all emotion labels.

![img]([https://github.com/LMK08/xG_Project/blob/main/Images/download-3.jpg](https://github.com/LMK08/NLP-Project/blob/main/results.png))

## Results

Using the above bar chart, we can see that model using lemmatization, TF-IDF vectorization, and a Random Forest Classifier performed best.

Across all of our findings we can see that Random Forest models consistently performed better than Log Regression or Multinomial NB, Lemming performed better than Stemming and TF-IDF performed better than Count. Therefore it checks out the a model comprised of the 3 best settings would perform the best overall.
