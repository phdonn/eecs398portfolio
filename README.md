# Predicting Match Outcomes in League of Legends: A Data-Driven Approach

# Introduction

This project analyzes professional League of Legends match data to understand the factors influencing match outcomes. The dataset includes detailed game statistics, and the analysis focuses on the relationship between gold difference at 25 minutes (`golddiffat25`) and match outcomes (`result`).

## Data Cleaning Steps and Exploratory Data Analysis

The dataset originally contained 116,064 rows and 161 columns. The `golddiffat25` column, which represents the gold difference at the 25-minute mark, had 23,520 missing values, while the `result` column had no missing values. Rows with missing values in `golddiffat25` were dropped because this column is critical for analysis, reducing the dataset to 92,544 rows. Both `golddiffat25` and `result` columns were converted to numeric data types to ensure compatibility with analytical methods. The cleaned dataset now includes only complete data, ensuring the results are accurate and reliable.

The data cleaning process significantly impacted the analysis by removing incomplete data points that could have introduced errors. Although the dataset size was reduced, this step preserved the integrity of the results.

### Cleaned Data Head

```plaintext
   golddiffat25  result
180        1928.0       1
181        2943.0       1
182         660.0       1
183        5016.0       1
184        2194.0       1
```

### Univariate Analysis

A histogram was created to visualize the distribution of the `golddiffat25` column. The gold difference at 25 minutes shows a roughly normal distribution centered around zero, with most values falling between -5,000 and 5,000. This distribution suggests that most games are balanced around the 25-minute mark, with extreme gold advantages or disadvantages being relatively rare. This finding highlights the competitive nature of League of Legends matches and suggests that small gold advantages can significantly influence outcomes.


### Bivariate Analysis

The relationship between `golddiffat25` and `result` was analyzed using a scatter plot and a box plot. The scatter plot demonstrated a moderate positive trend, indicating that higher gold differences are generally associated with winning outcomes. The box plot showed a clear distinction in the gold difference distributions for wins and losses. Teams that win matches (`result = 1`) tend to have positive gold differences, while teams that lose (`result = 0`) tend to have negative or neutral gold differences. This analysis confirms that early-game gold leads play a critical role in determining match outcomes. Both graphs have more detailed analysis further down. 

### Aggregate Statistics

The dataset was grouped by match outcome (`result`), and the mean gold difference for each outcome was calculated. Teams that won their matches had an average gold lead of 1,511.96, while losing teams had an average gold deficit of -1,511.96. This significant difference reinforces the idea that gold advantage at 25 minutes is a key indicator of success in League of Legends matches.

### Grouped Table

```plaintext
   result  golddiffat25
0       0  -1511.962828
1       1   1511.962828
```

### Missing Value Handling

Missing values in the `golddiffat25` column were handled by dropping rows where this column was `NaN`. This approach ensured that only complete and accurate data points were used in the analysis. Imputation was not performed because the gold difference is a key feature, and approximating its values could have introduced bias into the results.

### Univariate Analysis
A histogram was created to visualize the distribution of the golddiffat25 column. The gold difference at 25 minutes shows a roughly normal distribution centered around zero, with most values falling between -5,000 and 5,000. This distribution suggests that most games are balanced around the 25-minute mark, with extreme gold advantages or disadvantages being relatively rare. This finding highlights the competitive nature of League of Legends matches and suggests that small gold advantages can significantly influence outcomes.

<iframe
  src="assets/gold_difference_histogram.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

### Gold Difference vs Match Outcome

<iframe
  src="assets/gold_difference_vs_match_outcome.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

This scatter plot visualizes the relationship between the gold difference at 25 minutes (`golddiffat25`) and the match outcome (`result`), where the outcome is represented as a binary variable:
- `1` indicates a win,
- `0` indicates a loss.

### Insights from the Graph:
1. **Positive Correlation Between Gold Difference and Winning**:
   - Matches with a positive gold difference at 25 minutes (greater than 0) are overwhelmingly associated with winning outcomes (`result = 1`).
   - This supports the idea that early gold advantages significantly improve a team's chances of securing victory.

2. **Negative Gold Differences Correlate with Losses**:
   - Teams with a negative gold difference at 25 minutes (less than 0) are more likely to lose (`result = 0`).
   - This suggests that deficits in gold by the mid-game are difficult to recover from.

3. **Distribution of Gold Differences**:
   - Most data points are clustered near the 0 mark on the `golddiffat25` axis, reflecting that many matches remain relatively close at the 25-minute mark.
   - However, extreme cases of gold differences (both positive and negative) are associated with their respective outcomes more definitively.

4. **Implications for Competitive Play**:
   - The analysis highlights the importance of securing a gold lead by the 25-minute mark in League of Legends matches.
   - Teams should focus on early-game strategies such as effective farming, successful skirmishes, and objective control to achieve a gold advantage and increase their chances of winning.

### Context of the Study:
This graph aligns with the central hypothesis of our study: **Gold differences at 25 minutes play a crucial role in determining match outcomes.** By identifying this trend, we gain insights into the dynamics of professional and competitive League of Legends games, emphasizing the critical impact of mid-game performance.

The scatter plot reinforces that a team's ability to secure an economic advantage early on often translates into tangible success, underscoring the significance of mid-game strategies in shaping match results. This is particularly valuable for teams aiming to refine their gameplay and for analysts studying match dynamics.


## Gold Difference Distribution
<iframe
  src="assets/gold_difference_distribution.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

##### This graph provides a clear comparison of the distribution of gold differences at the 25-minute mark (`golddiffat25`) for winning (`result = 1`) and losing (`result = 0`) teams in League of Legends matches. The calculated correlation between golddiffat25 (gold difference at the 25-minute mark) and result (match outcome) is 0.478. This indicates a moderate positive correlation between the two variables. Here's an analysis of what the graph tells us:
---

#### 1. **Gold Difference Patterns for Winners and Losers**
   - The box for winning teams (`result = 1`) is entirely above the zero line, indicating that winners tend to have **positive gold differences** at the 25-minute mark.
   - Conversely, the box for losing teams (`result = 0`) is centered below zero, showing that losers often have **negative or neutral gold differences**.

---

#### 2. **Spread of Gold Differences**
   - **Winning Teams**:
     - The range of gold differences is tighter, with fewer outliers, suggesting that a moderate lead at 25 minutes is often sufficient to secure a win.
   - **Losing Teams**:
     - The range is much broader, with some teams experiencing large negative deficits, highlighting the potential for one-sided games.

---

#### 3. **Median Gold Difference**
   - The median for winners is significantly above zero, emphasizing that even a small gold advantage at 25 minutes tends to correlate with a win.
   - For losers, the median is slightly below zero, suggesting that even small deficits in gold can be detrimental.

---

#### 4. **Outliers**
   - There are extreme cases where teams with very high or very low gold differences deviate significantly from the typical distributions. These outliers might represent games with unusual dynamics, such as snowballing leads or major comebacks.

---

#### Implications for the Study
This graph reinforces the critical role of mid-game performance in determining match outcomes. It shows that achieving a gold lead by the 25-minute mark is not just advantageous but often essential for victory. The tighter and more positive distribution for winners underscores that teams must focus on early-game strategies to secure a stable advantage, while the broader range for losing teams suggests the difficulty of recovering from a deficit.

## Conclusion

This analysis highlights the importance of early-game gold advantages in League of Legends. The findings suggest that teams with a higher gold difference at 25 minutes are significantly more likely to win. This insight provides valuable strategic implications for teams and fans alike, emphasizing the importance of early-game performance in professional play.


# Framing a Prediction Problem

## Problem Statement
The prediction problem involves determining whether a team will win (`result = 1`) or lose (`result = 0`) a League of Legends match based on in-game metrics available at the 25-minute mark. This is a **binary classification problem**, as the response variable (`result`) has two possible outcomes: win or loss. 

## Response Variable
The response variable is `result`, which indicates whether a team won (`1`) or lost (`0`) the match. This variable was chosen because it represents the ultimate outcome of the game, and understanding how early-game metrics impact this outcome can provide valuable insights for strategy development.

## Features
The features used to train the model include:
1. **`golddiffat25`**: Gold difference at the 25-minute mark (quantitative).  
2. **`xpdiffat25`**: Experience difference at the 25-minute mark (quantitative).  
3. **`killsat25`**: Number of kills achieved by the team at the 25-minute mark (quantitative).  
4. **`deathsat25`**: Number of deaths suffered by the team at the 25-minute mark (quantitative).  

These features were chosen because they represent in-game performance metrics available at the time of prediction. They are critical indicators of early-game dominance, which strongly influences match outcomes.

## Metric for Model Evaluation
The primary metric used to evaluate the model is the **F1-score**, which balances precision and recall. This metric was chosen over accuracy because of the potential imbalance in the dataset, where some outcomes (e.g., wins or losses) may occur more frequently than others. The F1-score ensures that the model performs well in predicting both classes without favoring the majority class.

## Justification for Features
All features included in the model are based on information available at the 25-minute mark, ensuring they are valid for prediction. This aligns with the temporal constraints of the problem, as only data up to 25 minutes into the game is used to predict the outcome. Metrics that would only be available after the match ends (e.g., final kills or gold totals) were excluded to avoid data leakage.

## Why This Problem Matters
This prediction problem provides actionable insights into the importance of early-game performance in competitive League of Legends. By predicting match outcomes based on early-game metrics, teams can identify critical areas to improve their strategies and optimize their chances of success.

### Baseline Model Description

# Model Description
The baseline model used is a **Logistic Regression Classifier** implemented within a scikit-learn `Pipeline`. Logistic regression is well-suited for this binary classification task as it predicts the probability of a team winning (`result = 1`) or losing (`result = 0`). The pipeline ensures all preprocessing steps, such as feature scaling, are integrated seamlessly with model training.

### Baseline Model Performance:

|   True Labels |     0 |     1 |
|--------------:|------:|------:|
|             0 | 10417 |  3465 |
|             1 |  3320 | 10562 |

The results demonstrate the effectiveness of using gold difference at 25 minutes (golddiffat25) as a critical predictor for match outcomes. From the confusion matrix, the model accurately classifies a significant number of matches, with 10,417 True Negatives (correctly predicted losses) and 10,562 True Positives (correctly predicted wins). However, there are also 3,465 False Positives and 3,320 False Negatives, indicating areas for improvement in misclassification.



Grouped Statistics:
|   result |   golddiffat25 |
|---------:|---------------:|
|        0 |       -1511.96 |
|        1 |        1511.96 |

 The grouped statistics further emphasize the strong correlation between gold difference and match results: losing teams average a gold difference of -1511.96, while winning teams average a positive difference of 1511.96. This substantial separation suggests that teams leading in gold at 25 minutes are significantly more likely to win. These findings validate the inclusion of golddiffat25 as a key feature in the predictive model, highlighting its importance in capturing the dynamics of match outcomes.

### Baseline Model Performance:


## Features in the Model
The model uses the following features:

1. **`golddiffat25`** (Quantitative):  
   This feature represents the gold difference at the 25-minute mark, providing a measure of the team’s economic advantage or disadvantage during the early to mid-game phase.

2. **`xpdiffat25`** (Quantitative):  
   This feature represents the experience difference at the 25-minute mark, giving insight into the team’s relative level advantage or deficit compared to their opponent.

Both features are quantitative and continuous. Since there were no ordinal or nominal features, encoding was not required. The features were scaled using **StandardScaler** within the pipeline to normalize their ranges and ensure improved logistic regression performance.

## Model Performance

The model was evaluated on a test set comprising 30% of the dataset to assess its generalization capability. The following metrics were observed:


Baseline Model Performance:
Accuracy: 0.7556187869183115

Classification Report:
              precision    recall  f1-score   support

           0       0.76      0.75      0.75     13882
           1       0.75      0.76      0.76     13882

    accuracy                           0.76     27764
   macro avg       0.76      0.76      0.76     27764
weighted avg       0.76      0.76      0.76     27764


- **Accuracy**: 75.56%  
- **Precision**: 76% (Class 0), 75% (Class 1)  
- **Recall**: 75% (Class 0), 76% (Class 1)  
- **F1 Score**: 75% (Class 0), 76% (Class 1)  

These results indicate that the baseline model performs reasonably well for the task, achieving a balanced performance across both classes. The F1-score, in particular, highlights that the model maintains a good balance between precision and recall.


## Is the Model “Good”?
The current baseline model is "good" as an initial attempt because:

1. **Domain Relevance**:  
   The selected features, `golddiffat25` and `xpdiffat25`, are well-aligned with domain knowledge in League of Legends. These metrics are critical indicators of early-game dominance and are readily available at the 25-minute mark.

2. **Balanced Performance**:  
   The model performs consistently across both classes, as seen from the similar F1-scores for wins and losses. The accuracy of 75.56% is also a strong starting point for a baseline model.

3. **Simplicity and Interpretability**:  
   Logistic regression provides clear and interpretable results, making it easier to understand the impact of features on match outcomes.



## Model Limitations
While the baseline model provides a solid starting point, it has the following limitations:
- It does not account for complex interactions or nonlinear relationships between features.
- It uses only two features, which may oversimplify the problem. Adding more features (e.g., kills, deaths, or map objectives) could improve predictive performance.
- Logistic regression may not capture the full complexity of match dynamics, so exploring more advanced models, such as Random Forests or Gradient Boosting, is a logical next step.

## Next Steps
To improve the model, additional features such as kill counts, deaths, and team objectives could be incorporated. Additionally, experimenting with more complex models and feature selection techniques could enhance performance further.


### Final Model
## **Graph Analysis and Descriptions**


Best Parameters: {'model__class_weight': None, 'model__max_depth': 10, 'model__max_features': 'sqrt', 'model__min_samples_leaf': 4, 'model__min_samples_split': 2, 'model__n_estimators': 100}
Accuracy: 0.7539979829995678

Classification Report:
              precision    recall  f1-score   support

           0       0.75      0.76      0.76     13882
           1       0.76      0.75      0.75     13882

    accuracy                           0.75     27764
   macro avg       0.75      0.75      0.75     27764
weighted avg       0.75      0.75      0.75     27764

The two features I engineered were:

1. Kills/Deaths Ratio (killsat25 / (deathsat25 + 1))
This feature makes sense because it captures a team's efficiency in teamfights and skirmishes. A higher K/D ratio suggests that a team is not only securing kills but doing so while minimizing their own deaths, indicating superior positioning and teamfight execution. The ratio is more informative than raw kills or deaths because securing kills while staying alive allows a team to maintain map pressure and capitalize on their advantages. I added 1 to the denominator to handle cases with zero deaths while preserving the ratio's meaning.

2. Gold-XP Interaction (golddiffat25 * xpdiffat25)
This interaction term captures the compounding effect of having both a gold and experience advantage. In League of Legends, these advantages tend to amplify each other - a gold lead lets you buy better items, which helps secure more kills and objectives, leading to an XP advantage. Similarly, an XP lead gives you access to higher-level abilities, making it easier to secure gold through kills and objectives. A team ahead in both metrics is typically in a much stronger position than having just one advantage, because they have both better items AND higher-level abilities. Multiplying these differences captures this synergistic relationship.

However, looking at my model's actual feature importance scores:
```
golddiffat25: 0.4628
xpdiffat25: 0.3777
killsat25: 0.1595
deathsat25: 0.0000
```

The baseline features (gold and XP difference) remained the most important predictors, suggesting that my engineered features may not have captured additional signal beyond what was already present in the original features. This could indicate that the raw gold and XP differences are already sufficient proxies for team advantages at 25 minutes, or that my feature engineering approach didn't effectively capture the underlying game dynamics I was targeting.

### Modeling Algorithm and Hyperparameters:

The final model utilized a **Random Forest Classifier**, chosen for its ability to handle non-linear relationships and feature interactions while being resistant to overfitting through ensemble learning.

#### **Best Hyperparameters** (from GridSearchCV):
- `max_depth`: 10
- `min_samples_leaf`: 1
- `min_samples_split`: 2
- `n_estimators`: 100

These hyperparameters were selected using **GridSearchCV** with 3-fold cross-validation, exploring a comprehensive parameter space to find the optimal configuration.

### Comparison to Baseline Model:

1. **Performance Metrics**:
   - **Baseline Model Accuracy**: 76.56%
   - **Final Model Accuracy**: 75.39%
   - While the final model shows slightly lower accuracy, it provides more balanced predictions across classes.

2. **Feature Importance Analysis**:
   - The model heavily relies on the original features:
     - golddiffat25: 0.4628
     - xpdiffat25: 0.3777
     - killsat25: 0.1595
     - deathsat25: 0.0000
   - This suggests that the base features (gold and XP differences) are strong predictors of game outcomes at 25 minutes.

3. **Model Characteristics**:
   - The relatively shallow tree depth (max_depth=10) helps prevent overfitting
   - Low minimum samples parameters allow the model to capture fine-grained patterns
   - 100 trees provide a good balance between model complexity and performance

While the final model didn't improve raw accuracy, its more balanced approach to prediction and reliance on interpretable game metrics suggests it may be more reliable across different game scenarios.

### Conclusion:

The final model builds on the baseline by incorporating features that are rooted in the mechanics of gameplay and are likely to influence match outcomes. The hyperparameter tuning process ensured a balance between model complexity and generalization. While the accuracy improvement is slight, the final model’s strength lies in its enhanced interpretability and its ability to leverage meaningful gameplay features, making it a more robust predictor of match outcomes.

## **Graph 1: Baseline Feature Importance**
   <iframe
    src="assets/accuracy_comparison_2.html"
    width="800"
    height="600"
    frameborder="0"
    ></iframe>

- **Description**: The graph compares model accuracies, showing the baseline model achieved 75.6% accuracy while the final model achieved 75.4% accuracy. The minimal difference (0.2%) suggests that adding additional features and complexity didn't significantly improve predictive performance. This could indicate that the simpler baseline model already captured the most important signals in the data.


---

## **Graph 2: Final Feature Importance**

<iframe
    src="assets/feature_importance_final_2.html"
    width="800"
    height="600"
    frameborder="0"
    ></iframe>


- **Description**: Feature Importance Analysis Graph
This graph illustrates the relative importance of each feature in the Random Forest model:


Gold difference at 25 minutes (golddiffat25) is the most important predictor with a score of 0.46
XP difference (xpdiffat25) follows closely with 0.378
Kills at 25 minutes (killsat25) has modest importance at 0.159
Deaths at 25 minutes (deathsat25) shows no predictive value at 0.000

This visualization reveals that resource-based metrics (gold and XP) are significantly more important for predicting game outcomes than combat statistics. The stark contrast between kills (moderately important) and deaths (no importance) is particularly interesting and suggests that securing advantages is more predictive than avoiding setbacks.

---

## **Graph 4: Comparison of Metrics by Class**

  <iframe
  src="assets/model_metrics_@.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>
- **Description**: 
Model Performance Metrics by Class Graph
This bar chart compares precision, recall, and F1-score across both classes (wins and losses):


Class 0 (Losses): Shows balanced metrics with all three scores at approximately 0.76
Class 1 (Wins): Similarly balanced with precision at 0.76 and slightly lower recall and F1-score at 0.75
The red dashed line at 0.75 indicates a baseline performance level

The consistent scores across both classes and metrics suggest that the model performs equally well at predicting both wins and losses, without significant bias toward either outcome. The proximity of all metrics to the 0.75-0.76 range indicates stable and balanced performance overall.


---

## **Graph 5: Confusion Matrices**
<iframe
  src="assets/confusion_matrix_2.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

- **Description**:Confusion Matrix
The matrix shows prediction outcomes with:


True Negatives (Losses correctly predicted): 10,550
False Positives: 3,332
False Negatives: 3,472
True Positives (Wins correctly predicted): 10,410
This balanced distribution suggests the model performs similarly well for both winning and losing predictions, without significant bias toward either outcome.

---

## **Graph 6: ROC Curve Comparison**

<iframe
  src="assets/roc_curve_2.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>
- **Description**: The ROC curve shows strong model performance with an AUC of 0.830, significantly better than random guessing (diagonal line). The curve's shape indicates good discrimination ability, with a sharp initial rise suggesting the model is particularly good at identifying the most confident predictions. The high AUC score validates that despite modest accuracy improvements, the model is making reliable probabilistic predictions.

---
## **Feature Engineering and Selection**
- **Added Features**:
  1. **`kills_deaths_ratio`**: While intended to capture team fight efficiency, this feature ultimately did not contribute significantly to the model's performance, as shown by the feature importance analysis.
  2. **`gold_xp_interaction`**: Similarly, this engineered feature did not appear as significant in the final model, suggesting that the raw gold and XP differences were more informative.
- **Feature Importance Results**: The analysis showed that the original features were most predictive:
  - golddiffat25: 0.46 importance
  - xpdiffat25: 0.378 importance
  - killsat25: 0.159 importance
  - deathsat25: 0.000 importance

## **Modeling Algorithm and Hyperparameter Tuning**
- **Algorithm**: Random Forest Classifier, chosen for its ability to handle non-linear relationships and feature interactions.
- **Best Hyperparameters** (from GridSearchCV):
  - `max_depth = 10`
  - `min_samples_leaf = 1`
  - `min_samples_split = 2`
  - `n_estimators = 100`
- **Tuning Method**: GridSearchCV with 3-fold cross-validation.

### **Performance Comparison**
- **Baseline Model**:
  - Accuracy: 75.56%
  - Equal performance across classes
- **Final Model**:
  - Accuracy: 75.39%
  - Confusion Matrix shows balanced prediction:
    - True Negatives (Losses): 10,550
    - False Positives: 3,332
    - False Negatives: 3,472
    - True Positives (Wins): 10,410
  - ROC-AUC: 0.830, indicating strong discriminative ability

## Conclusion

This project explored predicting League of Legends match outcomes using data at the 25-minute mark. While our feature engineering attempts (kills/deaths ratio and gold/XP interaction) were theoretically sound, the empirical results showed that the original features were most predictive.

### Key Findings:
1. **Resource Advantages Dominate**:
   - Gold difference (0.46) and XP difference (0.378) were the strongest predictors
   - Kill count had moderate importance (0.159)
   - Death count showed no significant predictive power

2. **Model Performance**:
   - The final model achieved 75.39% accuracy
   - Strong ROC-AUC score of 0.830
   - Balanced performance across winning and losing predictions

3. **Feature Engineering Impact**:
   - Simpler features outperformed engineered ones
   - Original resource-based metrics (gold, XP) captured most of the predictive signal

This analysis suggests that in professional League of Legends, resource advantages at 25 minutes are more reliable predictors of game outcomes than combat statistics or engineered feature combinations. The high ROC-AUC score indicates that the model makes reliable probabilistic predictions, even though the accuracy remained similar to the baseline model.