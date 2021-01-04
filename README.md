# Wrangle-and-Analyze-Data
WeRateDogs is a Twitter account that rates people's dogs. we gather, assess and cleaning data to extract insights and make visualizations to answer the questions provided on this data.

## Introduction 

Real-world data rarely comes clean. Using Python and its libraries, you will gather data from a variety of sources and in a variety of formats, assess its quality and tidiness, then clean it. This is called data wrangling. I will document my wrangling efforts in a Jupyter Notebook.

These ratings almost always have a denominator of 10. The numerators, though? Almost always greater than 10. 11/10, 12/10, 13/10, etc. Why? Because "they're good dogs Brent." WeRateDogs has over 4 million followers and has received international media coverage.

![dog-rates-social](https://user-images.githubusercontent.com/49722916/103572289-fe374380-4ed4-11eb-8571-447a119b9260.jpg)

## The Datasets

### 1.Enhanced Twitter Archive

The WeRateDogs Twitter archive contains basic tweet data for all 5000+ of their tweets, but not everything. One column the archive does contain though: each tweet's text, which I used to extract rating, dog name, and dog "stage" (i.e. doggo, floofer, pupper, and puppo) to make this Twitter archive "enhanced." Of the 5000+ tweets, I have filtered for tweets with ratings only (there are 2356).

<img width="1317" alt="screenshot-2017-10-10-18 19 36" src="https://user-images.githubusercontent.com/49722916/103572560-6dad3300-4ed5-11eb-9ef2-37af35b14639.png">

### 2.Image Predictions File

A table full of image predictions (the top three only) alongside each tweet ID, image URL, and the image number that corresponded to the most confident prediction (numbered 1 to 4 since tweets can have up to four images).
    
                        Tweet image prediction data
<img width="1308" alt="screenshot-2017-10-10-18 43 41" src="https://user-images.githubusercontent.com/49722916/103572704-b107a180-4ed5-11eb-83ee-d98bb37754ee.png">

So for the last row in that table:

* tweet_id is the last part of the tweet URL after "status/" → https://twitter.com/dog_rates/status/889531135344209921
* p1 is the algorithm's #1 prediction for the image in the tweet → golden retriever
* p1_conf is how confident the algorithm is in its #1 prediction → 95%
* p1_dog is whether or not the #1 prediction is a breed of dog → TRUE
* p2 is the algorithm's second most likely prediction → Labrador retriever
* p2_conf is how confident the algorithm is in its #2 prediction → 1%
* p2_dog is whether or not the #2 prediction is a breed of dog → TRUE
* etc.

### 3.The Twitter API

Back to the basic-ness of Twitter archives: retweet count and favorite count are two of the notable column omissions. Fortunately, this additional data can be gathered by anyone from Twitter's API. Well, "anyone" who has access to data for the 3000 most recent tweets.

**I used twitter-api.py file to query the twitter data using the four keys (consumer_key, consumer_secret, access_token, access_secret)**

## Key Points

* I only want original ratings (no retweets) that have images. Though there are 5000+ tweets in the dataset, not all are dog ratings and some are retweets.

* The requirements of this project are only to assess and clean at least 8 quality issues and at least 2 tidiness issues in this dataset.

* Cleaning includes merging individual pieces of data according to the rules of tidy data.

* The fact that the rating numerators are greater than the denominators does not need to be cleaned. This unique rating system is a big part of the popularity of WeRateDogs.

* I do not need to gather the tweets beyond August 1st, 2017.

## Project Details

tasks in this project are as follows:

* Data wrangling, which consists of:
  * Gathering data .
  * Assessing data
  * Cleaning data
  
* Storing, analyzing, and visualizing your wrangled data
* Reporting on 1)  data wrangling efforts **wrangle_report.pdf**  and 2)  data analyses and visualizations **act_report.pdf**

## 1.Gathering Data 

1. twitter_archive_enhanced.csv, so download it and include it in the notebook

2. image_predictions.tsv is hosted on Udacity's servers and should be downloaded programmatically using the Requests library and the following URL: https://d17h27t6h515a5.cloudfront.net/topher/2017/August/599fd2ad_image-predictions/image-predictions.tsv

3. Each tweet's retweet count and favorite ("like") count at minimum, and any additional interesting data. Using the tweet IDs in the WeRateDogs Twitter archive, query the Twitter API for each tweet's JSON data using Python's Tweepy library and store each tweet's entire set of JSON data in a file called **tweet_json.txt** file. Each tweet's JSON data should be written to its own line. Then read this .txt file line by line into a pandas DataFrame with (at minimum) tweet ID, retweet count, and favorite count. 


## 2.Assessing Data 

After gathering each of the above pieces of data, assess them visually and programmatically for quality and tidiness issues. Detect and document at least eight (8) quality issues and two (2) tidiness issues in  wrangle_act.ipynb Jupyter Notebook.

## 3.Cleaning data 

Clean each of the issues you documented while assessing. Perform this cleaning in wrangle_act.ipynb as well. The result should be a high quality and tidy master pandas DataFrame.

## 4.Storing, Analyzing, and Visualizing Data for this Project

Store the clean DataFrame(s) in a CSV file with the main one named **twitter_archive_master.csv**. Analyze and visualize  wrangled data in  wrangle_act.ipynb Jupyter Notebook. At least three (3) insights and one (1) visualization must be produced.
