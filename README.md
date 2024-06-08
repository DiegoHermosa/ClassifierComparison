# Comparing Classifiers

### Overview
In this practical application, th objective is to compare the performance of the classifiers we encountered in this section, namely K Nearest Neighbor, Logistic Regression, Decision Trees, and Support Vector Machines. We will utilize a dataset related to marketing bank products over the telephone.

### Data:
The data can be found in this link: 

[bank-additional-full.csv](https://github.com/DiegoHermosa/ClassifierComparison/tree/main/data/bank-additional-full.csv)

Notebook Link
The following notebook contains all the development of the analysis carried out.

[prompt_III.ipynb](https://github.com/DiegoHermosa/ClassifierComparison/tree/main/prompt_III.ipynb)

### Business Understanding
The task is intended to understand what drives a customer to accept or not subscribing a bank term deposit and to verify which are the features that most influence this decision. For this purpose, a dataset of 41187 records has been provided from which information has been collected on several characteristics related to the customer. The data represents 17 marketing campaigns which were done during May 2008 until Nov 2010.

### Data Understanding
Next we have the dataset feature descriptions, we can see the input variables section where the feature have been organized in several categories according to the source of the information they represent: bank client data, last contact, other attributes, social and economic context. As the output variable we have the "y" feature which stores the customer's decision about be subcribed or not to the bank product.

#### Input variables:

- **Bank client data:**<br/>
  **1. age** (numeric) <br/>
  **2. job**: type of job (categorical: 'admin.','blue-collar','entrepreneur','housemaid','management','retired','self-employed','services','student','technician','unemployed','unknown') <br/>
  **3. marital**: marital status (categorical: 'divorced','married','single','unknown'; note: 'divorced' means divorced or widowed) <br/>
  **4. education**: (categorical: 'basic.4y','basic.6y','basic.9y','high.school','illiterate','professional.course','university.degree','unknown') <br/>
  **5. default**: has credit in default? (categorical: 'no','yes','unknown') <br/>
  **6. housing**: has housing loan? (categorical: 'no','yes','unknown') <br/>
  **7.l oan**: has personal loan? (categorical: 'no','yes','unknown') <br/>
  
- **Related with the last contact of the current campaign:**<br/>
  **8. contact**: contact communication type (categorical: 'cellular','telephone') <br/>
  **9. month**: last contact month of year (categorical: 'jan', 'feb', 'mar', ..., 'nov', 'dec') <br/>
  **10.day_of_week**: last contact day of the week (categorical: 'mon','tue','wed','thu','fri') <br/>
  **11. duration**: last contact duration, in seconds (numeric). Important note: this attribute highly affects the output target (e.g., if duration=0 then y='no'). Yet, the duration is not known before a call is performed. Also, after
  the end of the call y is obviously known. Thus, this input should only be included for benchmark purposes and should be discarded if the intention is to have a realistic predictive model. <br/>
  
- **Other attributes:**<br/>
  **12. campaign**: number of contacts performed during this campaign and for this client (numeric, includes last contact) <br/>
  **13. pdays**: number of days that passed by after the client was last contacted from a previous campaign (numeric; 999 means client was not previously contacted) <br/>
  **14. previous**: number of contacts performed before this campaign and for this client (numeric) <br/>
  **15. poutcome**: outcome of the previous marketing campaign (categorical: 'failure','nonexistent','success') <br/>
  
- **Social and economic context attributes:**<br/>
  **16. emp.var.rate**: employment variation rate - quarterly indicator (numeric) <br/>
  **17. cons.price.idx**: consumer price index - monthly indicator (numeric) <br/>
  **18. cons.conf.idx**: consumer confidence index - monthly indicator (numeric) <br/>
  **19. euribor3m**: euribor 3 month rate - daily indicator (numeric) <br/>
  **20. nr.employed**: number of employees - quarterly indicator (numeric) <br/>
  
#### Output variable (desired target):
- **21. y**: has the client subscribed a term deposit? (binary: 'yes','no') <br/>

### Data Preparation and Cleaning
- Data has no missins values.
- For the categorical features we will the TargetEncoder and OrdinalEncoder to encode their values, this features are:<br/>
  - job, marital, education, default, housing, loan, contact, month, day_of_week, poutcome<br/>
- The dataser is imbalanced: <br/>
  ![image](https://github.com/DiegoHermosa/ClassifierComparison/assets/160977826/d1b95e56-394b-4e1d-8f79-73fc6113e197)

### Classifier comparison
For the Classifier Comparison, we ran the classifiers in two ways: 
- Simple model execution using the dataset's bank client data features(columns 1 to 7) only and simple models with default parameters.
- Improved models with almost all the features excepting those removed after analysing the correlation matrix.
 
### Simple data and model
In this stage we will use the basic data (features 1 to 7) and run the classification model with the defalt parameters and see the accuracy score behaves.

### Improving data and model
In this stage we will use more feature and run the classification model with more paramerers and performance metrics

### Findings
1. During this practical application we applied two approaches: one is the basic, with fewer features(bank client data) and simple models, this gave us an initial idea of the data behavior vs the target feature. Then we included more features, after a data correlation analysis we could discard some of them and by the dataset's documentation we removed others which did not make sense to have them in the analysis. This process was valuable because we were getting important insights about the data and about the objetive of the project.
2. By Using different Classification algorithms (KNN, Logistic Regression, Decision Tree and SVM) and comparing their performance results we got the best one for this particular dataset is Decision Tree, it got the best Recall and F1 score which are aligned to the objective to correctly identify the most of the subscribers (minimizing false negatives).  
3. The execution time and training time are factors which could impact on the decision to choose a Classification algorithm but we need to find a balance between those times and the scores we could get from the differents models. CRISP-DM allows to iteratively improve our data and the parameters to get the best performances.
4. Identify the most important featuures is a key part in the understanding of the prediction, by analysing their data distribution and relation to the target feature (subscribed) we could determine why the customer took the decision to accept the bank term deposit, for example:
- Euribor3m (Euribor 3 month rate - daily indicator)
- Month (Last contact month of year)
- Pdays (Number of days that passed by after the client was last contacted from a previous campaign)

### Next Steps and Recomendations
1. Improve the Classification process by adding tools to handle the imbalanced dataset, as we can see, this dataset is imbalanced which yields some metrics can be misleading between them. One improvement we could do in this process the Resampling Techniques:
- Oversampling: Duplicate samples from the minority class to increase its representation.
- Undersampling: Remove samples from the majority class to balance the dataset.
- SMOTE (Synthetic Minority Oversampling Technique): Generates synthetic data points for the minority class.

2. Analyse the the other features, for the scope of this project, we reviewed the top 3 features, the others need to be analyzed to get more valuable information.

### References
- The dataset comes from UCI Machine Learning repository [link](https://archive.ics.uci.edu/ml/datasets/bank+marketing).  The data is from a Portugese banking institution and is a collection of the results of multiple marketing campaigns




