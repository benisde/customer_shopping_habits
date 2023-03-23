# Movie Recommendation and ROI models analysis

Our goal was to develop an AI tool that is a content-based filtering method for movie recommendations to suggest movies to users based on the movies' content and the users' preferences.

The system analyzes the content of the movies, such as their genre, keywords, the mood of the users, and cult classics per genre, and uses this information to determine which films are similar to each other.

This tool provides recommendations that users predict future preferences by using their past experiences and preferences. These services use sophisticated systems to recommend the best items to their users to make their experiences great. 

Prediction models for Budget vs Revenue based on the popularity of the movies are also defined.


<br>

## Content-based recommendation

1. Movie recommendations based upon Keywords  

The user gives a Movie Title as input and based on the keywords associated, the tool returns the top 10 movies.
![A screenshot of the result.](Images/Keywords_op.png)


2.  Movie recommendations for the user based on different genres based upon votes.
    
If a user has watched and liked several action movies, the recommendation system might suggest other action movies that have similar content and order by maximum votes received.

![A screenshot of the result.](Images/Genre_op.png)

3.  Movie Recommendations for the user on the basis of their mood.

Assuming the mapping of a user's mood per genre, the Tool recommends the movie ordered by votes 
*   Happy mood mapped to 'Comedy'
*   Sad mood mapped to 'Drama'
*   Excited mood mapped to 'Action'
*   Romantic mood mapped to 'Romance'
*   Scared mood mapped to 'Horror'

![A screenshot of the result.](Images/Mood_op.png)


4. Recommendations for cult-classics (High Rating, Low Budget) based on different genres.

Assuming a movie of rating 7.5 and votes at least above 100 defined the cult-classics recommended movies on the genre provided by the user.
  
![A screenshot of the result.](Images/cult_classic_op.png)

<br>

## Analysis of various factors for ROI (Revenue vs Budget)

![A screenshot of the result.](Images/ROI_op.png)

* The above heat map shows the budget, revenue, and popularity of the movies are highly correlated. 
* Also, vote counts for high ratings are being gathered for high-budget movies. 



<br>

## Machine Learning

Prediction models

The following prediction models are used in our analysis

* AdaBoostRegressor
* GradientBoostingRegressor

The above models were used to define a better accuracy of revenue predicted for a movie of a certain budget compared to the true historical revenue.

AdaBoost is the first designed boosting algorithm with a particular loss function. On the other hand, Gradient Boosting is a generic algorithm that assists in searching the approximate solutions to the additive modeling problem. This makes Gradient Boosting more flexible than AdaBoost.


<br>
Source Data

The source data files contain metadata for 45,000 movies listed in the Full Movie Lens Dataset. The dataset consists of movies released on or before July 2017. Data points include plot keywords, budget, revenue, release dates, languages, production companies, countries, TMDB vote counts, and vote averages.

The source data set is a comma-separated value (CSV) file. 

Cleaned up the columns not used in deriving recommendations and prediction analysis like id', 'original_title', 'production_companies', 'production_countries', 'status', 'tagline'.
Also removed an NA and converted the date fields like Release Date to data time format.


<br>
Train and Test data for models

The training and Test data set are divided in the random state to define the y set as 'revenue' and X against 'Budget' 'popularity'.


![A screenshot of the result.](Images/Models_Prediction.png)
 


AdaBoostRegressor Metrics:

    MSE: 8345049776798292.0
    RMSE: 91351243.98057364
    R2 Score: -0.8133629640768927

GradientBoostingRegressor Metrics:

    MSE: 1659001474115129.5
    RMSE: 40730841.80464638
    R2 Score: 0.6395022305470832

![A screenshot of the result.](Images/Models_compare.png)

Based on the results, it can be observed that the GradientBoostingRegressor model outperforms the AdaBoostRegressor model in terms of MSE, RMSE, and R2 Score. 

The MSE and RMSE values for the GradientBoostingRegressor model are significantly lower than the AdaBoostRegressor model, indicating that the GradientBoostingRegressor model provides more accurate predictions. 

The R2 Score for the GradientBoostingRegressor model is also significantly higher than the AdaBoostRegressor model, indicating that the GradientBoostingRegressor model explains more variance in the data.

<br>

## Conclusion

The tool provides recommendations for movies based on Keywords, genre, user's mood, and cult-classics per genre.

An analysis is performed for the ROI of budget vs revenue impact on the voting scores.

This tool also defines a prediction model to find what factors (budget and popularity vs revenue) correlate with the highest Return on Investment.



<br>

## Next steps

* Interface this tool in AWS for an interactive Chat Bot using Sage Maker, Lambda function, and Lex capabilities

* Enhance the tool with a live data set of user history to provide recommendations using search history, keywords, and movie reviews.

<br>

## References 

https://www.kaggle.com/datasets/rounakbanik/the-movies-dataset?datasetId=3405
