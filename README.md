# Assignment-_3_VI

Homework 3 - Regression Models
We will be exploring an medical cost dataset with various demographic and health information on patients. We can tackle 2 main ideas in supervised learning: (1) regression and (2) classification.

For a regression task, the goal is to predict medical costs (based on insurance claims) using a linear regression model.
For a (binary) classification task, the goal is to predict if the insurance beneficiary is a smoker or a non-smoker with a logistic regression model.


### Exploratory Data Analysis (EDA)

There are 1338 individual datapoints with 7 columns or features in the dataset:

age: age of the primary beneficiary
ratio (continuous variable)
sex: sex of the beneficiary (male or female)
nominal (categorical variable)
bmi: body mass index; a value derived from the mass and height of the beneficiary
interval (continuous variable)
children: number of children covered by the insurance
ratio (discrete variable)
smoker: whether the beneficiary smokes or not (yes or no)
nominal (categorical variable)
region: residential area of the beneficiary in the U.S.
nominal (categorical variable)
charges: individual medical costs billed by the insurance
ratio (continuous variable)
int64 refers to integer numbers; float64 refers to floating point numbers; and object refers to texts or alphanumeric values.

Luckily there are no missing datapoints in the dataset. Missing data can be problematic when carrying out data analysis. To combat this, we can either drop the entire row or use data imputation strategies where the missing value is replaced by a substituted value.

There is one duplicated row and will be removed accordingly.

### Data visualization
In addition to the descriptive statistics, visualizing the distribution of the data can provide additional information on the data itself and can guide us in how to carry out the analysis appropriately.

The distribution appears to be non-Gaussian and positively skewed (or right skewed). We can formally test the normality with the Shapiro–Wilk test and can confirm that the distribution is indeed not normal.

***Note, normality is a condition for regression models.

While it is not always necessary to transform data, it often helps with interpretability and to meet certain assumptions for statistical inference. In our case, we will be using the Box-Cox transformation.


Correlation coefficient values below 0.3 are considered to be weak; 0.3-0.7 are moderate; >0.7 are strong. In this case, all correlations are 0.3 or below, so we can conclude that the variables are independent from one another.


### Question 3A

Plot the distribution of independent variables "sex", "smoker" and "region"
Plot the relationship between the independent variables (sex, smoker, region) and the dependent/target variable (charges)
Initial thoughts on above plots:

It appears that there may be sex differences in the medical costs; in particular, male, on average, spends more on medical procedures. However, since the error bars do overlap, we cannot make a solid conclusion.
Not surprisingly, medical costs are likely to be higher for smokers, compared to non-smokers.
Interestingly, where one lives seems to have an effect on the medical costs. Most likely due to the differences in the state law, healthcare policies, and lifestyle of individuals living in different regions within the U.S.

### Preprocessing

Given that we wish to use a regression model and some of the features are non-numeric, we must transform them via feature encoding. There are several encoding strategies and can vary depending on the nature of the feature (i.e., nominal vs. ordinal). In our case, we will be using a simple label encoder that turns the target labels to values between 0 and n_classes-1.

### Modelling
We have more or less completed the heavy lifting already. Contrary to popular belief, most of data science and AI (machine learning) is about exploring data and feature engineering (i.e., cleaning up data). That said, we are ready to define the model, train the model, make predictions, and evaluate the performance of our model.

### Linear regression
https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LinearRegression.html

In this section, we will build a Linear Regression model to predict the amount of charges (medical costs) based on an individual's age, BMI, number of children, sex, whether they are a smoker, and what region they live in.

### Build the model

We will first split the dataset into different datasets: (1) training set; and (2) test set. When we develop a model, we train the model using the samples in the training set. Once the model has learned, we evaluate the performance of our model with the samples in the test set. By testing on unseen data, we minimize the bias of our model and can accurately estimate the generalizability and predictive power of our model. Here, we will split the dataset into 90% training set and 10% test set. Other typical splits includes 70-30 split, 80-20 split, etc.
