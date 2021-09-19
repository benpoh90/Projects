# Ben Poh Project 2: Prediction of Housing Sale Prices

### Introduction

The data is from the Ames Assessor’s Office used in computing assessed values for individual residential properties sold in Ames, IA from 2006 to 2010. It contains a range of **81 features** describing a property's characteristics. The target variable of this project will be 'SalePrice'.

---

### Problem Statement

You work for the local housing authority. Using the Ames housing dataset, your manager is keen to know how features of a property can determine its sale price. Your manager would also like to know if a better basement (size, quality, exposure etc.) will lead to a higher sale price.

---

### Datasets and Data Dictionary

#### Provided Data

There are two datasets included in the `datasets` folder. For the train dataset, I will be perfroming a further train/test split to get train/holdout sets to evaluate my models on (part 2). I will then be predicting sale prices from the test dataset by applying my model on the full train set again.


* [`train.csv`](../datasets/train.csv)
* [`test.csv`](../datasets/test.csv)

#### Data Dictionary

I have separated them into ordinal, nominal, discrete and continuous categories based on information from the [data dictionary](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt).

|Continuous|Categorical|Ordinal|Discrete|
|---|---|---|---|
|Lot_Frontage|MS_Zoning|Overall_Cond|Bsmt_Full_Bath|
|BsmtFin_SF_1|Street|Overall_Qual|Full_Bath|
|BsmtFin_SF_2|Alley|Lot_Shape|Year_Remod/Add|
|Bsmt_Unf_SF|Land_Contour|Utilities|Kitchen_AbvGr|
|Total_Bsmt_SF|Lot_Config|Land_Slope|TotRms_AbvGrd|
|Garage_Area|Neighborhood|Exter_Qual|Half_Bath|
|Lot_Area|Condition_1|Exter_Cond|Bsmt_Half_Bath|
|Gr_Liv_Area|Condition_2|Bsmt_Qual|Bedroom_AbvGr|
|Low_Qual_Fin_SF|Bldg_Type|Bsmt_Cond|Garage_Yr_Blt|
|1st_Flr_SF|House_Style|Bsmt_Exposure|Fireplaces|
|2nd_Flr_SF|Roof_Style|BsmtFin_Type_1|Mo_Sold|
|Wood_Deck_SF|Roof_Matl|BsmtFin_Type_2|Yr_Sold|
|Open_Porch_SF|Exterior_1st|Heating_QC|Year_Built|
|Enclosed_Porch|Exterior_2nd|Electrical|Garage_Cars|
|3Ssn_Porch|Mas_Vnr_Type|Kitchen_Qual||	
|Screen_Porch|Foundation|Functional||	
|Pool_Area|	Heating|Fireplace_Qu||	
|Mas_Vnr_Area|Central_Air|Garage_Finish||
|Misc_Val|Garage_Type|Garage_Qual||
||Misc_Feature|	Garage_Cond||	
||Sale_Type|Paved_Drive||	
||MS_SubClass|Pool_QC||
|||Fence||

---

### Brief Summary Analysis

The project is split into two main parts (1) data cleaning/feature engineering, and (2) modelling using sklearn's `LinearRegression`, `Ridge` and `Lasso` models. 

To fulfil the project requirements, I also applied the model on a test set to predict 'SalePrice' and this was uploaded to a Kaggle competition.

A few key results/observations below:
   - A few variables (e.g. 'Overall_Qual','Gr_Liv_Area') have a good positive correlation with 'SalePrice'
   - The model works the best with a subset of 49 highly correlated features using the Linear Regression model
   - However, the Lasso and Ridge models performed quite similarly to the Linear Regression model
   - For the Kaggle competition, I chose the Lasso model with the 49 highly correlated features and obtained a RMSE of 27,849 on the public score.
   - To answer the problem statement, basement features provide a good association with 'SalePrice'

---

