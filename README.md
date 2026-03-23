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

### Data Analysis and Preparation
The primary data source for this project is an agricultural production dataset containing state- and county-level crop information, including irrigated and non-irrigated acreage and yield. The data is obtained from the USDA (United States Department of Agriculture) QuickStats database and is downloaded as a CSV report from https://quickstats.nass.usda.gov/. This dataset serves as the core data source for model training and evaluation.

### Data Sources
Data analysis and preparation were conducted as part of the capstone submission for Module 20.
Location to business understanding and data preparation
![https://github.com/sushikshit79/CropRecommendationEDA/edit/main/README.md]


### Outline of project


- **Link to Jupyter Notebook:** [(https://github.com/sushikshit79/CropRecommendationEDA/blob/main/crop_prediction_eda.ipynb)](https://github.com/sushikshit79/CropRecommendationEDA/blob/main/crop_prediction_eda.ipynb)


#### Contact and Further Information
For questions, feedback or additional information regarding this project, please contact:

**Sushikshit Billa**\
Email:sushikshit@gmail.com\
LinkedIn: linkedin.com/in/sushikshit-billa
