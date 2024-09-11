# Soccer Outcome Predictor

**Author**: Lucas Kimball

# Data Source

The data is taken from FBREF, ClubElo, Footballdata.uk, and gamemodelsfootball.com.

## Modeling

For our modeling we iterated through a series of different models and hyperparameters, settling on an ensemble of tuned XGboost, Random Forest, and linear regression models. Our goal was to get the most accurate distribution of predicted probabilities for a match, so picking a scoring method was not straightforward, especially due to the nature of the 3 potential outcomes. We looked at accuracy, ROC AUC, Log loss, and Mean Brier Score-- generally defering to ROC AUC score when different iterations of the model were close otherwise.

## Results

Our best model had the below scores:

accuracy: 0.61
ROC AUC Score (Calibrated Ensemble): 0.7109
Log Loss (Calibrated Ensemble): 0.9087
Mean Brier Score (Calibrated Ensemble): 0.1766

Different iterations of this model have returned very different outputs following the input of the predicted probabilities into  different betting strategies. Many have returned profit, many have not- such is the nature of back-testing.

## Next Steps

The next addition to this model-  if my computer doesnt crash taking 3 days to pull lineup data- is integrating time decay MBAPPE (or other EPM models). Currenting I am using a lineups cumulative MBAPPE from the past season, however this is quite flawed and could very easily be improved using a time decay method- or even just using the current season's MBAPPE(if it was publicly available)
