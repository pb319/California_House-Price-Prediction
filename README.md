# California_House-Price-Prediction
This is going to be my first end to end ML project implementation covering all required stages taking guidence from book called "Hands On Machine Learning"

## Table of Contents
- [Big Picture](https://github.com/pb319/California_House-Price-Prediction?tab=readme-ov-file#big-picture)
- [No Data Snooping](https://github.com/pb319/California_House-Price-Prediction?tab=readme-ov-file#no-data-snooping)
- [Exploratory Data Analysis](https://github.com/pb319/California_House-Price-Prediction?tab=readme-ov-file#exploratory-data-analysis)
- [Data Preparation](https://github.com/pb319/California_House-Price-Prediction?tab=readme-ov-file#data-prparation)
- [Model Selection and Training](https://github.com/pb319/California_House-Price-Prediction?tab=readme-ov-file#model-selection-and-training)
- [Model Fine Tuning](https://github.com/pb319/California_House-Price-Prediction?tab=readme-ov-file#model-fine-tuning)
- [Evaluation on Test Set](https://github.com/pb319/California_House-Price-Prediction?tab=readme-ov-file#evaluation-of-test-set)


## Big Picture

1. Problem Statement
   - Welcome to Machine Learning Housing Corporation!
   - Organiazationa Objective: Replacing expensive, time consuming and less effective manual prediction technique with Machine Learning
  
2. Framing the problem
   - Data: California Census Data 
   - A typical Univariate Multiple Regression task.
   - Training Set is labelled hence **"Supervised Learning"**
   - Data is small hence we shall opt for **"Batch Learning"**

2. Performance Measure
   - Root Mean Square Error (RMSE) - l<sub> 2 </sub> Norm
   - Mean Absolute Deviation (MAD) - l<sub> 1 </sub> Norm

## No Data Snooping

1. Get the Data
   - Overview and Primary Understanding
2. Test Set
   - Firstly employed **Simple Random Sampling** to draw a test & tarin set using `Scikit- Learn`
   - Sencondly utilized **Stratified Sampling** by categorizing the whole datase on `median_income`
   - Later we compared **Sampling Bias** from both the sampliing techniques


## Exploratory Data Analysis

1. Creating Viualizations
  ***
  ![Screenshot from 2024-06-06 10-24-13](https://github.com/pb319/California_House-Price-Prediction/assets/66114329/bf2a3d13-60e8-4af4-9cf3-01ed0fb864bc)

  ***
   * There is a celar depiction of clusters in and around San Diego, Los Angeles, San Feancisco, etc.
   * From the above figure we can see a general figure hou `ocean_proximity` is seems to be assocoated with `median_price_value`
   *  Bus still there are exceptions in North-California, so we've to deploy some **feature engineering** here as well.
   * Features such as **proximity to clusters** can also be checked.

  ***
 2. Correlation Matrix and Scatter Plot
  
   ![Screenshot from 2024-06-06 19-53-02](https://github.com/pb319/California_House-Price-Prediction/assets/66114329/91f2e71c-50a8-461b-9892-068e18e0f5a3)
   
   ***
   * In General it shows a strong positive trend.
   * Straight line at $500,000 reemphasize the **price_cap**
   * Concerns are afew straight line in and aroud `$450,000`, `$350,000`, `$280,000`, `$230,000` and so on in the below.
   * We may remove the concerned districts.

## Data Prparation

1. Data Cleaning

    * Missing value of `total_bedrooms` (1.01%) has been treated using **SimpleImputer** Class of Scikit Learn.
     
2. Handling Text Attribute
    * **OneHotEncoding** is used to handle `ocean_proximity` column

3. Feature Scaling and Transformation Pipeline
    * Laid down single transformation pipeline to transform both numeric and categorical attributes
    * StandardScaler(), ColumnTransformer() classes have been utilized.
  
## Model Selection and Training

1. Model Selection
   
   * `Linear Regression`, `Decision Tree Regressor`,`Random Forest Regressor` models has been **fitted on training set**.
   
3. Model Evaluation
   
   * "K-Fold Cross Validation" depicts RSME scores of **68973.98, 70100.86, 50639.61** respectively.
   * Random Forest Regressor looks very promising.
   * Note: Score on training set is still muchlower than on validation sets means **still overfitting the training set**.

## Model Fine Tuning

1. Grid Search Cross Validation
   
   * Deployed `GridSearchCV()` to fine-tune hyperparamentrs
   * Got --->  `RandomForestRegressor(max_features=8, n_estimators=30)`
   * RSME score slightly improved from 50646 to 50532 (K Fold Cross Validation)
  

## Evaluation of Test Set
   * K-Fold Cross Validation (RSME) score of `47330.19` having `[45321.16526478, 49257.3427213]` confidence interval with 5% level of Significance.





***


## To be continued...
