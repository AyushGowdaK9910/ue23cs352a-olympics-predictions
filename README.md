# ue23cs352a-olympics-predictions
Mini-project to predict Olympic medal counts using machine learning.<br>
Dataset references:
1. https://www.kaggle.com/datasets/theworldbank/world-development-indicators
2. https://www.kaggle.com/datasets/heesoo37/120-years-of-olympic-history-athletes-and-results


Machine Learning Project Report: 2020 Summer Olympics Medal Prediction
Ayush K Gowda(PES1UG23CS124)
Likitha H(PES1UG24CS810)
1. Problem Statement
The goal of this project is to develop a machine learning model capable of estimating the total medal count for each participating country in the Summer Olympic Games (specifically predicting the 2020/2021 Games using 2016 data for testing). The challenge lies in accurately predicting a non-negative count variable with a large concentration of zero values (countries winning no medals). This is framed as a regression problem where macro socio-economic indicators (GDP, population, etc.) and historic performance are used as features.
2. Methodology: A Two-Phase Approach
Recognizing the "point mass at zero" issue (many countries win zero medals), a standard regression model (like Poisson or Linear Regression) struggles. The solution implemented is a two-stage hybrid model:
1.	Phase 1: Binary Classification
o	Objective: Predict whether a country will win any medals () or no medals ().
o	Models Explored: Logistic Regression, Support Vector Classification (SVC), Gaussian Naive Bayes, Multilayer Perceptron (MLP), and Random Forest Classifier.
2.	Phase 2: Regression
o	Objective: For countries predicted to win medals in Phase 1, accurately predict the exact number of medals they will win.
o	Models Explored: Linear Regression (as baseline/weighted), Ridge, Lasso, Poisson Regression, Support Vector Regression (SVR), and Random Forest Regressor.
3.	Data & Feature Engineering:
•	Datasets: Olympic results (Kaggle) merged with World Development Indicators (World Bank).
•	Data pre-processing involved resolving country name discrepancies, removing entries with null data, and keeping only games from 1988 onwards.
•	Key engineered features included Medals Last Games, GDP, Population, and ratios like medals_per_athlete and relative_medal_share. Simple linear kernels were generally found to be the most effective, despite testing complex kernels like RBF and Polynomial.
4. Results & Conclusion
The final selected model combination demonstrated a significant improvement over the unclassified linear regression baseline (which had an average standard deviation of ).
 
The successful deployment of the two-phased approach effectively addressed the challenge posed by the zero-inflated nature of the medal count data, resulting in a robust predictive model.
5. Challenges and Future Work
•	Data Sparsity/Quality: Removing all training examples with null data significantly reduced the available training set size. Future work should implement imputation techniques to retain more data.
•	Feature Completeness: Including data from years between the Olympic games would provide richer time-series information for the models.
•	Objective Function Optimization: A multi-objective optimization function that simultaneously weights the overall accuracy (Eq. 1) and the accuracy of predicting top-performing countries (Eq. 2) would lead to a more purposeful model selection than the current qualitative combination.

