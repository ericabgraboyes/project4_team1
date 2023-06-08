## Predicting - Customer Churn

### Project Overview:
This project's objective is to develop a machine learning model that can accurately predict if a customer will leave their bank. The concept of customer turnover or churn is paramount to most businesses as the cost of acquiring new customers is typically higher than the cost of retaining existing customers.  We thought it would be interesting to understand what drives customer churn or turnover.  That is to say are there certain demographics or characteristics in which a higher proportion of customers exited the bank vs. stayed.  When training the model to predict customer turnover or churn, the project considered factors such as age, credit score, gender... [INSERT FACTORS BASED ON FEATURE IMPORTANCE]. Ultimately if banks understood what variables drove customers to leave they could not only implement measures to mitigate churn but also identify attributes that are important when implementing customer loyalty programs. 

#### Key Questions to Consider:
- Can we accurately predict if a customer will leave? 
- What factors have the greatest importance in determining if a customer will leave?
- Is there a certain age group or demographic that is more likely to exit?
- How does where a person live impact churn?  Do factors that predict customer churn differ by country?
- How does a customer's credit score influence their decision to leave?

#### Technologies Employed:
- Python/Pandas/Numpy
- Scikit-learn
- TensorFlow
- Spark
- Tableau
- HTML/CSS

#### Datasets:
- Bank churn customer data (10,000 records): https://www.kaggle.com/datasets/radheshyamkollipara/bank-customer-churn?resource=download
- It is important to acknowledge this project used ficitous data designed for the purpose of machine learning.  Unfortunately access to real customer retention and attrition data is highly sensitive and confidential.  While we would have liked to have real world customer level data to build our machine learning model off of, this was not feasible. The project does however provide a framework for building out the features and attributes that would be valuable to consider when predicting customer churn.

### Project Implementation - Data Cleansing:
The data_cleanse.ipynb notebook ingested the raw CSV file of bank churn customer data and used Spark to clean and transform the underlying dataset.  As part of the data cleanse process we dropped the row number, customer id and surname fields from the raw data. The cleansed data was exported to a separate csv file and used in the subsequent notebooks where we developed and optimize the machine learning models.

### Project Implementation - Machine Learning Develoment & Optimization:
The data_cleanse.ipynb notebook ingested the raw CSV file of bank churn customer data and used Spark to clean and transform the underlying dataset.  As part of the data cleanse process we dropped the row number, customer id and surname fields from the raw data. The cleansed data was exported to a separate csv file and used in the subsequent notebooks where we developed and optimize the machine learning models.

#### Visualizations:

### Future Considerations:

#### Contributors:
- Erica Graboyes
- Chris Johnson
- Daniel Lee
- Lacey Morgan
- Kevin McMurphy
