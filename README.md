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
We loaded the raw csv file to jupyter notbook and used Spark to clean and transform the underlying dataset.  As part of the data cleanse process we dropped the row number, customer id and surname fields from the raw data. The cleansed data was exported to a separate csv file and used in the subsequent notebooks where we developed and optimize the machine learning models.

### Project Implementation - Developing a machine learning model:
We loaded the cleansed dataset into a separate jupyter notebook (model_exploration) where we evaluated both the skewness and kurtosis of the independent variables.  We grouped the independent variables into numeric and categorical groups and encoded the categorical variables using one-hot encoding. Next we created our features (independent variables) and target (dependent) variables and used train_test_split to split the data.

We used a function to train and test several different models and then analyzed the initial model results based on their accuracy score 

[Insert model table and accuracy]

Even though the initial model accuracy was not as impressive as other models, we wanted to use a logistic regression model to predict customer churn -- to see if we could optimize the model's performance using various machine learning techniques.  We also aligned that given the colinearlity between exited and complain we should remove the "Complain" variable when building the regression model as the variable created quasi-causation. If the variable had captured number of complaints instead of a binary output we would have reconsidered excluding it the next phase of the project. 

### Project Implementation - Optimizing and Tuning a machine learning model:
The started the machine learning model out using a simple baseline logistic regression. The baseline model did not account for resampling (in spite of the imbalanced sample) or scaling of numeric independent variables.  We felt that it was important to establish a true baseline for how the model performed, even though scaling the dependent variables and accounting for sampling bias were steps we knew ultimately needed to be taken.

While the baseline model demonstrated decent accuracy, it is important to note that the model's performance dropped considerably when evaulating performance on the balanced accuracy scale. While the precision score (prediction true positives) was "tenible" the recall score of .05 was quite discouraging when considering the model's overall performance.

Given the sub-optimal performance of the baseline model the first modification we made was to set the built-in class_weight method to balanced (class_weight = balanced). This method adjusts the class weight inversely proportional to their respective frequencies..so that model is effectively more 'aware' of underrepresented classes.  We thought that by increasing the model's awareness of the under-represented classes it would improve the model's ability to classify both classes accurately.  As expected we saw a substantial improvement in the model's balanced accuracy and recall scores. It is important to note however that implemented balanced class_weight only resulted in a marginal improvement to the model's accuracy and precision.

#### Visualizations:

### Future Considerations:

#### Contributors:
- Erica Graboyes
- Chris Johnson
- Daniel Lee
- Lacey Morgan
- Kevin McMurphy
