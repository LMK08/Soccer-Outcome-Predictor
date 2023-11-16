# Soccer-Outcome-Predictor

**Author**: Lucas Kimball

##  Overview

Predicting the outcome of a sports game?! That is impossible. Well... it is impossible to be perfectly accurate when predicting the outcome of sports, especially when the game is as low-scoring and random as soccer(football). That doesn't mean there isn't significant value in trying! An outcome prediction model for a soccer match has many use cases, whether for evaluating a team's performance, betting on matches, or on the sports media side providing context for fans. 

In this project, I explore different types of classification models and combinations of hyperparameters to find the best predictor and then apply the results of the model to develop a profitable betting model.



## The Data

The data used to train our model is taken from a variety of websites including [Football Reference(FBRef)](https://fbref.com/en/),[Football-Data].uk(https://www.football-data.co.uk/), and [Club Elo](http://clubelo.com/). 

From FBRef, I scraped data of individual matches from the English Premier League over the last 6 premier league seasons, 17/18 through 22/23. From Club Elo I scraped the Elo ratings, which are updated every 4 days or so, of all the clubs in the EPL over the same time period. From Football Data UK I downloaded a file contain a compilation of odds for all matches over the same time period. In total the dataset contained 2280 matches.

After combining the data sets and engineering features, as well as removing some unhelpful features, I was left with the following features:

- referee                     
- home_team_elo               
- away_team_elo                
- home_xG_to_date              
- away_xG_to_date             
- home_xG_against_to_date      
- away_xG_against_to_date      
- home_goals_scored_to_date    
- away_goals_scored_to_date    
- home_goals_conceded_to_date  
- away_goals_conceded_to_date  
- home_points_to_date           
- away_points_to_date         
- home_form                    
- away_form
- Pinnacle Closing Home Win Odds  
- Pinnacle Closing Draw Odds
- Pinnacle Closing Away Win Odds  
- home_team
- away_team

## Machine Learning Modeling

I used a series of different machine learning models as set to the task of classifying the outcome of a soccer match as win, loss, or draw. I started training models using strictly the numeric features to get a baseline using a simple Logistic Regression classifier model. Next I created a pipeline to iterate through an ensemble of models and a series hyperparameters including:
- Logistic Regression
- Random Forest
- XGBoost
- CatBoost

The CatBoost model performed the best on the numeric data with an F1 score of .454. As CatBoost has the additional benefit of being able to interepret the categorical features in my dataset without have to one hot encode, I proceeded with using this type of model. 

The additional of the categorical features: referee, home_team, and away_team, as well as further tuning bumped the F1 score up to .469. Through further evaluation of the results, this score is brought down signficantly by the accuracy of predicting draws. The model does a good job of predicting away wins at a .603 accuracy, and a fantastic job of predicting home wins, .759 accuracy, but a terrible job of predicting draws, at tiny .018 accuracy score.

It is also important to extract the feature importance for this type of model. For this model, home and away team elo ratings were 2 of the top 3 features in terms of importance, which checks out, as elo rating is supposed to be a rolling value for the strength of a team. Interestingly, home and away form are also two of the more signficant features, indicating that form or hot streaks may not only exist, but matter more than a teams current position in the table.

## Applying the ML Results to Betting

In order to apply the model's results to betting, we need to extract all the probabilities for the test set. This means that for each match in the test set(456 total), we have a probability of home win, draw, or away win.

Next, we calculate the Expected Value(EV) for every outcome. So what is expected value? It is define as the average profit from a bet, given a stake. So if you re-ran a bet an infinite number of times, the EV would be your profit. For our data there are three possible outcomes for each match this leaves us with 1368 Expected Values. Most of the time, if the book makers are good at their jobs, it is hard to find positive EV bets. The formula for EV is as follows: 

(probability of winning the bet * (betting odds * stake))-(probability of losing the bet * stake)

I simulated two betting strategies, calculating the profit and return on investment for each(ROI). The first strategy involved betting $10 on every positive EV outcome, of which there are 611. Our total profit from this strategy was $2263.79, giving us a 37.05% ROI. This strategy also had a 46.7% win rate per match, meaning that we turned a profit on that percentage of matches that we bet on. The second strategy was to bet $10 on only the best EV outcome per match, which meant 456 total bets. Our total profit was $1948.30, albeit on a smaller total stake, giving us a 43.10% ROI.  This strategy also had a 38.8% win rate per match.







