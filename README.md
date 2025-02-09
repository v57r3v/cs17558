java c
Data Science in Economics 
(Econ 337) 
Mock Assignment 
Guidelines
1. The submitted file must be a Jupyter notebook (which, note, can be written through Google Colab, MyLab, or your own local installation of Python and Jupyter, respectively).
2. There is no word limit, however I urge you to present (and interpret whenever possible) the relevant results of your analysis with brevity and precision.
Data 
The data file “labour supply.csv” (which, note, you can download on the ”Econ 337 – Mock Assign-ment (Week 13)” section of the course’s Moodle page) includes a dataset with samples of women with at least two children in the United States.
These are some of the variables that you will encounter in “labour supply.csv”:
kids: total number of kids
boys2 : = 1 if the first two births boys
girls2 : = 1 if the first two births girls
boy1st: = 1 if the first birth boy
boy2nd : = 1 if the second birth boy
multi2nd : =1 if 2nd birth is twin
age : age of mom
agefstm : age of mom at first birth
black : =1 if black
hispan : =1 if hispanic
worked : = 1 if mom worked last year
weeks : number of weeks worked, mom
hours : hours of work per week, mom
labinc : mom’s labor income, in thousands of dollars
faminc : family income, in thousands of dollars
nonmomi : ‘non-mom’ income, in thousands of dollars
educ : years of education for mother
To start, import “pandas” and “numpy”:
import pandas a s pd
import numpy a s np
After, load “labour_supply.csv” as a pandas data frame.
labour_supply = pd . readcsv (labour_supply . csv)
Lastly, run the following code to select a random subset of observations:
np . random . seed (your_student_id)
a1 = np . random . choice (labour_supply . shape [0] , \\
10000 , replace=False)
train_data = labour_supply . iloc [a1, :]
This newly drawn dataset of 10,000 observation will be your training sample.
Important: You have to insert your actual student ID number in “your student id”...
... for example, you should use np.random.seed(84377968) if your ID is 84377968.
Exercises 
Read each question carefully and answer to ALL questions:
(a) Using your training data, report summary statistics (in a table format – printed, you do not need to save a table in a separate file) of hours, kids, age, faminc, edu, labinc, and black.
In addition, create a scatterplot matrix of the same set of variables. Draw the histogram of the hours (with the percentage in y-axis). Describe your findings. Are any of the predictors associated with hours?
[hint: search on Google how to estimate each type of plot using matplotlib.pyplot] (20 marks)
(b) Again, using your training data , generate a dummy variable morekids that equals 1 if the total number of kids (kids) is larger than or equal to 3.
Produce boxplots of faminc (y-axis) over morekids (x-axis). Discuss your findings.
[Hint: review “econ337_tutorial_2 ” to know how to create dummy variables] (10 marks) 
(c) Using your training data, estimate the following two linear regression models:
Model 1 : hoursi = β0 + β1kidsi + ei
Model 2 : hoursi = β0 + β1kidsi + β2faminci + eis.
For each model, give a brief interpretation of the coefficient estimates and discuss whether the signs you obtain match your expectations. For the simple regression (Model 1), plo代 写Econ 337 Data Science in EconomicsPython
代做程序编程语言t hours and kids along with the least squares regression line.
Also, discuss how does the introduction of the variable faminc affects the estimated parameter on kids. What can you infer about the correlation between faminc and kids? Justify your response.
[Hint: review “econ337 tutorial 2 ” to estimate a linear regression model] (20 marks) 
(d) Using the regression results in (c), find the predicted work hours for a mother who has 3 kids and family income of 20,000$, and 95 % prediction interval.
[Hint: review “econ337 tutorial 2 ” to predict outputs from fitted models] (10 marks) 
(e) This question is composed by four sub-questions (all amounting to 30 marks):
(e.1) Run an OLS regression of hours on other control variables. Add whichever other controls you might think are appropriate and explain why your selected variables are important. (5 marks) 
(e.2) Select your regressors by following the “Forward Selection” algorithm (read p.24-26 in the lecture notes of Week 12 [“Linear Regression”] and see below for an explanation of the algo.):
Forward Selection - Algorithm:
(a) Begin with the null model - a model that contains an intercept but no predictors;
(b) Fit k (number of control variables) univariate linear regressions and add to the null model the variable that results in the largest Adjusted R-squared;
(c) Enlarge the model fitted in point (b) with the variable that results in the largest Ad-justed R-squared (amongst all possible two-variable models that include the variable found in point (b));
(d) Continue until some stopping rule is satisfied, for example when all remaining vari-ables have a p-value above some threshold (e.g., p-value > 0.1). (10 marks) 
(e.3) Select your regressors by following the “Backward Selection” algorithm (read p.24-26 in the lecture notes of Week 12 [“Linear Regression”] and see below for an explanation of the algo.):
Backward Selection - Algorithm:
(a) Start with all variables in the model;
(b) Remove the variable with the largest p-value - that is, the variable that is the least statistically significant;
(c) The new (k − 1) variable model is fit, and the variable with the largest p-value is removed;
(d) Continue until a stopping rule is reached (again, for instance, we may stop when all remaining variables have p-value smaller than 0.1). (10 marks) 
(e.4) Compare your results with “Forward Selection”, “Backward Selection” and the methods you have used in (e.1), based on your economic reasoning. (5 marks) 
(f) Choose (at least) three models with different choices of regressors (e.g., those models selected in (e) if these are all different), predicting hours, and fit these models using your 10,000 obs. training sample.
Then, select a validation dataset with 50 observations as follows:
np . random . seed (your_student_id ∗ 2 + 1)
a2 = np . random . choice (range (labour_supply . shape [ 0 ]) ,
50 , replace=False)
validation_data = labour_supply . iloc [a2]
Then, calculate the “Mean Square Prediction Error (or test MSE)” for the three models you selected (where you calculate the MSE by making predictions with each model using as inputs your 50-observation validation dataset).
Choose the model with lowest MSE. Discuss your findings. (10 marks) 









         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
