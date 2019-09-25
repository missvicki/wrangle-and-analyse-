# wrangle-and-analyse-

Data Analysis: Wrangle and Analyse the WeRateDogs twitter archive

WeRateDogs is a Twitter account that rates people's dogs with a humorous comment about the dog. These ratings almost always have a denominator of 10. The numerators, though? Almost always greater than 10. 11/10, 12/10, 13/10, etc. Why? Because "they're good dogs Brent." WeRateDogs has over 4 million followers and has received international media coverage. The WeRateDogs Twitter archive contains basic tweet data for all 5000+ of their tweets, but not everything.

# The data wrangling process

The data wrangling process is a 3 step procedure involving gathering data, assessing data that has been gathered and cleaning data. Often before gathering data, there are questions we may need to ask to better understand what kind of data we are to deal with or collect.
The questions we ask help in guiding our analysis and keeping us on track so as not to lose sight of the goal.

For this project, I wished to know 3 things:
The most favorite dog stage between doggo, floofer, pupper, and puppo
The We Rate Dogs tweeting trend over time. Has it declined or increased?
The average number of dogs rated above 10

## Gathering data

I had to gather three different kinds of data namely;
The WeRateDogs Twitter archive.
The tweet image predictions, i.e., what breed of dog (or other object, animal, etc.) is present in each tweet according to a neural network. This file (image_predictions.tsv) is hosted on Udacity's servers and should be downloaded programmatically using the Requests library and the following URL: https://d17h27t6h515a5.cloudfront.net/topher/2017/August/599fd2ad_image-predictions/image-predictions.tsv
Each tweet's retweet count and favorite ("like")

The Twitter archive had been provided in csv format and all I needed to do was load it using the pandas data frame into the twitter_archive table.
The tweet image predictions file was on the Udacity website and I made use of requests, responses and urls to get the data which I finally stored in the images table.
For the last part of the data to be gathered, I made use of the twitter API to fetch the retweets and favorite counts. This process was slow and tedious and seemed to take a very long time to return. I stored the data fetched in the tweet_data table.

## Assessing data

After gathering each of the above pieces of data, I was required to assess them visually and programmatically for quality and tidiness issues. I was able to detect and document at least eight (8) quality issues and two (2) tidiness issues.

Quality issues are issues with content.
In the twitter archive data frame, the following issues were present:
Has retweets and therefore data may be duplicated
Missing tweet ids of twitter archive data frame in the images data frame
Has columns that are not needed for analysis
Incorrect data type for timestamp which is indicated as string and not date time
dog names starting with lowercase letters and some unusual dog names for example a, such, the, this, unacceptable, e.t.c

In the images data frame, the following issues were present:
duplicated jpg_url
p1, p2, p3 columns have underscores instead of space
inconsistent capital letters in p1, p2 and p3

Tidiness issues are issues with structure that prevent easy analysis. The following issues were detected from the three tables.
doggo, floofer, pupper, and puppo columns in twitter_archive should be in one column "stage"
all three data frames should be one data frame as they have similar data for tweets

## Cleaning data

Under this section, I was able to clean each of the issues I documented while assessing. I followed a detail, code and test approach during cleaning whereby detail included details of the issue and cleaning method am proposing.
