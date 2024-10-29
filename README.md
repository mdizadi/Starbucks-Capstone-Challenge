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
- **Logit Regression**: A logistic regression model identifies significant variables that affect the likelihood of completing an offer. Interaction terms are included to capture nuanced effects, such as the influence of income levels on reward and difficulty.
- **Random Forest Classifier**: A Random Forest model is used to classify customer responses across different offers, considering variables like age, income, spending history, and offer difficulty/reward.

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
- `shap`

To install the required packages:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn statsmodels shap
```

## ChatGPT Assistance
This project was developed with the support of OpenAI's ChatGPT for code explanation, README file creation, and analytical guidance. ChatGPT helped streamline and clarify the project documentation.

## Medium Blog Post
For a detailed write-up of this project, please see the Medium blog post [here](https://support.udacity.com/hc/en-us/articles/17527771361165-FAQs-about-Udacity-s-New-Subscription).