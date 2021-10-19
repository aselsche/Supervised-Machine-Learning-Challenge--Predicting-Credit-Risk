![image](https://user-images.githubusercontent.com/84043141/137827209-cd0d61b8-3a5f-4cb4-8ff6-280ef30ab709.png)

# Supervised-Machine-Learning-Challenge--Predicting-Credit-Risk
Using this data to create machine learning models to classify the risk level of given loans. Specifically, comparing the Logistic Regression model and Random Forest Classifier.

# Background
LendingClub is a peer-to-peer lending services company that allows individual investors to partially fund personal loans as well as buy and sell notes backing the loans on a secondary market. LendingClub offers their previous data through an API.

# Steps
1. Prepare and clean the data
In the Generator folder in Resources, there is a GenerateData.ipynb notebook that will download data from LendingClub and output two CSVs:
        - 2019loans.csv
        - 2020Q1loans.csv
I used entire year's worth of data (2019) to predict the credit risk of loans from the first quarter of the next year (2020).

2. Preprocessing: Convert categorical data to numeric
I created a training set from the 2019 loans using `pd.get_dummies()` to convert the categorical data to numeric columns. Similarly, created a testing set from the 2020 loans, also using `pd.get_dummies()`.

3. Develop models
This analysis is trying to find the best model that can detect if a loan is high risk or not. To come up with a solutiom, I will be using the following models: a LogisticRegression and RandomForestClassifier. Before they were created, I fit, and scored the models.  The logistic regression will be a better suited model for this credit risk case, which has relatively direct data. The Logistic regression does well on highly correlated data which is true in this case. The random forest fits a number of decision tree classifiers on various sub-samples of the dataset and uses averaging to improve the predictive accuracy and control over-fitting. But in this case, using the random forest will be overfitting.

4. Fit a LogisticRegression model and RandomForestClassifier model
I created a LogisticRegression model, fit it to the data, and printed the model's score. I did the same for a RandomForestClassifier.  Logistic Regresion is good about taking all columns and finding the equation.  Before scaling the data, the score was: 0.50 (Test), 0.65 (Train). Then, RandomForestCLassifier was used. Random forest is really good about finding odd but strong predicitive patterns. I did the same steps here: 0.70 (Test), 0.72 (Train). 

5. Revisit the Preprocessing: Scale the data
Then, I scaled the data because it allows the data to be normalized to train the model, which I did by calling the transform() function. After training the Logistic Regression model on the scaled data, it is no longer over-fitting and we went from 50%  to 81%: 
0.81 (Test), 0.71(Train)
After training the RandomForestCLassifier on the scaled data, the model score was:
0.69 (Test), 0.73 (Train).

4. Conclusion
In conclusion, I think logistic regression is more fitted for this specific Credit Risk Case because the credit risk dataset is strongly linked together and highly correlated. Logistic regression is great in identifying direct data connection. 
In general, Random Forest and other ensemble methods reduce the prediction variance to almost nothing, improving the accuracy of the ensemble.Every model with high complexity can overfit and in this case, I think Random Forest will overfit. 
