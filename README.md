Gold Price Prediction A Machine Learning Research Summary

Project Overview and Philosophy
This project is a comprehensive machine learning research on forecasting daily gold prices. The primary goal was not just to build a predictive model but to deeply analyze market noise and prevent data leakage. We wanted to discover the most mathematically sound way to frame a financial time series problem.

Data Validation and Leakage Prevention
To ensure our models were learning real patterns rather than cheating we strictly removed autoregressive features like todays price when attempting to predict absolute future values. For model tuning we abandoned standard Cross Validation in favor of TimeSeriesSplit. This guaranteed that our models were trained and tested strictly chronologically and never looked into future data.

The Three Experimental Approaches
We tested three different ways to predict the market evolving our strategy based on the results.

Approach 3 Predicting Absolute Price
We asked the models to predict tomorrows exact gold price using only independent features like Volume and Volatility without knowing todays price. The result was a massive error because without knowing where the price is today machine learning cannot guess the absolute value of an asset.

Approach 2 Predicting Price Delta Regression
We shifted to predicting the exact dollar change for tomorrow. The results achieved an error of approximately 18.90 which slightly underperformed the Naive Baseline of 18.78 which simply predicted zero change every day. This proved that trying to predict the exact amplitude of a price swing is less efficient than assuming no volatility.

Approach 1 Predicting Market Direction Classification
We simplified the task to predicting if the price would go UP or DOWN. Our Random Forest Classifier successfully beat the naive baseline achieving an accuracy of 53.90 percent. This proved that predicting the general vector of the market is possible.

Model Selection Strategy
We structured our modeling as a competition between Simple and Complex algorithms. We used Logistic Regression and Ridge Regression as linear sanity checks to see if simple equations could solve the problem. We used Random Forest and Gradient Boosting to capture complex nonlinear market conditions and remain robust against market outliers.
