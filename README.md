# Soccer-Outcome-Predictor

**Author**: Lucas Kimball

##  Overview

Predicting the outcome of a sports game?! That is impossible. Well... it is impossible to be perfectly accurate when predicting the outcome of sports, especially when the game is as low-scoring and random as soccer(football). That doesn't mean there isn't significant value in trying! An outcome prediction model for a soccer match has many use cases, whether for evaluating a team's performance, betting on matches, or on the sports media side providing context for fans. 

In this project, we explore different type of classification models and combinations of hyperparameters to find the best predictor.



## The Data

The data used in to train our model is taken from a variety of websites including [Football Reference(FBRef)](https://fbref.com/en/), [SofaScore](https://www.sofascore.com/), [Football-Data].uk(https://www.football-data.co.uk/), and [Club Elo](http://clubelo.com/). 

From FBRef, we scraped data of individual matches from the English Premier League over the last 6 premier league seasons, 17/18 through 22/23. From Club Elo we scraped the Elo ratings, which are updated every 4 days or so, of all the clubs in the EPL over the same time period. From Football Data UK we downloaded a file contain a compilation of odds for all matches over the same time period. Finally, From Sofa Score, we scraped individual player ratings for every match in our dataset. 
