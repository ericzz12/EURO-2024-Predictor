## EURO-2024-Predictor
### Project Description
This project predicts the match results of the EURO 2024 football matches. It uses the Random Forest Classifier by Scikitlearn and trains on data from qualifying matches. This data is scraped from fbref.com using the Requests and BeautifulSoup libraries.  

TeamDataScraper.ipynb scrapes team specific data for the matches played by each participating country (shots, fouls, etc.) and saves it in matches.csv. The predictions are done in ModelTrainer.ipynb, which takes the data for qualifying matches combined with team specific data for each match from matches.csv to train a Random Forest Classifier to predict the winner of each match. 

### Machine Learning Method
The Random Forest Classifier is trained on qualifying matches before November 2023 and tests on the remaining qualifying matches from November 2023 onwards. This gives approximately a 80%-20% split in the training and testing set. The model must train on numeric data, so some of the predictors need to be converted to numeric types. Also, rolling averages for some match stats are calculated for each team using their past games to be used as predictors. Unfortunately, there is no data for Germany because they automatically qualify for the EUROs as the host, so they have no qualifying matches.  

List predictors used:
- Time of game
- Day of the week of game
- Home and away team
- Rolling averages of past 3 games for:
  - Goals scored
  - Goals against
  - Possession
  - Shots
  - Shots on target
  - Yellow cards
  - Fouls
  - Fouls drawn
  - Crosses
  - Interceptions
  - Tackles won

The model's predictions for the EURO match results are at the end of ModelTrainer.ipynb.  
