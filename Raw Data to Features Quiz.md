1. What are the characteristics of a good feature?
* __Related to the objective__
* __Knowable at prediction time__
* __Have enough examples in the data__
* Be in free-text format
* __Be numeric with meaningful magnitude__
_____________________________________________________________________________________________________

2. I want to build a model to predict whether Team A will win its basketball game against Team B. I will train my model on features computed on historical basketball games. One of my features is how many games this season Team A has won. How should I compute this feature?

* Compute num_games_won / num_games_played over the whole season
* __Compute num\_games_won / num\_games\_played until the N-1 th game in order to train with the label for the N th game__
* Compute num\_games\_won / num\_games\_played until the N th game in order to train with the label for the N th game
_____________________________________________________________________________________________________

3. I want to build a model to predict whether Team A will win its basketball game against Team B. Which of these attributes (computed on historical basketball games) are good features? Assume that these features are all computed appropriately without taking into account non-causal data.
* __How often Team A wins games__
* __How often Team A wins games where its opponent is ranked in the top 10__
* __How many of the last 7 games that Team A played that it has won__
* The fraction of games that Team A won when it played against Team B when both teams had this exact set of players


