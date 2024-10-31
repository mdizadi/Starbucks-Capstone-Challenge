# Starbucks-Capstone-Challenge

## Project Overview

This project is the Udacity capstone project that uses simulated customer data from the Starbucks rewards mobile app to investigate customer response to different types of offers. The goal is to analyze the influence of various offers, demographics, and spending history on customer behavior. Specifically, this project seeks to determine which demographic groups respond best to specific types of offers, such as BOGO (buy one, get one free), discounts, or informational offers.

## Data Sources

The project uses three datasets:
- **portfolio.json** - Contains details about each offer, including offer ID, type, difficulty, duration, reward, and available channels.
- **profile.json** - Contains demographic data for each customer, such as age, gender, income, and membership start date.
- **transcript.json** - Logs all transactions and offer-related events (offer received, viewed, and completed), each associated with a specific customer.

## Project Structure

### Data Preprocessing
- **Portfolio Data:** One-hot encodes offer channels and converts the offer duration from days to hours.
- **Profile Data:** Encodes categorical demographic variables like age, gender, and income groups.
- **Transcript Data:** Extracts and organizes events related to offers received, viewed, and completed, tracking customer interactions over time.

### Modeling Approach
- **Logistic Regression**: A baseline logistic regression model was used to examine significant variables affecting the likelihood of offer completion. Interaction terms provided insights into complex effects, such as income's influence on reward and difficulty.
- **Random Forest Classifier**: A Random Forest model helped predict customer responses to different offers. The feature importance analysis identified age, income, and spending history as key predictors.
- **XGBoost Classifier**: XGBoost was implemented as an advanced classifier to enhance prediction accuracy. 

Hyperparameter tuning was applied to optimize performance.

### Model Selection

To determine the best-performing model, both **accuracy** and **F1 score** were considered. These metrics provide an overall performance measure and address potential class imbalances in the data. The test accuracy and F1 scores for both models are nearly identical: Random Forest achieved 80.0% accuracy and an F1 score of 0.79, while XGBoost achieved an 80.0% accuracy and an F1 score of 0.80.

Additionally, both models display minimal overfitting, as indicated by the small differences between training and test accuracies (Random Forest: -0.015, XGBoost: -0.019), suggesting each model generalizes well to new data.

The **Random Forest model** was selected as the final model due to its similar performance to XGBoost and because its feature importance order—particularly for "Reward" and "Difficulty"—aligns more closely with logistic regression. This alignment improves interpretability, offering clearer insights into the impact of key variables.


## Analysis and Findings

### Offer Completion
- The analysis focuses on variables that influence the probability of offer completion. Key findings include:
  - **Income and Spending**: Higher income levels and spending histories increase the likelihood of completing offers.
  - **Offer Type**: Discount offers tend to have a higher completion rate.
  - **Difficulty and Reward**: Lower difficulty levels increase the completion probability among younger demographics.

### Multi-Level Classification
- A multi-level classification model predicts which offer type each customer is most likely to complete.
- The model suggests targeting offers with low difficulty to young, low-income customers while assigning higher difficulties to high-income individuals.

## Dependencies

The project requires the following Python packages:
- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`
- `scikit-learn`
- `statsmodels`
- `xgboost`
- `shap`

To install the required packages:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn statsmodels xgboost shap
```

## Refrences
[Starbucks-Capstone-Challenge](https://github.com/mspcvsp/StarbucksCapstoneChallenge)
[Model Evaluation Metrics in Machine Learning](https://www.kdnuggets.com/2020/05/model-evaluation-metrics-machine-learning.html)
[Understanding Classification Metrics: Your Guide to Assessing Model Accuracy](https://www.kdnuggets.com/understanding-classification-metrics-your-guide-to-assessing-model-accuracy)
[Overfitting in Machine Learning: What It Is and How to Prevent It](https://elitedatascience.com/overfitting-in-machine-learning)

This project was developed with the support of OpenAI's ChatGPT for code explanation, README file creation, and analytical guidance. ChatGPT helped streamline and clarify the project documentation.

For a detailed write-up of this project, please see the Medium blog post [here](https://medium.com/@mdizadi/understanding-starbucks-customer-behavior-f2055400f790).