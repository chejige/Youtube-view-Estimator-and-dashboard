# YouTube view Estimator: Project Overview 
* The main aim of this object is to created a tool that estimates video viewers on channel 'StatQuest with Josh Starmer'. This is a good channel for data science self-leaner. So I am interested to done some dashboard shown and prediction based on the videos in this channel.
* Scraped all the videos from this channel using youtube API. Using two other yoube API to get more features for each video.
* Importing the datas to sql database (SQLite) and join tables to prepare the dataframe for prediction. 
* Preprocessing the data, do the EDA and then processing the data.
* Fit the data with Linear, Ridge, Lasso, Desission tree, Random Forest Regressors to find the best model. 

## Code and Resources Used 
**Coding enviroment:** Google Colaboratory 
**Packages:** pandas, numpy, sklearn, matplotlib, seaborn, selenium, pickle, request, plotly, sqlite3, datatime


##Youtube Scraping
Scrape 221 video from https://www.youtube.com/c/joshstarmer/playlists #StatQuest with Josh Starmer#. 
With each video, we got the following:
*	Video ID
* Title	
* Publish_date	
* viewer_count	
* like_count	
* comment_count	
* categroyID	
* description	
* duration	
* Links	tags	
* plist_num	
* plist1	plist2	plist3	plist4	plist5

## Build a dashboard using streamlit
* Add sidebar with selectbox shows Individual Video Analysis and data anylysis.
In 'data anylysis', show total view, total video and avarage view. Display the detail of top 10 like videos Shows the view and like in recent 1 year.
In 'Individual Video Analysis', add a select box to choose from the video title list. And then display the details for the selected video.
![alt text](https://github.com/chejige/Youtube-view-Estimator-and-dashboard/blob/main/data%20analysis.jpg)
![alt text](https://github.com/chejige/Youtube-view-Estimator-and-dashboard/blob/main/Individual%20video.jpg)

## Data import to database
* Import the data from csv file and then store the data to two tables in SQLite.
* One table has the the main video information, one is the playlist and use left outer join to join these two tables to get the data for prediction.


## Data Cleaning
After download the data from SQL database, I needed to clean it up so that it was usable for our model. I made the following changes and created the following variables:

*	Drop video ID and title.
* Add description length, publish time and tag number columns.
* Change the Catagory ID to catagrical type.
* Log transform 'like_count', 'comment_count', 'description', 'duration'.
* Normalize the rest numerical data.

## EDA
I looked at the distributions of the data and the value counts for the various categorical variables. Below are a few highlights from the pivot tables. 

![alt text](https://github.com/chejige/Youtube-view-Estimator-and-dashboard/blob/main/boxplot.png)
![alt text](https://github.com/chejige/Youtube-view-Estimator-and-dashboard/blob/main/histplot.png)
![alt text](https://github.com/chejige/Youtube-view-Estimator-and-dashboard/blob/main/pairplot.png)
![alt text](https://github.com/chejige/Youtube-view-Estimator-and-dashboard/blob/main/heatmap.png)

## Model Building 

First, I transformed the categorical variables into dummy variables. I also split the data into train and tests sets with a test size of 10%.   

I tried five different models and evaluated them using Mean Absolute Error. I find disicion tree model get the smallest MAE.
* MAE: 59748.96
* RMSE: 148952.70
* R2 score: 0.89

The model we chose has very little tendency to overfitting, but we think it can be tolerated within normal reasonable limits.




