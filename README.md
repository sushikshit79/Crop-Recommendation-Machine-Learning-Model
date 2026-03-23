# Crop Recommendation Machine Learning Model

## Project Title
Crop Recommendation - Machine Learning Model

**Author**
Sushikshit Billa

### Executive summary

Crop selection plays a critical role in determining agricultural productivity, profitability, and financial stability for farmers and the broader agricultural ecosystem. Selecting crops that are well suited to the geographic and environmental conditions of a region can significantly improve yields and reduce operational risk. However, many crop decisions continue to rely on traditional practices, intuition, or incomplete information, which can lead to suboptimal outcomes and increased financial exposure for both farmers and agricultural lenders.

This project develops a data-driven crop recommendation approach by leveraging historical agricultural production data, including yield and irrigation information at the state and county levels. Using machine learning techniques, the model analyzes geographical agricultural data to identify crops and sub-commodity categories that are most suitable for a given region. The resulting model is capable of recommending the most likely crop options for a specific location, along with ranked alternatives, providing practical decision support for agricultural planning.

### Rationale
Crop selection is a critical decision in agriculture because it directly affects yield, profitability, and the financial stability of farming operations. When this decision is made without reliable, data-driven insights, farmers often rely on traditional practices, personal experience, or incomplete information about regional crop performance. While these approaches may work in some cases, they may not fully capture historical production trends or geographic variability in crop suitability. As a result, farmers may select crops that are not well suited for their region, which can lead to lower yields, reduced profitability, and increased financial risk.

The lack of objective, data-driven guidance also impacts other stakeholders in the agricultural ecosystem. Agricultural lenders, financial institutions, and agribusiness organizations must evaluate the viability and risk associated with crop production when making lending or investment decisions. Without analytical insights into which crops historically perform well at the state and county levels, it becomes more difficult to assess regional crop suitability and associated risks. Developing a data-driven model to analyze historical agricultural data can therefore help farmers and stakeholders make more informed decisions and improve the overall effectiveness and stability of agricultural planning.

### Research Question
Can a machine learning model accurately recommend the most suitable agricultural commodity for a farmer based on state and county level production and irrigation data?

## Objective

The objective of this project is to deliver a data-driven capability that identifies and ranks the best-performing crops for a given state and county based on historical yield data. This solution is intended to support farmers, agricultural stakeholders, and agricultural lenders by assisting with information on suitable crops for planting, thereby improving crop selection decisions and regional crop risk assessment.

The project focuses on developing and evaluating machine learning models—including KNN, Logistic Regression, Decision Tree, Random Forest and SVC to predict and recommend crops under different feature engineering strategies. It aims to minimize agricultural risk by helping farmers avoid low-yield crops while also supporting financial institutions in assessing crop viability and lending risk. Additionally, the solution emphasizes real-world applicability by enabling predictions with limited inputs such as state and county and is designed to be scalable for future enhancements with additional agricultural data.

The project follows the CRISP-DM (Cross-Industry Standard Process for Data Mining) framework to ensure a structured and iterative approach, covering business understanding, data preparation, modeling, evaluation, and deployment.

### Data Sources
The primary data source for this project is an agricultural production dataset containing state- and county-level crop information, including irrigated and non-irrigated acreage and yield. The data is obtained from the USDA (United States Department of Agriculture) QuickStats database and is downloaded as a CSV report from https://quickstats.nass.usda.gov/. This dataset serves as the core data source for model training and evaluation.

### Data Analysis and Preparation
Data analysis and preparation were conducted as part of the capstone submission for Module 20.
Location to business understanding and data preparation
![https://github.com/sushikshit79/CropRecommendationEDA/edit/main/README.md]

#### Feature Engineering
The dataset contains both categorical and numeric attributes representing geographic, administrative, and yield related information. To prepare the data for modeling, features were grouped into categorical and numerical variables based on their characteristics.

* **Categorical Features:**
The following fields were treated as categorical variables because they represent geographic or administrative classifications rather than measurable numeric quantities
    * State – Represents the U.S. state where the crop yield was recorded.
    * Ag District – Agricultural district grouping within a state.
    * County – County level geographic identifier.

* **Numeric Features:**
The following variables were treated as numerical features because they represent quantitative values or encoded identifiers
    * Year – Indicates the year of the agricultural observation and allows the model to capture trends in crop productivity.
    * State ANSI – Numeric code representing the state. 
    * Ag District Code – Numeric identifier for the agricultural district.
    * County ANSI – Numeric identifier for the county.
    * county_missing_flag – Binary indicator identifying records where the county code was originally missing and replaced with a placeholder.
    * std_yield – Standardized crop yield measured in pounds per acre, representing productivity of the crop.

* **Target Variable:**
New target variable is constructed for following reasons
    * To create a more precise prediction target, a new variable called target_crop was engineered by combining the Commodity and Sub_Commodity fields.
    * This approach ensures that the model predicts both the main crop category and its specific sub-category, enabling more granular crop recommendations.

* **Train/Test Split:**
The dataset was divided into training and testing subsets to evaluate the performance of the machine learning models on unseen data.
   * A 70%–30% split was used
      * 70% of the data was used for training the model, allowing the algorithm to learn patterns.
      * 30% of the data was reserved as a test dataset to objectively evaluate model performance.
    
### Model Evaluation:
**Baseline Model Evaluation**
Baseline modeling establishes a reference point for model performance before applying more complex machine learning algorithms. It helps determine whether a predictive model is actually learning meaningful patterns from the data.

To establish a reference point for model performance, two baseline models were implemented: a Dummy Classifier and a Logistic Regression classifier.
   * The Dummy Classifier will establish a baseline that represents random or distribution-based predictions.
   * The Logistic Regression model will provide an interpretable machine learning approach that can capture meaningful relationships in the dataset.
   * Comparing these two models allows us to determine whether the model is learning useful patterns from the data and provides a foundation for evaluating more advanced algorithms in later stages of the project.

Below are the performance metrics for Dummy Classifier and a Logistic Regression classifier.

![https://github.com/sushikshit79/Crop-Recommendation-Machine-Learning-Model/blob/main/images/model_comparison.jpg](https://github.com/sushikshit79/Crop-Recommendation-Machine-Learning-Model/blob/main/images/model_comparison.jpg)

* **Dummy Classifier Observations**
   * Correctly predicts about 11–12% of samples
   * Macro Precision / Recall / F1 is 0.04 that projects class imbalance, which means rare clases may never get predicted correctly
   * ROC AUC is 0.5,  which means no discrimination and behaving correctly on random ranking

The stratified DummyClassifier achieved an accuracy of 11.8% with macro F1 of 0.042, establishing the statistical performance floor. Any model exceeding this baseline demonstrates learned predictive signal beyond random class distribution.

* **Logistic Regression Observations**
   * Accuracy (68.6%) is substantially higher than the Dummy baseline (11.8%).
   * Precision indicates that more than half of predicted positives are correct.
   * Recall demonstrates moderate ability to capture actual positives, suggesting potential improvement through threshold tuning.
   * The macro ROC AUC of 0.98 indicates strong class separability and ranking capability.

### Outline of project


- **Link to Jupyter Notebook:** [(https://github.com/sushikshit79/CropRecommendationEDA/blob/main/crop_prediction_eda.ipynb)](https://github.com/sushikshit79/CropRecommendationEDA/blob/main/crop_prediction_eda.ipynb)


#### Contact and Further Information
For questions, feedback or additional information regarding this project, please contact:

**Sushikshit Billa**\
Email:sushikshit@gmail.com\
LinkedIn: linkedin.com/in/sushikshit-billa
