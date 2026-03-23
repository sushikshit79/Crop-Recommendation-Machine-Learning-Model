# Crop Recommendation Machine Learning Model

## Project Title
Crop Recommendation - Machine Learning Model

**Author:**
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
 
### Next steps

* **Evaluate Multiple Classification Models:** Train and compare several classification algorithms like Logistic Regression, K-Nearest Neighbors (KNN), Decision Tree, Random Forest and Support Vector Classifier (SVC). These models will help determine which algorithm best captures patterns in the agricultural dataset and produces reliable predictions.
* **Hyperparameter Tuning:** For each model will be evaluated by multiple hyperparameter configurations to optimize performance. Parameters such as the number of neighbors in KNN, tree depth in Decision Trees, number of estimators in Random Forest, and kernel parameters in SVC will be tested for best performing model configuration.
* **Feature Evaluation and Selection:** Analyze the contribution of each feature used in the model, including State, Agricultural District, County, Year, geographic codes, and standardized yield. Features will be evaluated to determine their impact on prediction accuracy and ranking performance.
* **Feature Reduction:** Identify features that can be removed without significantly affecting model performance. Eliminating non-informative features can reduce model complexity, improve interpretability, and potentially enhance model generalization.
* **Model Comparison and Selection:** Compare the performance of all trained models using consistent evaluation metrics such as accuracy, precision, recall, F1 score, ROC-AUC, and ranking performance.
* * **Ranking-Based Evaluation:** Since the objective of the project is to recommend suitable crops, the models will be evaluated not only on standard classification metrics but also on their ability to correctly rank crop predictions. Metrics such as Top-k accuracy for Top-3 recommendations will be used to measure top predicted options.
 

### **Evaluate Multiple Classification Models with Default Behavior**

To Evaluate the effectiveness of different classification approaches for crop prediction, five machine learning models were trained and tested: Logistic Regression, K-Nearest Neighbors (KNN), Decision Tree, Support Vector Classifier (SVC) and Random Forest Classifier. Each model was evaluated using metrics such as accuracy, precision, recall, F1 score, ROC AUC, training time and prediction time. This step establishes a baseline to understand how each model performs before applying hyperparameter tuning or feature engineering. 

**Evaluate Metrics of Multiple Classification Models with Default Behavior** 
![https://github.com/sushikshit79/Crop-Recommendation-Machine-Learning-Model/blob/main/images/crop_recom_param_def_metrics.jpg](https://github.com/sushikshit79/Crop-Recommendation-Machine-Learning-Model/blob/main/images/crop_recom_param_def_metrics.jpg)

### Observations with default parameters
* Decision Tree classifier shows the best overall performance under default parameters, achieving the highest accuracy and F1 score among the evaluated models.It also has very fast training and prediction times, making it both accurate and computationally efficient for this task.
* Logistic Regression and Random Forest exhibit the highest ROC AUC scores, indicating strong capability in distinguishing between crop classes.
* K-Nearest Neighbors performs the weakest, with lower accuracy and significantly higher prediction time due to its distance-based computation.

Overall, Decision Tree provides the best balance of predictive performance and efficiency among the models when using default settings.

### **Evaluate Multiple Classification Models with Hyperparameter Tuning:**
Hyperparameter tuning is used to improve the performance of machine learning models by identifying the optimal configuration of model parameters that control how the algorithm learns from the data. Hyperparameters are set before training and influence aspects such as model complexity, regularization, and decision boundaries. Evaluating multiple hyperparameter combinations helps ensure that the model captures meaningful patterns in the dataset while avoiding underfitting or overfitting.

In this project, hyperparameter tuning was performed using GridSearchCV with cross-validation to systematically test multiple parameter combinations across different classification models.

**Evaluate Metrics of Multiple Classification Models with Hyperparameter Tuning:**
![https://github.com/sushikshit79/Crop-Recommendation-Machine-Learning-Model/blob/main/images/crop_recom_param_hp_metrics.jpg](https://github.com/sushikshit79/Crop-Recommendation-Machine-Learning-Model/blob/main/images/crop_recom_param_hp_metrics.jpg)

### Hyperparameter Tuning observations:
* The Decision Tree classifier continues to show the strongest overall performance after hyperparameter tuning, achieving the highest accuracy and F1 score among the evaluated models.
* The ROC AUC score of the Decision Tree classifier is also comparable to the strong ROC AUC performance of Logistic Regression and Random Forest classifiers, indicating good class separation capability.
* SVC demonstrates moderate performance, while K-Nearest Neighbors remains the weakest performer among the evaluated models.

## Engineering features

### Modeling with Hyperparameters and Feature Engineering 1 (HP_FE1)
* **Ag District**: This feature was removed because agricultural districts are aggregations of counties and therefore do not provide additional information beyond the county-level geographic feature already present in the dataset. Removing it reduces redundancy while preserving relevant geographic information.

* **State ANSI and County ANSI**: These numerical identifiers were removed because the same geographic information is already represented through the categorical State and County features. Keeping both forms would introduce redundant information without improving model learning.

* **std_yield**: This feature was removed because yield values are typically known only after crop production and may introduce potential data leakage when predicting crop suitability. The aggregated historical yield features were created instead to represent long-term productivity patterns without relying on outcome-based information.
    * **state_crop_avg_yield:** Historical average crop yield at the state level used to capture long-term regional productivity patterns and reduce yearly fluctuations.
    * **county_crop_avg_yield:** Historical average crop yield at the county level used to capture localized agricultural productivity and improve learning of crop suitability at a finer geographic level.

**Evaluate Metrics of Multiple Classification Models with Hyperparameters and Feature Engineering 1 (HP_FE1):**
![https://github.com/sushikshit79/Crop-Recommendation-Machine-Learning-Model/blob/main/images/crop_recom_hp_fe1_metrics.jpg](https://github.com/sushikshit79/Crop-Recommendation-Machine-Learning-Model/blob/main/images/crop_recom_hp_fe1_metrics.jpg)

### Observations on models with Hyperparameters and Feature Engineering 1 (HP_FE1)
* Decision Tree classifier achieves the best overall performance, achieving the highest accuracy(0.887), precision(0,872), recall(0.887), F1(0.865) and ROC AUC(0.993) score among all evaluated models, indicating strong predictive capability and good class separation capability.
* Decision Tree classifier also maintains very low training and prediction times, making it both accurate and computationally efficient compared to other models.
* Random Forest shows strong performance as well, with high accuracy (~0.83) and a strong ROC AUC score, indicating good class discrimination capability.
* Logistic Regression demonstrates balanced performance, with good ROC AUC and moderate improvements in accuracy after feature engineering.
* SVC accuracy aas increased measurably still showing moderate performance with reasonable precision, higher training and prediction times as compared to other models.
* K-Nearest Neighbors accuracy has increased but remains the weakest performer, with lower accuracy and significantly higher prediction time.

### Modeling with Hyperparameters Hyperparameters and Feature Engineering 2 (FE2)

Feature Engineering 2 (FE2) introduced additional features to better capture geographic specificity and temporal trends in the agricultural data. These transformations help the model learn regional crop patterns and long-term agricultural changes more effectively. The following features were created to evaluate whether these transformations improve model accuracy and other evaluation metrics.

* **state_county:** A combined geographic feature created by concatenating State and County to represent a unique location identifier, enabling the model to learn more precise regional crop suitability patterns.
* **years_from_start:** A temporal feature derived from the Year variable representing the number of years since the earliest observation in the dataset, allowing the model to capture long-term agricultural trends without relying on raw year values.

**Evaluate Metrics of Multiple Classification Models with Hyperparameters and Feature Engineering 2 (HP_FE2):**
![https://github.com/sushikshit79/Crop-Recommendation-Machine-Learning-Model/blob/main/images/crop_recom_hp_fe2_metrics.jpg](https://github.com/sushikshit79/Crop-Recommendation-Machine-Learning-Model/blob/main/images/crop_recom_hp_fe2_metrics.jpg)

### Observations on models with Hyperparameters and Feature Engineering 2 (HP_FE2)
**Feature Engneering 2(HP_FE2)** transformations generated almost comparable results to **Feature Engineering 1 (HP_FE2)** transformations, but the metrics decreased negligeably.
* Decision Tree classifier still continues to deliver the strongest overall performance, achieving the highest accuracy, precision, recall, F1 and ROC AUC score among all evaluated models.
* Random Forest classifier shows the second-best performance, with strong accuracy and balanced precision–recall values, along with a high ROC AUC score.
* Logistic Regression maintains stable performance, with competitive ROC AUC while maintaining moderate accuracy and F1 score.
* K-Nearest Neighbors remains the weakest performer, with significantly lower accuracy, precision, recall, and F1 score.

### Modeling with Hyperparameters and Feature Engineering 3 (HP_FE3)
* In this setup, the model uses State and County as the only input features to predict the most suitable crop. These features are treated as categorical variables and encoded using one-hot encoding to enable their use in machine learning models.
* This approach removes all engineered and yield-based features to eliminate data leakage and ensure that the model relies solely on information that would realistically be available to farmers and stakeholders.

**Evaluate Metrics of Multiple Classification Models with Hyperparameters and Feature Engineering 3 (HP_FE3):**
![https://github.com/sushikshit79/Crop-Recommendation-Machine-Learning-Model/blob/main/images/crop_recom_hp_fe3_metrics.jpg](https://github.com/sushikshit79/Crop-Recommendation-Machine-Learning-Model/blob/main/images/crop_recom_hp_fe3_metrics.jpg)

### Observations on models with Hyperparameters and Feature Engineering 1 (HP_FE3)
* Model performance is significantly lower compared to FE1, with accuracy ranging roughly between 19%–28%, indicating limited predictive capability.
* Geographic features State and County alone are insufficient to capture crop suitability, as they do not include critical factors like yield into the mix.
* Overall, HP_FE3 demonstrates the trade-off between real-world applicability and model accuracy, emphasizing the need for richer feature sets to improve prediction quality.

## Visulization of Evaluation Metrics

### Accuracy Comparison Across Models
![https://github.com/sushikshit79/Crop-Recommendation-Machine-Learning-Model/blob/main/images/accuracy_comparison_across_models.jpg](https://github.com/sushikshit79/Crop-Recommendation-Machine-Learning-Model/blob/main/images/accuracy_comparison_across_models.jpg)

### F1 Score Comparison Across Models
![https://github.com/sushikshit79/Crop-Recommendation-Machine-Learning-Model/blob/main/images/f1_comparison_across_models.jpg](https://github.com/sushikshit79/Crop-Recommendation-Machine-Learning-Model/blob/main/images/f1_comparison_across_models.jpg)

### ROC AUC Comparison Across Models
![https://github.com/sushikshit79/Crop-Recommendation-Machine-Learning-Model/blob/main/images/roc_auc_comparison_across_models.jpg](https://github.com/sushikshit79/Crop-Recommendation-Machine-Learning-Model/blob/main/images/roc_auc_comparison_across_models.jpg)

### Performance Comparison Across Models
![https://github.com/sushikshit79/Crop-Recommendation-Machine-Learning-Model/blob/main/images/perf_comparison_across_models.jpg](https://github.com/sushikshit79/Crop-Recommendation-Machine-Learning-Model/blob/main/images/perf_comparison_across_models.jpg)

### Model Performance Progression Across Modeling Stages
![https://github.com/sushikshit79/Crop-Recommendation-Machine-Learning-Model/blob/main/images/mdel_perf_stages.jpg](https://github.com/sushikshit79/Crop-Recommendation-Machine-Learning-Model/blob/main/images/mdel_perf_stages.jpg)

## Model Comparison Across Experiments (Default → HP → FE1 → FE2 → FE3)

### Logistic Regression
* Shows consistent and stable performance across all experiments.
* Noticeable improvement with feature engineering (FE1/FE2), especially in accuracy and F1.
* Maintains strong ROC AUC throughout, indicating good class separability.
* Best suited as a baseline, interpretable model, but not the top performer.

### K-Nearest Neighbors (KNN)
* Weakest performer across all experiments.
* Slight improvement with hyperparameter tuning and feature engineering, but still significantly below others.
* High prediction time and sensitivity to feature scaling/geography.
* Not recommended for this dataset.

### Decision Tree
* Top performer across all experiments, especially after defining Hyperparameters and Feature Engineering.
* Achieves highest accuracy, precision, recall, F1 and ROC AUC consistently with Hyperparameters and Feature Engineering.
* Very fast training and prediction times.
* Risk of overfitting exists but controlled with tuning (max_depth, splits).

### Support Vector Classifier (SVC)
* Moderate performance across all stages.
* Benefits from feature engineering but still lags behind tree-based models.
* Higher training and prediction time.
* ROC-AUC was not computed for the SVC model because probability estimates were not enabled, and enabling them would significantly increase computational cost.
* Not optimal overall.

### Random Forest
* Consistently strong and reliable performer.
* Significant improvement after Feature Engineering (FE1/FE2).
* High ROC AUC and balanced precision–recall, indicating robustness.
* Slightly slower than Decision Tree but more stable (less overfitting).

### Real World Execution

Based on the comparative evaluation across all models and experiments, both the Decision Tree classifier and Random Forest Classifier with Hyperparameter Tuning and Feature Engineering 1 (HP_FE1) are most effective models. These models consistently achieved high accuracy, precision, recall, and F1 score, indicating strong predictive performance and balanced classification across all target classes. Additionally, they also delivered a high ROC AUC score, demonstrating excellent capability in distinguishing between crop classes.

Since both Decision Tree and Random Forest demonstrated strong and comparable performance across evaluation metrics, it is important to assess their behavior in real-world scenarios. Running sample-based predictions allows us to evaluate how each model performs in practical use, particularly in terms of recommendation quality and probability distribution. These results can then be used to select the most suitable model for deployment.

**Comparison of Predictions - Decision Tree vs Random Forest**
![https://github.com/sushikshit79/Crop-Recommendation-Machine-Learning-Model/blob/main/images/Best_Model_Pred_Comp.jpg](https://github.com/sushikshit79/Crop-Recommendation-Machine-Learning-Model/blob/main/images/Best_Model_Pred_Comp.jpg)

#### Overall Conclusion – Decision Tree vs Random Forest
* The Decision Tree model produces highly confident but rigid predictions, often assigning extreme probabilities (0 or 1), which leads to limited diversity in recommendations beyond the top rank.
* In contrast, the Random Forest model generates more balanced probability distributions, resulting in more meaningful and diverse Top-3 crop recommendations.
* Across multiple locations, both models generally agree on the top-ranked crop, indicating consistency in identifying dominant regional crops.
* Random Forest provides better differentiation in lower-ranked predictions, capturing alternative crop options that the Decision Tree fails to represent.

Overall, while Decision Tree is simpler and highly interpretable, Random Forest is better suited for recommendation systems, as it offers improved generalization and more reliable probability-based rankings.

## Deployment Report

### Overview
The deployment focuses on operationalizing the trained machine learning model to provide real-time crop recommendations based on user inputs. The final solution is designed to accept State and County as inputs and return the top 3 recommended crops with probabilities, enabling practical use by farmers, agricultural stakeholders and lenders

### Final Model Selection
After evaluating multiple models across different feature engineering strategies, Random Forest was selected as the final model for deployment. While Decision Tree showed comparable accuracy, Random Forest demonstrated better generalization and produced more reliable and diverse probability-based recommendations during real-world sample testing.

### System Architectural Components
* Trained Random Forest model (**best_rf_model**)
* Prediction function for Top-3 recommendations (predict_top3_from_location)

#### Input and Output Design

* **Inputs:**
    * State (Example: TENNESSEE)
    * County (Example: LINCOLN)

* **Output:**
    * Top 3 recommended crops
    * Associated probability scores

**Example**
Below with sample code and results

state = "TENNESSEE"
county = "LINCOLN"
preds = predict_top3_from_location(best_rf_model, state, county)
preds_df = pd.DataFrame(preds)
preds_disp = preds_df.style.set_table_styles([
    {'selector': '', 'props': [('border', '1px solid black')]},
    {'selector': 'td', 'props': [('border', '1px solid black')]},
    {'selector': 'th', 'props': [('border', '1px solid black')]}
])
preds_disp

![https://github.com/sushikshit79/Crop-Recommendation-Machine-Learning-Model/blob/main/images/sam_op.jpg](https://github.com/sushikshit79/Crop-Recommendation-Machine-Learning-Model/blob/main/images/sam_op.jpg)

#### Deployment Approach:
* **The model can be deployed using the following approaches**
    * **UI Integration and API-Based Deployment:** Deploy the model as an API  using frameworks like FastAPI and integrate it with a web or mobile interface to enable farmers and stakeholders to access crop recommendations in real time.
    * **Batch Deployment:** Generate recommendations for multiple regions periodically.

#### Limitations
* Predictions are based on geographical features and yield only and deosn't include real-time environmental factors like weather and soil conditions
* Model performance may vary on sparse data

#### Future Enhancements
* Integrate weather and soil data for improved predictions
* Build a user friendly dashboard
* Add explainability features to improve transparency

### Summary
The deployed solution provides a practical crop recommendation system that balances model performance with real-world usability, enabling data-driven agricultural decision-making.

## Executive Summary

This project presents a machine learning crop prediction and recommendation system designed to support farmers, agricultural stakeholders, and lenders in making informed data-driven decisions. By leveraging historical agricultural data at the state and county level, multiple models including Logistic Regression, KNN, Decision Tree, SVC and Random Forest were developed and evaluated using various feature engineering strategies to identify the most effective approach.

Introducing only State and County as input features resulted in low model accuracy, highlighting the limited predictive power of geographic data alone. Incorporating yield-based features significantly improved accuracy, but also introduced practical constraints. While the Decision Tree model achieved slightly higher accuracy, it produced overly confident and rigid predictions with limited variability in alternative recommendations. In contrast, Random Forest provided better differentiation across lower-ranked predictions, offering more diverse and realistic crop options. Based on comparative analysis and real-world sample testing, Random Forest was selected as the preferred model as it strikes a better balance between predictive performance and practical usability for crop recommendation.

The final system enables users to input a state and county and receive ranked crop recommendations, supporting better crop selection, reducing agricultural risk and aiding lenders in risk assessment. Overall, the project highlights the importance of feature design, model selection and aligning machine learning solutions with real-world usability.

### Outline of project

- **Link to Jupyter Notebook:** [([https://github.com/sushikshit79/Crop-Recommendation-Machine-Learning-Model/blob/main/crop_recommendation.ipynb](https://github.com/sushikshit79/Crop-Recommendation-Machine-Learning-Model/blob/main/crop_recommendation.ipynb))

#### Contact and Further Information
For questions, feedback or additional information regarding this project, please contact:

**Sushikshit Billa**\
Email:sushikshit@gmail.com\
LinkedIn: linkedin.com/in/sushikshit-billa
