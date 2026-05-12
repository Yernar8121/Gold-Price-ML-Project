# Gold Price Prediction: A Machine Learning Research Summary

## Project Overview and Philosophy

This project focused on using machine learning to forecast daily gold prices. The goal was not only to build a predictive model, but also to understand the challenges of financial time series prediction, especially market noise and data leakage.

A major part of the research was finding the most mathematically sound way to frame the problem. Instead of simply testing models, we carefully examined what the models were allowed to know and whether their predictions reflected real learning or hidden leakage from future information.

## Data Validation and Leakage Prevention

To avoid data leakage, we removed autoregressive features such as today’s gold price when predicting future absolute prices. This ensured that the models could not “cheat” by relying on information that would make the task unrealistically easy.

For model tuning, we used `TimeSeriesSplit` instead of standard cross-validation. This allowed the data to be split chronologically, meaning the models were always trained on past data and tested on future data. As a result, the evaluation process better reflected real-world forecasting conditions.

## The Three Experimental Approaches

We tested three different approaches to predicting the gold market. Each approach helped us better understand the strengths and limitations of machine learning in this context.

### Approach 3: Predicting Absolute Price

In this approach, the models were asked to predict tomorrow’s exact gold price using only independent features such as volume and volatility, without knowing today’s price.

The result was a very large prediction error. This showed that without knowing the current price level, machine learning models cannot reliably estimate the absolute value of an asset. In financial markets, the current price is a critical reference point.

### Approach 2: Predicting Price Delta with Regression

Next, we shifted the target from predicting the exact future price to predicting the dollar change in price for the next day.

This approach produced an error of approximately **18.90**, which was slightly worse than the naive baseline of **18.78**. The naive baseline simply predicted zero change every day.

This result showed that predicting the exact size of a daily price movement is extremely difficult. In this case, assuming no change was slightly more effective than trying to forecast the exact price swing.

### Approach 1: Predicting Market Direction with Classification

Finally, we simplified the task by predicting whether the price would move **up** or **down** the next day.

This was the most successful approach. The Random Forest Classifier achieved an accuracy of **53.90%**, beating the naive baseline. Although the improvement was modest, it suggested that predicting the general direction of the market is more realistic than predicting the exact price or exact price change.

## Model Selection Strategy

We designed the modeling process as a comparison between simple and complex algorithms.

Logistic Regression and Ridge Regression were used as linear baseline models. These helped us test whether simple mathematical relationships were enough to explain the target variable.

Random Forest and Gradient Boosting were used to capture more complex, nonlinear patterns in the market. These models were also useful because they are more robust to outliers and can handle interactions between features more effectively.

## Key Conclusion

The main finding of this research is that the way a financial forecasting problem is framed matters more than the complexity of the model itself.

Predicting the exact future price was not realistic without including the current price. Predicting the exact price change was also difficult and did not outperform a simple baseline. However, predicting the direction of the market showed measurable improvement, making classification the most promising approach in this project.

Overall, the project demonstrated that successful machine learning in financial markets depends heavily on careful data validation, leakage prevention, realistic baselines, and choosing the right prediction target.
