
# Using NLP to Classify Subreddits

## Danielle Reycer
---

## Problem Statement

Meredith's National Media Group reaches more than 180 million unduplicated American consumers every month, including over 80 percent of U.S. millennial women. Meredith is the No. 1 magazine operator in the U.S., and owner of the largest premium content digital network for American consumers.

They are interested in marketing to parents, especially given that *Parents Magazine* is one of their most popular publications. It is believed that differentiating between pregnant people and those beyond pregnancy will help the marketing team to develop future campaigns that can be more directed. My work aims to come up with a way to distinguish between these two groups and the types of things that people in those groups post about to give information to the Marketing team at Meredith’s Corporation.

I will develop multiple classification models, including a RandomForest, KNearestNeighbors, and LogisticRegression, and I will try ensembling as well to attempt to improve my model. Success will be evaluated using cross validation, attempting to minimize false predictions and minimize overfitting (variance) of my model.

---

## Background

Companies have been trying to market to parents-to-be and new parents for as long as marketing has been around. Understanding the needs of these parents can help a marketing team to better target their specific audience. We aim to gather information about the needs and desires of soon-to-be parents as well as new parents by first classifying posts. This will be the groundwork to identifying trends in posts of each subreddit and determining the liklihood of being able to do so.

---

## My Notebooks

- [01_scraping](https://git.generalassemb.ly/dreycer/project_3/blob/master/code/01_scraping.ipynb)
- [02_eda](https://git.generalassemb.ly/dreycer/project_3/blob/master/code/02_eda.ipynb)
- [03_modeling](https://git.generalassemb.ly/dreycer/project_3/blob/master/code/03_modeling.ipynb)

---

## Data

### Data

I used Reddit's API to scrape data from the ['pregnant'](https://www.reddit.com/r/pregnant/) and ['beyondthebump'](https://www.reddit.com/r/beyondthebump/) subreddits. The raw data contained 2000 posts from each of the subreddits (prior to cleaning and EDA.) 

- `pregnant_df.csv`: Original data scraped using Reddit API from r/pregnant
- `beyondbump_df.csv`: Original data scraped using Reddit API from r/beyondthebump
- `pregnant.csv`: Only 3 columns from original `pregnant` data (`title`, `selftext`, and `subreddit`)
- `beyondbump.csv`: Only 3 columns from original `beyondbump` data (`title`, `selftext`, and `subreddit`)
- `clean_df`: Merged both DataFrames and cleaned up data


### Data Dictionary

|Feature|Type|Description|
|---|---|---|
|**full_text**|*string*|Merged text from original 'title' and 'selftext' columns| 
|**word_count**|*integer*|Number of words separated by spaces in the 'full_text'|
|**question_mark**|*boolean*|Whether or not the text contains a question mark| 
|**something_old**|*boolean*|Whether or not the text contains the phrase 'weeks old' or 'month(s) old'|
|**beyondbump**|*boolean*|**Target** 1 if from r/beyondthebump, 0 if from r/pregnant| 

---

## Conclusions

After evaluating all the models, the one that I chose for our purposes was the Random Forest model. Through cross validation, I found that we are 95% certain that our model will be 78% - 82% accurate at predicting between the pregnancy subreddit and the beyondthebump subreddit. Though the mean accuracy of the chosen model is one percent below that of the Voting Classifier model, the Random Forest is easier to interpret and also takes less time to run. Random Forest also had lower variance than the Voting Classifer model. 

Given that the desire is to be able to generalize our model across other blogs, posting sites, and social media in order to create marketing campaigns we should be aware of the limitations of this model. The posts that were scraped from Reddit were relatively text heavy (mean around 140 words per post). If we were interested in pulling data from a site that limits post length, the model may not generalize well. 

Moving forward, I propose a continuing project on identifying the types of products that parents post about. Furthermore, we can begin to identify at what age range parents begin to wonder about specific products. Using this information, the marketing team would be able to more successfully target their campaigns for when parents need specific items for their children. 
