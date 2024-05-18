# Project 2 - Unlocking Property Potential with Predictive Pricing


## **Problem Statement**

A Real State company, with a focus on developing and acquiring properties in Old Town, Ames, Iowa, has initiated a project with two primary objectives. Firstly, to develop a predictive model capable of accurately forecasting house prices. Secondly, to identify key house features that significantly influence housing prices. By achieving these goals, the project aims to facilitate optimized investments and maximize returns for the company.

## **Data Dictionary**

The datasets contains information from the Ames Assessor’s Office used in computing assessed values for individual residential properties sold in Ames, IA from 2006 to 2010. <https://www.cityofames.org/government/departments-divisions-a-h/city-assessor>

The Data dictionary contains some of features that were observed to have a high correlation with housing Sale Price. The full Data dictionary can be found here: <https://jse.amstat.org/v19n3/decock/DataDocumentation.txt>

| Feature | Type | Description |
| :--- | :--- | :--- |
| Overall Qual| Ordinal  | Rates the overall material and finish of the house |
| Gr Liv Area | Continuous | Above ground living area square feet |
| Garage Cars | Discrete | Size of garage in car capacity |
| Garage Area | Continuous | Size of garage in square feet|
| Total Bsmt SF | Continuous | Total Square feet of basement area |
| 1st Flr SF	| Continuous | First Floor square feet |
| Exter Qual_TA | Engineered | Average/typical quality of the material on the exterior  |
| Year Built	| Discrete | Original construction date |
| Year Remod/Add | Discrete | Remodeled date, samme as construction date if not remodeled |
| Full Bath | Discrete | Full Bathrooms above ground |
| Kitchen Qual_TA | Engineered | Average kitchen quality |
| Foundation_PConc	 | Engineered | Poured Concrete foundation |
| TotRms AbvGrd	 | Discrete | Total rooms above ground, not including bathrooms |
| Mas Vnr Area	 | Continuous | Masonry veneer area in square feet|
| Garage Finish_Unf	 | Engineered | Indicates if garage is finished or unfinished |
| Garage Yr Blt | Discrete | Year garage was built |
| Fireplaces | Discrete | Number of fireplaces |
| BsmtFin Type 1_GLQ	 | Engineered | good rating basement finished area |
| Bsmt Qual_TA	 | Engineered | Typical basement quality |
| 'Garage Type_Detchd' | Engineered | Garage detached from house |


## **Executive Summary**

In the search of the best predictive model, I followed the following steps: 

*Data Cleaning*

The first step was to conduct an analysis on the dataset. Columns with missing values exceeding 50% of the total values were eliminated. For the remaining columns with missing values, numerical variables were imputed with the mean, while categorical variables were filled with values derived from other columns. 

*Feature Engineering*

Categorical variables were transformed to expand them into a binary format using One-Hot Encoding. This enhanced the model's capacity to interpret and utilize categorical data effectively. 

*Modeling*

Following an examination of correlations between house features and prices, I initially developed a Linear Regression model using 20 variables. While this model showed decent performance, it tended to deviate by roughly $30k in predictions, particularly for houses priced over $350k.

To enhance the model's predictive capability, I explored the addition of more features. Comparing root mean squared errors (RMSE) suggested that this indeed improved performance. Subsequently, I fitted another Linear Regression model with all available features, resulting in a considerable improvement with a variability of 0.93%. However, it still struggled with accurate predictions for houses priced above $350k.

In an effort to further refine the model, I implemented a Pipeline and cross-validation approach. Utilizing a loop, I evaluated three Linear Regression models - Linear Regression, Lasso, and Ridge - each employing the same 20 features as the baseline model. Polynomial features ranging from degree 1 to 3 were applied, along with cross-validation using 3 folds. Though Lasso and Ridge were anticipated to perform best with polynomial features of degree three and alpha hyperparameters of 100 and 1000 respectively, computational limitations prevented their testing.

Subsequently, I evaluated Ridge and Lasso with 100 features, both with polynomial features and alpha hyperparameters, both still falling short for house prices above $350k. The Lasso model exhibited considerable signs of overfitting. While the Ridge model showed a slight risk of overfitting, it closely paralleled the performance of the Linear Regression model. Consequently, it was determined that the latter model performed the best.


## **Recommendations**

Based on the analysis of house features impacting prices in Old Town, several recommendations can be made to stakeholders when deciding which houses to purchase:

* Houses with more recent construction are considerably more expensive, thus it is advisable to focus on purchasing properties built before then
* The number of full bathrooms above ground increase sale price considerably, about $6,285 per bathroom 
* Properties featuring fireplaces exhibit a notable increase in value, with prices rising by approximately $5,205 per fireplace
* The number of cars a garage can accommodate directly influences the property's price, with each additional car space contributing approximately $3,688 to the overall value
* Houses with a greater number of rooms above ground experience a price boost, with an increase of approximately $600 per additional room

Identifying properties that align with these key features can serve as ideal investment opportunities, potentially offering higher returns and increased market demand. By leveraging these insights, stakeholders can make informed decisions when selecting investment properties in Old Town. 