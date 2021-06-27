# Project-3
## Subreddit classification - r/wallstreetbets &amp; r/valueinvesting

Reddit is an online forum where users can post ideas/ contents in groups called subreddits. It is widely popular and naturally this provides us with a huge database of text data regarding a certain topic. In this notebook, we seek to explore the use of natural language processing in classifying which subreddit does a post belong to.

We have selected r/wallstreetbets and r/valueinvesting as the subreddits in this study. These are 2 subreddits that discuss about investments in the financial markets, most of the posts are either questions regarding investing or investment pitches. Where the 2 subreddits defer is on the style of investing as well as the tone of discussion. r/wallstreetbets is more casual and filled with memes, their general investment methodology includes going all in (or YOLO) into high risk growth stocks hoping for it to go to the moon. r/valueinvesting is more serious in its discussion, their investment methodology is (as the title says) value investing where they place emphasis on the company’s fundamentals.

Classifying between the 2 subreddits is particularly interesting. A well-developed model that can distinguish between the 2 subreddits can be extended to a model that can interpret a given text related to investment (e.g. investment advise) is classified as value investing, growth investing or just meme investing.

# Problem Statement
To what extent can a classification model distinguish between posts from r/wallstreetbets and r/valueinvesting?

# Executive Summary
In this project file, we used Reddit's API to extract posts from the subreddits r/wallstreetbets and r/valueinvesting. After cleaning the data we are left with 825 post from r/wallstreetbets and 705 from r/valueinvesting. The models used in this study are Logistic Regression, Support Vector Machine (SVM), Naive Bayes Classification. To select the optimal classification model, we will be using GridSearchCV to compare the scores of models. Each model will be run twice, once with a CountVectorizer and the second time with a TfidfVectorizer; this leaves us with 6 models to compare.

After comparing models evaluation metrics, the model with SVM and TfidfVectorizer was the best with an accuracy score of 90.9% (baseline 54%).

# Model Results
|#|Vectoriser|Model|Accuracy|
|---|---|---|---|
|1|CountVectorizer|Logistic|0.879895561|
|2|TfidfVectorizer|Logistic|0.903394256|
|3|CountVectorizer|SVM|0.874673629|
|4|TfidfVectorizer|SVM|0.908616188|
|5|CountVectorizer|Naive Bayes|0.903394256|
|6|TfidfVectorizer|Naive Bayes|0.895561358|

We found that using a TfidfVectorizer with a Subjective Vector Machine produced the best results. The model achieved a relatively high accuracy score of 90.9%.

# Evaluation

### Model:

The downside of this model being an SVM is that it is a blackbox model, input is coverted to output but there is not much to infer from the model.

All the models that were evaluated did not fully solve the issue of overfitting. We still observe very high accuracy score for the train dataset compared to the test dataset. This can be resolved with further tuning the model, where we reduce the variance of the model. It could also be reduce if we had a bigger sample of text.

### Data collection:

r/wallstreetbets has 10M followers, r/valueinvesting has 100k followers. The difference in the followers may have some impact on the sample data. 

r/wallstreetbets had a high proportion of media post, these were dropped at the start of the study as they did not contain any text in the body.

The posts collected were collected at different timings and not systematically.

All in all the data collection process could be improved if a cleaner dataset was extracted from Reddit. A better subreddit that is similar to r/valueinvesting could be chosen.
