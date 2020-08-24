# Classifying Online Shoppers Intentions (Revenue vs No Revenue) - Metis Project 3 
Rudy Wang

## Background

For a classification project, I wanted to develop a stronger understanding of how data analysis can assist an online business's revenue generation from its unique visitors. My background in financial risk and compliance has never been about making money for a client - I wanted to better understand what kind of data can help a an online business interpret its potential buyers accurately. The dataset I will be using is from [Kaggle](https://www.kaggle.com/roshansharma/online-shoppers-intention) with features of the dataset belonging to Google Analytics.

## Mission

To classify visitors accurately to either be someone who will buy something off the site or not. We will see which features matter the most to determining a buy, so we can push recommendations to our client on what parts of the online business should focus on having the biggest impact on purchasing decisions.

## Process

1. Constructed and cleaned (removed nulls, outliers) a dataframe to hold the CSV dataset within Jupyter Notebook.
2. Determined Page Values to have the strongest correlation to my target variable. Decided to explore how including and not including Page Values can affect my classification score. (Page Values will be further explained below)
3. Model selection will be focused on finding the highest F1 Score since the costs of False Positives and False Negatives are equally as important when looking to see which features would yield high True Positives and True Negatives.
4. Compare the results of F1 scores between the best model selected for Features including Page Values vs Features without Page Values.

## Page Values

Page Value as a feature is derived from Google Analytics. According to [Google Analytics](https://support.google.com/analytics/answer/2695658?hl=en#:~:text=Page%20Value%20is%20the%20average,more%20to%20your%20site's%20revenue.), page value is the average value for a page that a user visited before landing on the goal page or completing an Ecommerce transaction (or both). In this dataset, the page value number is the average of all pages that a user visited before landing on the goal page, which intuitively would mean that all visitors who ended up purchasing the service/product will have a higher page value than vistors that did not. 

Due to the strong bias page values would have on my classification models, I ultimately decided to find two models to see the top features that matter when Page Value is included and when Page Value is not included. 

## Conclusion

For both models with and without Page Values, the Logistic Regression had a high F1 score with the highest amount of interpretation of the coefficients.

For Logistic Regression with Page Values, only two features mattered to produce the best score: Page Values and Exit Rates (F1 Score of 0.68).

For Logistic Regression without Page Values, all features had to be put into the model to produce a high F1 score. The top three highest features are Product Related Duration, Month of the Visit, and Exit Rates (F1 Score of 0.37). Although the XGBoost model produced better scores, the confusion matrix is a completely different story (only 11 True Positives, with 335 False Positives). 

It's quite clear that without Page Values, the classifier model suffers greatly - it is the singular most important feature within the dataset for my target variables to be accurate. 

## Further Work

Page value setup is the most critical value when it comes to classifying a visitor's online shopping habit. But this dataset was limited in its scope to allow me to investigate which specific pages would matter the most to the website. Furthermore, if we knew the page values for the different pages setup, we could have potentially removed the final goal page with the highest page value, so we could examine which other pages led the visitor to the final transaction page. 

Ultimately, a recommendation of which kind of pages grabbed the visitor's attention to continue browsing the site would have been the best result to come out of this project. 

## Tools

- Jupyter Notebook
- Scikit-Learn
- Pandas
- Matplotlib
- Seaborn
- Tableau
