# Capstone_VideoGameRetention
Using a selection of ML models to predict whether someone is going to retain for 7 days in a video game. This is the submission for the Capstone Project of the UC Berkley Machine Learning and AI course

### Project Executive Summary: Player Retention Predictive ###
Objective: To identify key gameplay "hooks" that predict whether a new player will remain active for at least 7 days, allowing the team to focus development on features that actually drive long-term engagement.

Key Findings
Top Performer: The Random Forest model emerged as the champion, achieving an 82.5% Precision rate.

Reliability: When the model flags a player as "likely to stay," it is correct 8 out of 10 times.

Primary Drivers: Gameplay metrics like Quest Starts and Group Participation were significantly more predictive of retention than simple time spent in-game.

Technical Strategy
Data Integrity: Implemented a strict "Split-Before-Scale" workflow to ensure the model generalizes well to future, unseen players.

Feature Engineering: Utilized Logarithmic Transformations to handle "Whale" players (extreme outliers) and created Actionable Feature Sets that exclude metrics developers cannot directly control (like date of join). We also had to clean the data before it went to the model which included handling
missing values and assigned numerics to days of the week as standard in ML pipelines

Optimization: Conducted a Triple-Model Grid Search (Logistic Regression, Random Forest, and XGBoost) specifically tuned to maximize Precision over raw accuracy.

### Data Sources

The data set used for this project was taken directly from our Video games telemetry that has been tracking players over the last 2 years. It contains 500,000 accounts and 33 feature columns. 
Each feature column represents a different potentual activity in the or how fast they achieved and activity. I used a test set of 30% to make this model. 

Link to notebook:

http://localhost:8888/notebooks/Berkley/CapStone3.ipynb?

## Results: ##

We were looking for Precision as our key attribute for our model to have. We want the model to be correct when picking attribute to make new features on. 

## Model Performance Comparison

After performing a Grid Search optimized for Precision, the following results were achieved on the unseen test set. The **Random Forest** model emerged as the best model for high-fidelity predictions.

| Model | Test Precision | Test Recall | Test F1-Score |
| :--- | :---: | :---: | :---: |
| **Random Forest** | **0.8270** | 0.6707 | **0.7407** |
| Logistic Regression | 0.5471 | 0.9043 | 0.6817 |
| XGBoost | 0.5007 | **0.9291** | 0.6507 |

---

## Key Insights
* **Precision Favorite:** The **Random Forest** model is highly reliable, with an **82.7% Precision** rate. This means that when the model predicts a player will be retained, it is correct over 8 times out of 10.
* **The Trade-off:** While **XGBoost** and **Logistic Regression** achieved higher Recall (identifying more retained players overall), they suffered from a high rate of "False Alarms," making them less ideal for targeted, high-cost interventions.
* **Actionability:** By prioritizing Precision, we ensure that any retention strategies (like specialized offers or push notifications) are directed toward the players most likely to actually engage, minimizing "marketing fatigue" and wasted resources.

Random Forest was the best model by far for this task of the 3 models.

By calculating the Feature Importance we can now deliver the message to the game team that Quest Starts, Total Gold Earned and Total Itews Earned are the main contributors to being retained 
which is invaluable information to a game designer. 

## Next Steps  <br>
By deploying this model, the studio can now accurately identify high-value players early in their journey. This allows for Precision Marketing—targeting the right players with rewards or social invites without wasting resources on players who were likely to stay regardless.
