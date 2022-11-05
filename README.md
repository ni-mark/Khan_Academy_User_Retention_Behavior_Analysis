# Capstone 2 - Khan Academy User Retention Behavior Analysis

Khan Academy is a free online education service that makes educational videos on a large variety of topics and subjects. Watching Khan Academy videos can be done across a variety of streaming services on both mobile and desktop platforms. The company also has a registration system implace on their website to track a user's educational journey. 

## Motivation 
Khan Academy has users using their service across a variety of platforms and through a variety of languages. Taking a one month dataset of all user interactions the goal of this project is to determine which user behaviors or features best predict a return user. Knowing which features increase user retention would allow khan academy to focus on to increase return users. 

## Data 
Data was provided by mentor Yunna Wei and consist of user login and use information on Khan Academy videos. 

The dataset is taken from Feb 18 - Feb 21 2016 with 31480 total data entries. 
Data includes: user id, session id, country of login, language used, user registration flag to Khan Academy, device type, operating system, whether the user used the Khan Academy application, URI, and conversion. The data also included columns for product, domain, subject, topic, tutorial, mission, video_slug, and video title. 


## Data Cleaning

The first step is to check for missing values. The columns of product, domain, subject, topic, tutorial, mission, video_slug, and video title had a missing value count greater than 75% and in most cases above 90% and were dropped accordingly. URI and conversion could be used for future analysis but were not used for this study and were subsequently dropped. 

The most important step in the data wrangling stage was to create a return user column.
I defined a return user as someone who returns to Khan Academy after 4 hours. This was chosen as the data between entries differs in the seconds. Therefore, if a user leaves and returns in more than 4 hours he/she is a return user. 
Of the total 31,481 entries, 21,790 are correlated to a return user. In total there are 432 unique return users.   


## Exploratory Data Analysis

The exploratory data analysis is centered on finding information on the return user.

First, I looked at which country return users are from and there was an overwhelming majority of over 90% towards users in the United States.

Next, I looked at language and as expected over 95% was in english 

Most of the return users were registered Khan Academy users. 

Next most of the return users were using a desktop. 

Likewise, since the Khan Academy app is a mobile app most of the return users were not using it since they were using desktops. 

Windows was the most popular operating system, followed by mac os

Lastly, most of the return users only returned once.


## Feature Analysis 

Chi-Square test followed by an ANOVA test was ran using Sklearn on Python. 
The Chi-Square test resulted in high significance for the features of country, language, OS, device, and registered user
The following ANOVA test confirmed the results found in the chi-square test

## Machine Learning 
A random forest model using Sklearn was created to initiate the machine learning model and served as indicator to rank feature importance
Features of OS and Device Type were one-hot encoded 
Language and Country were encoded of being in english and USA or not, respectively
Sklearn was used to initiate the random forest classifier with an 80% to 20% test train split

After the Random Forest Model a logistic regression was intiated to provide coefficients to measure the percent increase per a unit for the top features of importance
Logistic regression was chosen as the data is categorical, which provides more accurate results than a linear regression.
A registered user is associated with a 65% increased probability of becoming a return user.
English is associated with a 15% increased probability of being a return user. 
Residing in the United States is associated with a 20% decrease probability of becoming a return user. 


## Predictions 
Behavioral recommendations for Khan Academy to increase return users:
Promote registration of users to become members/registered users
Focus on increasing content in english 
Decrease promotion toward the United States user base


## Future Improvements 
Increase the definition of a return user
4 hours to 1 day 
Concern for multicollinearity due to high levels of significance found in feature analysis
Gather more data over time

