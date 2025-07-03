**Project Overview**
**Data Preparation**
The project begins with comprehensive data preparation. The raw dataset is imported and initially examined for inconsistencies, missing values, and outliers. Specific outliers, such as records from the United Arab Emirates (ARE), are excluded to avoid skewed model performance. Only relevant numerical features are selected for modeling, including metrics such as cereal yield, foreign direct investment as a percentage of GDP, gross national income per capita, energy use per capita, urban agglomeration percentages, protected land areas, population growth rate, and urban population growth rate. These features are chosen based on their potential influence on carbon emissions. The dataset is then split into training and testing subsets, ensuring that the model can be evaluated on unseen data.

**Data Exploration**
To gain a deeper understanding of the selected features and their trends over time, exploratory data analysis is performed. A key part of this analysis involves calculating the Compound Annual Growth Rate (CAGR) for each important feature from 1991 to 2008 across a set of countries: India, USA, Pakistan, Russia, and New Zealand. This analysis reveals economic and environmental progress—such as increases in cereal yield and energy use—as well as urbanization trends and protected area expansion. Notably, while developed nations like the USA show a slight decline in energy usage, developing nations such as India and Pakistan demonstrate strong growth, suggesting future increases in emissions. These insights are used to simulate future values of the same features for forecasting.

**Feature Selection and Model Training**
Feature selection is performed using Recursive Feature Elimination with Cross-Validation (RFECV), a technique that iteratively removes less important variables and retains the most impactful ones based on model performance. This step significantly reduces dimensionality, mitigates multicollinearity, and enhances the generalization of the model. Following feature selection, a Random Forest Regressor is trained using the selected features. The model is optimized with RandomizedSearchCV, which tests various hyperparameter combinations through cross-validation to find the configuration that yields the highest R² score. The finalized model demonstrates excellent predictive ability, achieving a cross-validated R² score of 0.986, indicating that the model explains nearly all the variance in the data.

**Model Evaluation**
After hyperparameter tuning, the optimized model is validated on the test subset. Performance metrics such as R², Mean Squared Error (MSE), and Root Mean Squared Error (RMSE) are calculated. A regression plot is used to visualize the correlation between actual and predicted CO₂ emission values. The evaluation results show that the model performs with a high level of accuracy and consistency, without signs of overfitting, as evidenced by the narrow standard deviation across cross-validation folds.

**Forecasting CO₂ Emissions**
Using the calculated CAGR values for each country-feature pair, the model simulates feature growth for the next 20 years. These projected values are then used as input to the trained model to forecast CO₂ emissions per capita from the most recent year in the dataset up to the year 2048. Forecasts are generated for each selected country and plotted over time to visualize future trends. The visualization shows that developed nations like the USA and Russia may experience declining emissions due to more efficient technologies and policies, whereas developing countries are projected to see an upward trend, aligning with economic growth and energy demand.

**Technologies Used**
**Programming Language:** Python
**Libraries:** Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn, Joblib
**Machine Learning:** Random Forest Regression, Recursive Feature Elimination (RFECV), Hyperparameter tuning with RandomizedSearchCV
**Visualization:** Regression plots, time-series forecasts using seaborn/matplotlib
