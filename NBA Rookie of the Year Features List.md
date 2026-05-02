# NBA Rookie of the Year Features List

##### In this Markdown file, I will describe each of the features (axes to evaluate players on) which I use in my analysis to forecast the 2025-26 NBA Rookie of the Year. These are the columns which are fed into the random forest model that I am using to create my predictions. I will consider metrics which historically drive ROY voting, and plausible additional factors I am putting in to make my model excel in a unique way. 

## Section A: Core Features

####     Feature No.        |        Feature (column name)        |        NBA Stat ID / Source        |        Description (*Note everything is only through first 20 games)

##### 1 &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;| &emsp;&emsp;&emsp;&emsp;PTS_per_game &emsp;&emsp;| &emsp;&emsp;&emsp; PTS &emsp;&emsp;&emsp;| &emsp;Rookie’s average points per game

##### 2 &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;| &emsp;&emsp;&emsp;&emsp;REB_per_game &emsp;&emsp;| &emsp;&emsp;&emsp; REB &emsp;&emsp;&emsp;|&emsp;Rookie’s total rebounds average per game

##### 3 &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;|&emsp;&emsp;&emsp;&emsp;AST_per_game &emsp;&emsp;| &emsp;&emsp;&emsp;AST &emsp;&emsp;&emsp;| &emsp;&emsp;&emsp;&emsp;&ensp;" " &emsp;&emsp;&emsp;assists &emsp;" "

##### 4 &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;| &emsp;&emsp;&emsp;&emsp;STL_per_game &emsp;&emsp;| &emsp;&emsp;&emsp; STL &emsp;&emsp;&emsp;|&emsp;&emsp;&emsp;&emsp;&ensp;" " &emsp;&emsp;&emsp;steals &emsp;" "

##### 5 &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;| &emsp;&emsp;&emsp;&emsp;BLK_per_game &emsp;&emsp;| &emsp;&emsp;&emsp;BLK &emsp;&emsp;&emsp;|&emsp;&emsp;&emsp;&emsp;&ensp;" " &emsp;&emsp;&emsp;blocks &emsp;" "

##### 6 &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;| &emsp;&emsp;&emsp;&emsp;TOV_per_game &emsp;&emsp;| &emsp;&emsp;&emsp;TOV &emsp;&emsp;&emsp;|&emsp;&emsp;&emsp;&emsp;&ensp;" " &emsp;&emsp;&emsp;turnovers &emsp;" "

##### 7 &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;| &emsp;&emsp;&emsp;&emsp;MIN_per_game &emsp;&emsp;| &emsp;&emsp;&emsp;MIN &emsp;&emsp;&emsp;|&emsp; Rookie's average minutes per game (MPG) which is a proxy for opportunity/role

##### 8 &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;| &emsp;&emsp;&emsp;&emsp;PRA_per_game &emsp;&emsp;| &emsp;Calculated &emsp;|&emsp; (PTS+REB+AST) per game. A composite stat that some analysts argue is a better basic indicator of impact for rookies: https://www.nba.com/nbabet/nba-rookie-of-the-year-odds-picks-value-on-paolo-banchero-and-sleeper-bets-entering-the-new-season

## Section B: Context / Role / Exposure Features

####     Feature No.        |        Feature (column name)        |        NBA Stat ID        |        Description (*Note everything is only through first 20 games)

##### 9 &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;| &emsp;&emsp;&emsp;&emsp;GP_pct &emsp;&emsp;| &emsp;Calculated &emsp;| &emsp;Percentage of games a player played

##### 10 &emsp;&emsp;&emsp;&emsp;&emsp;| &emsp;&emsp;&emsp;Opp_metric &emsp;&emsp;| &emsp;Calculated &emsp;| &emsp;Opportunity metric measuring a rookie's playing time, role stability, availability, and team pace

##### 11 &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;| &emsp;&emsp;&emsp;Pick_no &emsp;&emsp;| &emsp;DRAFT_NUMBER &emsp;| &emsp;Rookie's draft pick number

## Section C: Labels (History Only)

##### 12 &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;| &emsp;&emsp;&emsp;&emsp;Voter_share &emsp;&emsp;| &emsp;Manually input from bball-reference &emsp;| &emsp;The final voting share for ROY from basketball-reference.com

## Section D: Unused Features for Future Advanced Modeling

##### *Note that I am not using these features in my model due to the imposed time constraint, however, if I were to spend (a lot) more time building this model, these may be features considered to drive a more advanced model. These columns are ones that I think are interesting and helpful, but would be too demanding for the given time frame.

####     Feature No.        |        Feature (column name)          |        Description (*Note everything would be only through first 20 games)

##### Would be 13 &emsp;&emsp;| &emsp;&emsp;&emsp;&emsp;TS_pct &emsp;&emsp;&emsp;&emsp;| &emsp;&emsp; &emsp;Shooting percentage with 3 pointers, 2 pointers, and free throws factored in together. Formula: Points/ [2*(Field Goals Attempted+0.44*Free Throws Attempted)]

##### Would be 14 &emsp;&emsp;| &emsp;&emsp;&emsp;&emsp;USG_pct &emsp;&emsp;&emsp;| &emsp;Percent of team plays which go through a player. Formula: 100*((Player’s Field Goal Attempts)+0.44*(Player’s Free Throw Attempts)+(Player’s Turnovers))*(Team’s Total Minutes)
/
((Team’s Total Field Goal Attempts)+0.44*(Team’s Total Free Throw Attempts)+Team’s Total Turnovers))*5*(Player’s Minutes)


##### Would be 15 &emsp;&emsp;| &emsp;&emsp;&emsp;&emsp;Plus_Min&emsp; &emsp;&emsp;| &emsp;The point differential of the game when the player is on the floor

##### Would be 16 &emsp;&emsp;| &emsp;&emsp;&emsp;&emsp;WS &emsp;&emsp;&emsp;&emsp;|  &emsp;Shares of wins a player contributes on defensive possessions

##### Would be 17 &emsp;&emsp;| &emsp;&emsp;&emsp;&emsp;REB_pct &emsp;&emsp;&emsp;| &emsp;Percentage of available rebounds a rookie grabbed while on the floor

##### Would be 18 &emsp;&emsp;| &emsp;&emsp;&emsp;&emsp;VORP&emsp;&emsp;&emsp;&emsp;| &emsp;Value over replacement player

##### Would be 19 &emsp;| &emsp;&emsp;&emsp;&emsp;PER &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;|  &emsp;Rookie's Player Efficiency Rating calculated via John Hollinger's: https://www.basketball-reference.com/about/per.html

##### Would be 20 &emsp;| &emsp;College_performance_metric &emsp;|  &emsp;Rookie's college/professional performance last year (all translated to one relative scale)

##### Would be 21 &emsp;| &emsp;&emsp;&emsp;&emsp;Rem_SOS &emsp;&emsp;&emsp;&emsp;|  &emsp;The team's remaining strength of schedule (may indicate if rookie's stats will increase/decrease over rest of season) <-- would be interesting to add another factor including the remaining schedule teams' current defensive rating since ROY is highly driven by offensive production

##### Would be 22 &emsp;| &emsp;&emsp;&emsp;&emsp;Hype &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;|  &emsp;A catch-all sentiment score index for how the internet is currently talking about the rookie (eg. tweet quantity & sentiment, article sentiment written by NBA ROY voters, etc.)

##### Would be 23 &emsp;| &emsp;&emsp;&emsp;Injury_risk &emsp;&emsp;&emsp;&emsp;|  &emsp;Estimate of the likelihood a rookie gets injured based on their health history, historic league trends, and amount of remaining back-to-back/taxing games

##### Would be 24 &emsp;| &emsp;&emsp;&emsp;Win_pct_diff &emsp;&emsp;&emsp;|  &emsp;The difference in percentage between the expected wins (from sportsbook lines/82 game season) versus actual win percentage for the rookie's team <-- may measure if the rookie is helping them win more than expected
