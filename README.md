# BeerReviewPrediction
This repository includes all files related to my final project deployed at Coderhouse´s Data Science course.

## Objective
We are trying to predict beer review overall from customers. We suspect beer features have some type of relation with their review overall score. In this effort we are looking for improvements on production, sales and consumption decisions.

## Dataset information
Data facts:
* 3197 beer reviews
* 934 breweries
* Features describing general profiles: Name - Style - ABV - Min./Max. IBU.
* Features picturing specific profiles: Body - Malty - Fruits - Hoppy... These were built counting words found on at least 25 reviews or more, adding 1 point for each word related to the feature. For more information, please visit (https://github.com/JulianHorvath/BeerReviewPrediction/blob/main/Beer%20Descriptors%20Simplified.xlsx) 
* Review features: review overall - review taste - review palate - review aroma - review appearance. They are on a scale from 1 to 5, being the average of beer reviews. 

Sources: 
* Kaggle [https://www.kaggle.com/datasets/ruthgn/beer-profile-and-ratings-data-set]
* BeerAdvocate [https://www.beeradvocate.com/community/threads/how-to-review-a-beer.241156/]

## Methodological warning
* Features picturing specific beer profiles lack of standarization. Subjective descriptions would add noise to the model so, previous visual data analysis and statistical tests, were discarded.
* Review variables come from a Likert scale. Aware of some theoretical discussions, we accepted some limitations and work with them, refining insights and overall data analysis.
* Dataset were filtered by beers with at least 25 reviews.

## Results

* Multiple Linear Regression had an outstanding performance on test stage, reaching out 0.93 of R squared and the following error metrics: MAE=0.0267, MSE=0.0011, RMSE=0.0338.
* Support Vector Regressor (SVR) was the other model with a great performance. It had 0.91 of R squared and the next error metrics: MAE=0.0306, MSE=0.0014, RMSE=0.0374.
* All models improved their error metrics significantly when data is normalized before testing. This is a key aspect for a compressed scale as Likert scale: we had to minimize the errors as much as we could. Zone with major variability was condensed under 3.
* We isolated major error zone and retested models. Picking out MSE as primarly error metric to penalize deviations, we found out Multiple Linear Regression (0.0034) and SVR (0.0029) were again the best performers, after normalizing input data.

## Insights
### Business insights
* Number of reviews does not have a strong relation with beer's review overall.
* However, beers with more than 550 reviews have a better shot for a highlighting review overall.
* Descriptive features best rated by reviewers were Malty and Sweet.
* Average beers are between 3.5 and 4.25 review overall score.
* Outstanding beers are above 4.25 review overall score. "Bad" beers standed between 3 and 3.5, while awful beers were below 3 review overall score.

### Methodological insights
* Filtering dataset excluding most reviewed beers, as an outliers preprocessing, does not modify correlations between variables. In fact, it changes target feature distribution, so it is not recommended.
* Grouping descriptive features on a single feature does not generate strong correlations, neither lineal nor no-lineal. This does not work also if we previously do feature selection.
* That also applies for feature engineering by business criteria (grouping by dimensions like mouthfeel, taste and flavor&aroma).

## Final considerations: business impact
* Review overall of products/services can be predicted disintegrating reviews in more specific dimensions.
* This focus on consumption sensorial experience. General evaluating always requires some abstraction level that is not the aim of reviews.
* On beer experience specifically, it is more important palate than appearance or aroma.
* With some limitations, our model could be useful for all economic models based on reviews, from deliveries to on demand platforms enterprises, just for mentioning some famed examples.
