# NBA Defense Analysis (2021-2024)

## Overview
This project investigates the popular sports adage “Defense wins championships” by analyzing NBA team performance from 2021 to 2024. Specifically, it examines the relationship between defensive metrics and team success in both the regular season and postseason, while comparing these to offensive metrics.

## Data
- **Source:** Basketball Reference (Advanced Stats)  
  - [NBA 2021 Regular Season Stats](https://www.basketball-reference.com/leagues/NBA_2021.html)  
  - [NBA 2021 Playoff Stats](https://www.basketball-reference.com/playoffs/NBA_2021.html)  
  - [NBA 2022 Regular Season Stats](https://www.basketball-reference.com/leagues/NBA_2022.html)  
  - [NBA 2022 Playoff Stats](https://www.basketball-reference.com/playoffs/NBA_2022.html)  
  - [NBA 2023 Regular Season Stats](https://www.basketball-reference.com/leagues/NBA_2023.html)  
  - [NBA 2023 Playoff Stats](https://www.basketball-reference.com/playoffs/NBA_2023.html)  
  - [NBA 2024 Regular Season Stats](https://www.basketball-reference.com/leagues/NBA_2024.html)  
  - [NBA 2024 Playoff Stats](https://www.basketball-reference.com/playoffs/NBA_2024.html)  

**Training set:** 2021–2023 seasons  
**Test set:** 2024 season  

**Response variables:**  
- Regular season wins (max 82)  
- Postseason wins (max = 16)  

**Predictor variables:**  
- **Defensive Rating (DRtg):** estimated points allowed per 100 possessions  
- **Offensive Rating (ORtg):** estimated points scored per 100 possessions  
- **Advanced defensive metrics:**  
  - Opponent Effective Field Goal %  
  - Opponent Turnover %  
  - Defensive Rebound %  
  - Opponent Free Throws per Field Goal Attempt  

All predictors were drawn from regular season data, with regular season wins (model 1) and playoff wins (model 2) as the outcome variables.

## Methodology
- **Data Cleaning & Storage:** CSVs uploaded to SQL Server Management Studio. Combined 2021-2023 for training; 2024 reserved for testing.  
- **Exploratory Analysis:** Correlation matrices and scatterplots using Pandas and Seaborn.  
- **Modeling:** Linear regression models to assess the predictive power of defensive and offensive metrics.  

**Modeling Setup:**  
- **Regular Season Wins (all teams):**  
  - Model 1.1: DRtg → Wins  
  - Model 1.2: Advanced defensive metrics → Wins  
  - Model 1.3: DRtg + Advanced metrics → Wins  
  - Model 1.4: ORtg → Wins  

- **Playoff Teams – Regular Season Wins:**  
  - DRtg → Wins  

- **Postseason Wins (playoff teams only):**  
  - Model 2.1: DRtg → Playoff Wins  
  - Model 2.2: Advanced metrics → Playoff Wins  
  - Model 2.3: DRtg + Advanced metrics → Playoff Wins  
  - Model 2.4: ORtg → Playoff Wins  

## Results
**Regular Season Wins (R² values):**  
- Model 1.1 (DRtg, all teams): 0.586, simple but strong predictor  
- Model 1.2 (Advanced metrics): 0.628, only slightly better than 1.1  
- Model 1.3 (DRtg + Advanced metrics): 0.631, marginal gain over 1.1 and 1.2  
- Model 1.4 (ORtg): 0.737, best predictor of regular season wins among tested variables  

**Playoff Teams – Regular Season Wins (R²):**  
- DRtg: 0.346: some explanatory power but weaker than full league  

**Postseason Wins (R² values):**  
- Model 2.1 (DRtg): 0.007 very weak result  
- Model 2.2 (Advanced metrics): -0.033 even weaker than just D rating  
- Model 2.3 (DRtg + Advanced metrics): -0.093, no noticeable improvement on model 2.1  
- Model 2.4 (ORtg): 0.147, Again, offense fairs as the best predictor of winning  

**Key Takeaways:**  
Across all teams, team defensive rating predicts regular season wins nearly as well as the more complex 4-stat model. For playoff teams, defensive rating alone outperforms the advanced metrics model, although both are very poor predictors for post season wins. Offensive rating is the strongest predictor of regular season success. Postseason success is largely unpredictable from regular season metrics; offense shows a slight advantage.  

## Conclusions
- **Regular season success:** Simple defensive rating (DRtg) is nearly as effective as a more complex 4-stat model. Offense remains the strongest predictor.  
- **Playoff teams:** Advanced defensive metrics do not improve prediction; DRtg alone is superior.  
- **Postseason success:** Neither simple nor complex defensive models provide meaningful predictive power; offense is slightly better but limited.  

**Insight:** Simpler models can perform nearly as well as complex ones for regular season wins, and added complexity may reduce predictive power in smaller, high-performing subsets like playoff teams.  

## Future Work
- Expand dataset to include more seasons or higher level statistics  
- Incorporate player-level or lineup-level statistics to capture the effect of team construction and defensive schemes on success  


