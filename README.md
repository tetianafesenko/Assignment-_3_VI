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
