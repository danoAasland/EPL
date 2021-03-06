# EPL
EPL Season Predictor
Soccer Match Predictor will predict the result of each matches and the final standing of English Premier League 2018/2019 (EPL) using past five seasons (2013/14 ~ 2017/18) and Pro Evolution Soccer Database.
The final result will be evalutated by two methods.

# Methods
## Data Cleaning
1. Grab data from web (PES data, past seasons fixtures and tables) using BeautifulSoup.
2. Calculate Offensive and Defensive rate for each team in each seasons (using Poisson distribution).
3. Clean and merge all neccessary data.

## Predicting Result by Classification
### Modeling
1. Scores of each matches will be predicted using Poisson distribution (Match Based Rating).
    - How many goals will be scored in 90 minutes.
    - Evaluate teams' offensive and defensive rating. 
    - Average 38 games.   
2. Save probabilities.
3. Combine Match Based Rating from actual past season dats with Roster Based Rating from PES database.
    - EPL teams' overall stats from past database (www.football-data.co.uk, www.transfermarkt.co.uk, www.sportsmole.co.uk, www.soccerstats.com).
    - PES (Pro Evolution Soccer) database (www.pesmaster.com) to predict the result more accurately.
4. After combine MBR and RBR (Off. rating, Def. rating, Game data, etc.), train/test split five seasons (13/14 ~ 17/18) in order to fit models (Regression models to predict total points of all teams in EPL 18/19).
    - Tested models include: KNN, Logistic Regression, Random Forest, Bagging, Adaboost, Gradient Boosting, Voting Classifier.
    
## Predicting Result Using Poisson Distribution
### Modeling
1. Use poisson distribution in order to get how many goals each team will score in 90 minutes in a probability (https://fivethirtyeight.com/features/how-our-2018-world-cup-predictions-work/).
2. Get the total probability of the result (W/D/L probability).
3. Predict which team will win.

## Use Poisson Distribution as Features of Classification
### Modeling
1. Merge Poisson distribution's probability into EPL data and creat classification models.
2. Same as classification process, traint/test split the data.
3. Use GridSearchCV to find the best parameter.


# Visualization
## Plotly
1. Goals Scored/Goals Allowed vs. Final Points [plotly](https://plot.ly/~slee279/47/).
2. Team performance by season. [plotly](https://plot.ly/~slee279/49/).
3. Team standing by week season 18/19. [plotly](https://plot.ly/~slee279/51/).

## Matplotlib
1. Number of Goals Scored per Match. [link](https://github.com/slee279/EPL/blob/master/Assets/goaldistribution.png?raw=true)

## radviz
1. Classification EDA

# Assumptions
1. Goal scoring in soccer follows a Poisson process (90 minutes per game).
2. There's no transfers during season (after the new season has begun).
3. There's no injury.
4. Players conditions(fatigue level), weathers are the same.
5. There will be 272 matches per seasons between 17 teams. Promoted teams from the past seasons are not predicted.


# If time permits
1. Calculate the fatigue level (count days between matches).
2. Use each players rating to calculate more accurate team rating and use it as predicting feature.
3. Use Monte Carlo to Poisson distribution.

# Resource
https://fivethirtyeight.com/features/how-our-2018-world-cup-predictions-work/   
https://dashee87.github.io/football/python/predicting-football-results-with-statistical-modelling/  
www.football-data.co.uk   
www.transfermarkt.co.uk   
www.sportsmole.co.uk   
www.soccerstats.com   
www.pesmaster.com  
