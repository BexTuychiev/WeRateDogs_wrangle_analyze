# WeRateDogs Twitter Archive Wrangle And Analyze
## By Bex


## Introduction
This project tries to bring the WeRateDogs twitter archive toa usable clean format. The project gathers the necessary data from three different sources:
1. The twitter archive is downloaded from [Udacity](www.udacity.com) servers.
2. In order to get each tweets "like" count and their number of retweets, Twitter's Developer API is used.
3. To get image predictions for each dog's picture `requests` library is used.


## Cleaning Steps
In wrangle_act notebook, I have performed several actions to clean three datasets.

I created the first dataset, we_rd, from the WeRateDogs enhanced twitter archive. The dataset included almost 2500 records of tweets and their id, rating, dog stage, etc. columns. Then, using requests library, I downloaded the contents of tweets corresponding to the tweet_id column in the first dataset. I stored the like count and the number of retweets from a json file to a second dataset, tweets_selected. Final dataset included the results of neural network algorithm to identify the dog breeds. The data was given a direct access for those who could not get the Twitter API developer account.

Overall, I have identified 9 quality and 7 tidiness issues. Most of the issues were in the we_rd dataset. Moreover, it was also very surprising to see so many tidiness issues. Two of the most notable tidiness issues were that dog stages were spread out in 4 different columns and had so many missing values. Even though, I could not fill out the missing values, I have successfully combined dog stages into one single column. The dataset also contained whether the tweet was a retweet or a just a reply to the original tweet. These informations were given in two columns. First, I extracted the ids of the tweets that were retweeted. Then, all the tweets which were replies. Using these ids, I dropped all the corresponding tweets in all three datasets. Another change which was absolutely essential was that some of the ratings of the dogs were extremely high or extremely low. I have analyzed the original channel of WeRateDogs and found out that their highest ever record rating was 15/10. So for all the numerators and denominators there were higher than 15 and 10, I replaced them with correct values and combined these two columns to form a new rating column. In the final staged, I saved the predictions dataframe to a new csv file, whereas for the twitter archive and selected tweets, I joined them into a single master dataframe and saved them to a csv file, ready for analysis.

## Links
- Image Predictions was downloaded using this [link]('https://d17h27t6h515a5.cloudfront.net/topher/2017/August/599fd2ad_image-predictions/image-predictions.tsv')