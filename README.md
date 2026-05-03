📌 Overview  
This project uses a supervised machine learning (ML) model called a Random Forest Algorithm (RFA) to forecast who will win the NBA Rookie of the Year (ROY) for the 2025-26 season. The goal is to create a full list of likelihoods corresponding to each rookie's chance of winning the award at the end of the season. The project was created in early December and finalized on 12/3/25.    

🎯 Objectives  
• Train a RFA on simple, easily accessible NBA data going back to the 2010-11 season.   
• Predict voter behavior through ML, increasing understanding of what matters for ROY voters.  
• Forecast each rookie's chance of winning, just through the early part of the season (first ~20 games).   
• Verify the model's strengths, and contribute to modern sports analytics through unique data analysis.   

🧠 Approach  
Phase 1. Data Acquisition and Management  
I acquired the necessary data for this project from the NBA Stats API: https://github.com/swar/nba_api/tree/master (posted by Swar Patel and others). I accessed LeagueDashPlayerStats and CommonPlayerInfo and merged them into a common dataset in order to have both the on court production and off-court numbers available. I performed data unification meticulously, and coded in some data correction, like recording undrafted players as if they were picked with the 61st overall pick.     

Phase 2. Feature Engineering  
I would have loved to include some advanced stats, or even more off-court stats, but the restriction of only using data from this NBA API meant that the included features are relatively simple. The Final Features are described as such (keep in mind this data corresponds to only the first 20 games of the season):  
• PTS [points per game]  
• REB [rebounds per game]  
• AST [assists per game]  
• STL [steals per game]  
• BLK [blocks per game]  
• TOV [turnovers per game]  
• MIN [minutes per game]  
• PLUS_MINUS [for the minutes the rookie was on the court, what is the difference between their team's change in score minus the other team's change in score]  
• PRA [calculated: PTS + REB + AST emphasizing the importance of simple box score stats for voters]  
• GP_pct [calculated: how many games has the rookie played so far out of how many games their team has played]  
• Opp_met [calculated: MIN * GP_pct * (1+(PLUS_MINUS)/10). A simple metric to estimate how much opportunity the player will receive in the rest of the season]  
• DRAFT_BUCKET [Draft position number if the player was picked in the lottery (1-14), and equal to 15 otherwise to de-emphasize distinction between someone picked between the 41st and 42nd picks, for example.]  


Phase 3. Model & Model Evaluation    
• For the model, I used scikit-learn's RandomForestRegressor. The parameters used are fairly standard, and not too much tinkering was done after seeing the simple model achieve a reasonable result.   
• The model is trained on voter output instead of simply who won the award. This better measures the various reasons a rookie may receive votes, which is important for giving each current rookie a final probability (instead of just measuring their chances of finishing exactly first). 
• The final output is stored in ./predictions.csv with each current rookie name and winning probability.   
• For the model evaluation, the following statistics were recorded:  
    • MAE = 0.01961. This corresponds to a mean absolute error of ~2% (vote share error), which is quite low, and the model is therefore accurate.   
    • R^2 = 0.06905. ~7% of the final voting being explained by variance in my features doesn't sound great, yet is fine considering that ROY voting is noisy, and narrative-driven. Being only based on players' on court, start of year stats, this is expected to be somewhat low. The more important metric for creating a ranked list of players is the nest one.   
    • Spearman rank = 0.319. This mean's the model puts the right players at the top of the list a reasonable amount of the time.   

💪 Example Outputs (in ./predictions.csv)       
   PLAYER NAME         PROBABILITY
1. Cooper Flagg          0.284689    
2. Kon Knueppel          0.269926  


🚀 Future Improvements  
• Include advanced metrics which signify player impact potentially leading to more team wins.   
• Include predictions on who specific voters will favor.  
• Quantify and train on off-court values: narrative sentiment, social media buzz, etc.  
• Include a function which analyzes injury probabilities.  


💻 How to Run & Tech Used  
• Download the .ipynb file (Eric Rumsfeld's Official ROY Projection Statistical Model.ipynb) and the two .csv files (historic_rookies & rookies_2025_26)  
• Open the .ipynb file in Python and feel free to run or tweak as you wish. Much of the data management was already completed and is therefore commented out, so you don't need to uncomment things to get the code going.   


🏁 Takeaways  
• The top 3 players in final ROY voting from this year were predicted exactly in order. They ended up getting 99.33% of the votes. This shows ROY forecasting can be completed accurately, even from a very simplistic model.  
• I learned more about model analysis, and what kinds of statistics should be deployed in different ML projects to really understand model performance.  
• For winning the NBA ROY, there's nothing more predictive than having the ball in your hands, and being featured a lot as an important/winning part of the team.  
• I hope to build more novel sports analytics data solutions like this one in exciting upcoming projects!  


      
👤 Author  
Eric Rumsfeld  
M.S. in Astronomy | Data Science & Sports Analytics  

