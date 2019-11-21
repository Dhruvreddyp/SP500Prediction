# SP500Prediction
Analyze the stock market based on social media data. 

As President, Trump has a unique source of power and even a slight social media presence may heavily impact changes on a national scale. Some see his Tweets as reckless and some others enjoy his content. His tweets may have a long lasting universal effect and we will observe that effect on a particular category. 
The S&P 500 is a stock market index that measures the stock performance of 500 large companies listed on stock exchanges in the United States and represents a market cap of over $25 trillion. It is one of the most commonly followed equity indices, and many consider it to be one of the best representations of the U.S. stock market.  In a recent experience with someone from a big investing firm, it was clear the many of the giant trading companies use social media to aid in trading and those trades performed in large quantities may cause correlate with market changes. We will observe the effect of Trump’s tweets and presence on twitter to the Stock Market data, particularly the S&P 500 index movement. 
A couple connections to observe include (but not limited to):- 
Impact of Trump Tweets (Quantity) on stock market
Impact of Trump Tweets (Sentiment) on S&P 500
We shall use the above connections, datapoints and given tweets in order to predict the stock market price change after the release of the tweets. In other words, we want to predict how people trade or how the markets react after Trump Tweets. A complication here is that the markets are open only on certain days and closed on other days such as weekends and holidays, so we shall attempt to spend some time understanding the impact of time interval on prediction. A potential method to do so would be to compare prediction accuracy within a day or more than a day based on the tweet release date. 

# Data Sources
Data Source 1: Twitter data from http://www.trumptwitterarchive.com/ 
Columns = source, text, created_at, id_str
Count: 28,505 tweets
Data Source 2: Stock Market (S&P 500 Index) Stock-mendation, Sharecast Data Source Account
Columns = Date, Open Price, Close Price, High Price, Low Price, Volume
Count: 1483 Dates
We have also found sources and libraries online which would enable us in our analysis, we shall mention these sources and library  in our final paper. 
Data Description- What data are we looking at?
The dataset for Trump tweets consists of all of Trump’s Tweets back from 2014 and similarly, the dataset for stock market data grabs the S&P 500 ETF costs back from January 1st of 2014. 
Columns of interest for the trump dataset include the actual textual data and the date of tweet. Other data such as the source of tweet (iphone android) can also be explored. 
