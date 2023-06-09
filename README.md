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

### Visualizations ###

### Project Implementation - Data Cleansing:
We loaded the raw csv file to jupyter notbook and used Spark to clean and transform the underlying dataset.  As part of the data cleanse process we dropped the row number, customer id and surname fields from the raw data. The cleansed data was exported to a separate csv file and used in the subsequent notebooks where we developed and optimize the machine learning models.
### Project Implementation - Developing a machine learning model:
We loaded the cleansed dataset into a separate jupyter notebook (model_exploration) where we evaluated both the skewness and kurtosis of the independent variables.  We grouped the independent variables into numeric and categorical groups and encoded the categorical variables using one-hot encoding. Next we created our features (independent variables) and target (dependent) variables and used train_test_split to split the data.

We used a function to train and test several different models and then analyzed the initial model results based on their accuracy score 

[Insert model table and accuracy]

Even though the initial model accuracy was not as impressive as other models, we decided to use a logistic regression model to predict customer churn -- to see if we could optimize the model's performance using various machine learning techniques.  We also aligned that given the colinearlity between exited and complain we should remove the "Complain" variable when building the regression model as the variable created quasi-causation. If the variable had captured number of complaints instead of a binary output we would have reconsidered excluding it the next phase of the project. 
### Project Implementation - Optimizing and Tuning Machine learning model:
We started wth a simple baseline logistic regression. The baseline model did not account for resampling (in spite of the imbalanced sample) or standard scaling.  We felt it was important to establish a baseline for model performance, understanding that we would ultimately layer on additional considerations for standard scaling and sampling bias.  While the baseline model demonstrated decent accuracy, the balanced accuracy score dropped considerably. While the precision score (prediction true positives) was "tenible" the recall score of .05 was quite discouraging when considering the model's overall performance.

Given the sub-optimal performance of the baseline model we set built-in class_weight method to balanced (class_weight = balanced). This method adjusts the class weight inversely proportional to their respective frequencies..so that model is effectively more 'aware' of underrepresented classes.  We thought that by increasing the model's awareness of the under-represented classes it would improve the model's ability to classify both classes accurately.  As expected we saw a substantial improvement in the model's balanced accuracy and recall scores. It is important to note however that implemented balanced class_weight only resulted in a marginal improvement to the model's accuracy and precision.

In addition to evaluating balanced class_weight, we also employed ADASYN (Adaptive Synthetic) sampling against the baseline model. Given the imbalanced target data we agreed that we needed to correct for the oversampling.  We decided on ADASYN because this technique generates synthetic data and adapts the dataset to focus on the data instances that are difficult to learn. Interestingly the results of the adaptive model were only marginally better than the logistic regression model with balanced class weight.

It is important to note that we had not scaled any of our numeric variables in the three initial logistic regression models.  We wanted to evaluate the impact of class_weights and resampling on the data based on the original values before deciding to implement scaling. We applied scaling to the resampled data, which lead to an improvement in all metrics, with the exception of recall. This occurred because scaling standardizes the features onto a uniform scale, thereby enhancing the model's ability to learn from the data. However, it does not directly influence the model's ability to identify the positive class, hence the stagnant recall rate.

Lastly, we utilized GridSearchCV for hyperparameter tuning. It used the 'liblinear' solver. This is an algorithm for small datasets and binary classification, and was likely preferred due to its efficiency with the dataset size and the problem at hand. As for the penalty parameter, the model opted for the L1 penalty, which introduces sparsity into the model, implying that it makes the coefficients of irrelevant features zero here is helping the model with feature selection. This is beneficial as it simplifies the model.
### Project Implementation - Part 2: Keras and TensorFlow:
In parallel to our logistic regression models we also built a Tensorflow model using Keras.  It is important to note that while the dataset has several categorical variables, we did not need to bin them before one hot encoding since there were only a few categorical variables within each variable. 

After running Keras Tuner, the best model was chosen and the data was fit and trained. The end results were acceptable, but not as good as hoped. The accuracy was lower than expected and dips throughout the fit process made us consider other options.

### Project Conclusion & Future Considerations:
Within this project onclusion starter: In this project, we've successfully leveraged the power of predictive modelling using the bank churn dataset. By iteratively refining a logistic regression model, we can effectively predict if a customer will leave the bank based on various features.
This model serves a dual purpose. Firstly, it can identify potential churn candidates early, enabling proactive intervention through targeted marketing or personalized service. Secondly, the model's interpretability assists strategic planning, helping pinpoint areas for improvement. For instance,  as the 'number of products' strongly predicts churn, the bank could strategize to engage customers with a wider range of services.
The model developed not only meets performance benchmarks but also provides valuable insights, shaping customer retention efforts and bolstering the bank's market position, underscoring the immense value of data analytics in banking.

#### Contributors:
- Erica Graboyes
- Chris Johnson
- Daniel Lee
- Lacey Morgan
- Kevin McMurphy
