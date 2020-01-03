# S&P 500 Prediction
Analyze the stock market based on social media data, specifically Trump's messages. 

Perform a vader sentiment analysis and normalize scores based on the content of the tweet and create several prediction models to predict whether the stock market will increase or decrease. 

Visit the published site at 
https://sites.google.com/g.harvard.edu/team51/

# Preface
As President, Trump has a unique source of power and even a slight social media presence may heavily impact changes on a national scale. Some see his Tweets as reckless and some others enjoy his content. His tweets may have a long lasting universal effect and we will observe that effect on a particular category. 

The S&P 500 is a stock market index that measures the stock performance of 500 large companies listed on stock exchanges in the United States and represents a market cap of over $25 trillion. It is one of the most commonly followed equity indices, and many consider it to be one of the best representations of the U.S. stock market.  In a recent experience with someone from a big investing firm, it was clear the many of the giant trading companies use social media to aid in trading and those trades performed in large quantities may cause correlate with market changes. We will observe the effect of Trump’s tweets and presence on twitter to the Stock Market data, particularly the S&P 500 index movement. 

# Problem Scope
The S&P 500 index has been fluctuating constantly as described in previous sections of the paper. 

Trump's Tweets as President of the United States has had relevant impact and now can be used to model the stock market, particularly the S&P500.

# Initial Analysis Plan
A couple connections to observe include (but not limited to):- 
1. Impact of Trump Tweets (Quantity) on S&P 500 stock market
2. Impact of Trump Tweets (Sentiment) on S&P 500 index

We shall use the above connections, datapoints and given tweets in order to predict the stock market price change after the release of the tweets. In other words, we want to predict how people trade or how the markets react after Trump Tweets. A complication here is that the markets are open only on certain days and closed on other days such as weekends and holidays, so we shall attempt to spend some time understanding the impact of time interval on prediction. A potential method to do so would be to compare prediction accuracy within a day or more than a day based on the tweet release date. 

# Data Sources
Data Source 1: Twitter data from http://www.trumptwitterarchive.com/ 
Columns = source, text, created_at, id_str
Count: 28,505 tweets
Data Source 2: Stock Market (S&P 500 Index) Stock-mendation, Sharecast Data Source Account
Columns = Date, Open Price, Close Price, High Price, Low Price, Volume
Count: 1483 Dates
We have also found sources and libraries online which would enable us in our analysis, we shall mention these sources and library  in our final paper. 

# Data Description- What data are we looking at?
The dataset for Trump tweets consists of all of Trump’s Tweets back from 2014 and similarly, the dataset for stock market data grabs the S&P 500 ETF costs back from January 1st of 2014. 
Columns of interest for the trump dataset include the actual textual data and the date of tweet. Other data such as the source of tweet (iphone android) can also be explored. 

# Data Processing

The Data Processing aspect of the project presented as the most time consuming as there were simple nuances in data types and adequately matching columns such as dates. 

Trump Tweet Data is the training data and serves as the training set. This data contains information about the actual individual tweets and the actual tweet itself as described previously. The stock market price changes will serve as the outcome or response variables. 

Several pandas dataframe grouping methods were used in order to gather relevant data and merge the two datasets. 

The twitter data was initially prepared by creating a function that would clean the tweet and then create a sentiment analysis using the Textblob library. 

The code snippet is as follows (as depicted in Supporting notebook):- 

positive = [ tweet for index, tweet in enumerate(tweets['text']) if tweets['sentiment'][index] > 0]

neutral = [ tweet for index, tweet in enumerate(tweets['text']) if tweets['sentiment'][index] == 0]

negative = [ tweet for index, tweet in enumerate(tweets['text']) if tweets['sentiment'][index] < 0]

Problem with this implementation is that each tweet was given only a 0, -1 or +1, but each tweet could have been in any range between the three.

There was a trajectory change when there was a realization that each day of tweeting for trump could have been a range of positive and a range of negative and how positive or how negative the tweet was mattered. 

Eventually, we found that several libraries already exist that can outperform our individual attempts to perform a sentiment analysis and thus we used that to our advantage.  The SentimentIntensityAnalyzer from the vaderSentiment module in the vaderSentiment  library helped create a sentiment analysis of each individual tweet with several polarities for each sentence.  VADER not only tells about the Positivity and Negativity score but also tells us about how positive or negative a sentiment is.

There are polarity_scores with a compound metric which calculates normalized lexicon ratings (more information on MIT's Vader Github).

So, after cleaning the text of Trump's tweets, we performed the sentiment analysis to extract the sentiment and subjectivity of each tweet. 

After performing this sentiment analysis, we are left with quite a few columns in our dataset. We shall further drop unneeded columns so that we are left with an input dataset of retweet_count, favorite_count, sentiment and subjectivity for each tweet. 

Next, we shall process the stock market data which consists of 6 different files of historical stock market data for the S&P500 Index. 

This Stock market data has dates and times for each ticker which is more information than needed. We shall process the data by simply gathering the data based on each given day. 

Pandas Merging the two datasets to form a connected and combined dataset.

As stated above, the only thing left to do is to join the datasets. 

After a little more data processing using the datetime library in python, we shall concatenate the two datasets into one full dataset. 

We merge the dataset based on each day and then based on the sentiment calculations of that day, we will create our models.

# Best model
Logistic Regression Classifier score on Test set

Accuracy: 0.5601888276947286

# Closing Thoughts
We see that the logistic regression model outperformed the other models such as KNN and even XGBoost. This is a significant accuracy score on the test set and is better than a random coin toss. 

# Project Challenges
There were many challenges and changes that presented throughout the course of this project. 

Initially, we began with a group of four members each of which had agreed to a certain responsibility and committed to a common goal. Eventually, two of the group members dropped the course and left us with no prior notice. 

Although the main idea and theme of this project stayed the same, there were many changes made throughout. 

Initially, there was an idea to model the Impact of Trump Tweets (Quantity) on stock market, but we changed that to the sentiment of Trump's tweets on the S&P 500 index. Also, initially, there was a plan to  spend time in understanding the impact of time interval on prediction. For instance, would Trump's tweet today affect the market today or tomorrow? 

There are snippets of code in the accompanying jupyter notebook that further processes the dates in order to model the impact of Trump's tweet's today on the following day's market change. The sources of Data were the same, but the actual data has several key differences. Initially when modelling Trump's tweets, there was only one attribute which represented the sentiment of the tweet, but now there are many more features that were extracted from the twitter data. 

The model performs at a mediocre performance level on the test set. A researcher would be happy that the model  performs better than a coin toss, but improvements are definitely possible. For instance, in one of the previous iterations of a similar experiment, a researcher used naivebayes as a baseline model which performed worse. 

Then, the researcher made use of support vector machines and spent the rest of the time in developing a Recurrent Neural Network(LSTM) that used a word vectorization approach with the pre-trained embedding vector of GloVe. Glove is a standard Word2Vec model, which uses the co-occurrence information of the words to map one-hot vector representation of words to lower dimension. 

# Future Work
To improve this model and improve accuracies, it may be of use to create and extract more feature variables. Currently, only 4 attributes are being used in our best model (logistic regression classifier), but having more data and information to capture the underlying distributions may greatly increase scores. 

All the models tested today were of great use for classification, as stated in the Data modeling and Results section. 

Similar to experiments done in the literature review section, it may be of use to experiment with other models and techniques. 

For instance, is it possible to use bagging and boosting in this case? Would a Neural Network with word embedding and out of bag word choices perform better? 

Is it possible to add more feature variables? What predictors would contribute significantly to a better model? Would a random forest classifier perform better than XGBoost?

All these are questions that require further analysis and more time invested in order to explore adequately. 


Overall, we found that even a simple model such as logistic regression can sometimes outperform other far complex and intuitive models. 
