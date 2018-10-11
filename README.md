# Streaming-twitter-data-api



## Python Script will help user to stream/search/download tweets based on different tracks, search parameters, etc.


### Prerequisites

This script is developed in Python 3.6 using the following packages :
```
Flask
Tweepy
PyMongo
json
time
datetime
io
```
### You will also need a running MongoDB client on your machine


To use this script -
```
Clone this repository.
Download all the packages required.
Run the script streamtest.py in command prompt.
Visit http://127.0.0.1:5000/ for the root access to the script.
Use different API endpoints as mentioned below for different works.
```
## API 1 (Trigger Tweets)

endpoint - /trigger?```<arguments>```
```
This endpoint will trigger a thread to stream all the tweets on a certain keyword present in the tweet text and store them in a database.
```
### Arguments :
```
keyword - NECESSARY argument needed for this API. This is the keyword which would be searched in the tweet stream. example - /triggertweets?keyword=nana_patekar
max_tweets - OPTIONAL argument to specify after how many tweets to stop the streaming. If not provided, default value 10 is taken. example - /triggertweets?keyword=nana_patekar&max_tweets=50
```

## API 2 (GET RESULTS ON WEBPAGE)

endpoint - /getresults?```<arguments>```

This endpoint can be used to search and analyse different tweets already present in the database or after adding the tweets using the 1st API. This endpoint will provide results by using pagination as the number of tweets could be really large. Using this API, we can - ..* Search for all tweets for a given keyword. ..* Search tweet texts to find a substring in a partical track. ..* Can apply filters such as sort , slice, dice, range filters, etc.

### Arguments:
```

* keyword - NECESSARY argument needed to search tweets based on that specific track. Will provide a Bad Request 400 if not provided.
* limit - To limit the number of tweets displayed upfront. Can be varied. Default is 10.
* offset - To tell which index tweet to start displaying with.
* name - Search tweets by user's Display Name.
* screen_name - Search tweets by user's Screen Name.
* retweet_count - Search tweets with given minimum retweet count.
* reply_count - Search tweets with given minimum reply count.
* favorite_count - Search tweets with given minimum favorite count.
* lang - Search tweets with given language (eg - en,hi,etc.)
* sort_by - Sorts the output by the given field (id,created_at,text). Default is id.
* order - order the sorted tweets in ASC(ending) or DESC(ending) order. Default is ASC.
* date_start - Search tweets only after starting date (converted to timestamp for computation).
* date_end - Search tweets only before ending date (converted to timestamp for computation).
* search - Tells which string parameter to search in the tweets for a given substring.
* search_type - Tells how to search the substring in the given parameter (starts,ends,contains). NECESSARY when search is not null.
* search_value - Tells which substring to find in the given parameter. NECESSARY when search is not null.
```
## API 3 (Download Results as a CSV)

endpoint - /download/getresults?<arguments>

This endpoint works exactly like API 2 but instead of having the results displayed on the webpage, it downloads a CSV file containing the results. All the arguments and formats remain same as API 2.



