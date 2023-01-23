# Image Classification with DeepLearning Project4

## Overview
***
- **Be Well Healthcare Center, Radiology Department is looking for an efficient way to screen chest x-ray images for pneumonia detection in pediatric patients.**

- They want to decrease the workload of its radiologists, minimize the diagnosis time, allow for faster treatment timelines, and lower the risk of human errors and improve patient safety.

- **GOAL**: is build a Neural Network that detects the presence of pneumonia in X-ray images. My main purpose was to  predict the status of the lungs (Normal vs pneumonia) as accurately as possible while maximizing recall: Identify majority of the True Positive cases correctly so that we catch as many kids with pneumonia as possible. 

## Data Understanding
***
* The data was obtained from [Kaggle](https://www.kaggle.com/datasets/paultimothymooney/chest-xray-pneumonia). 

* The data involved chest X-ray images from 5,863 pediatric patients separated by the image categories that they belong to (Pneumonia/Normal). 

## Data Preprocessing:
***
* Train (80%), test (10%), validation (10%) sets formed
* All images are downsized to a size of 128 x 128 pixels
* Pixels values (0-255) normalized to 0-1
* Converted to Grayscale

* Below graph shows a sample image data before and after pre-processing:





![DataMatrix_BeforeAfterCleaning](https://user-images.githubusercontent.com/61121277/199284666-c8f26292-406a-43c3-a6dd-36a780364683.png)

## Preprocessing
***
#### Binary (yes/no) Columns:
* Many of the variables in float type are actually binary (yes/no).
* Given that the proportion of null values are not too high for these variables, the null values will be replaced with the **most frequent**. 

    ##### `health_insurance`:
    * A **predictive model** will be used to impute the missing values and then these values will be merged into the dataset. 

#### Numerical Columns:
* Some of variables in float type are **ordinal** (some sense of ordering to its categories), so they will be treated as **numerical**. 
* The null values will be replaced with the **Median**. 
* Standard Scaling for the numerical variables only (since binary and categorical variables are already encoded as 0 and 1)

#### Categorical Columns:
* The variables in object type are **nominal** (no intrinsic ordering to its categories), so they will be treated as **categorical**. 
* The null values will be replaced with a **contant('missing')** creating its own level before one-hot encoding these variables. 

    ##### `income_poverty`:
    * A **predictive model** will be used to impute the missing values and then these values will be merged into the dataset. 

## Modeling
***
1. The data was split into training and test sets.
2. The data was pre-processed. 
3. Several types of classifiers were built, tuned (using GridSearchCV to test combinations of hyperparameters) and validated:

    - Logistic Regression
    - Decision Tree
    - Random Forest
    - XGradient Boosted
    - Stacking Classifier (using above models)

4. Scoring Metric: Roc_Auc was used afor tuning hyperparameters and evaluating model performance, because:
 
* We care equally about true positives and true negatives, and the roc curve gives a desirable balance between **sensitivity/recall (maximizing True positive Rate)** and and **1 - specificity  (minimizing False Positive Rate - Probability that a true negative will test positive)**

* We want to utilizes **"probabilities"** of class prediction. Based on this, we’re able to more precisely evaluate and compare the models. 

## Evaluation
***

![Compare_RocCurve_Models](https://user-images.githubusercontent.com/61121277/199509396-629dd8df-bbb7-4715-85b8-e7626bf4c289.png)

* **XGBoost** gives the best performance on both train (tells if model is confident in it’s learning) and test datasets (tells if the results are negeralizable to an unknown dataset). It gives Roc_Auc values of 88% (on Train) and 87% (on test), which is considered **GOOD**.

![XGB_Results1](https://user-images.githubusercontent.com/61121277/199540455-5f1c29eb-cead-421f-bae3-2dad7efe6304.png)
![XGB_Results2](https://user-images.githubusercontent.com/61121277/199540456-eebd5573-1875-47c2-8501-edcb9ef0633b.png)

* Results from the best fitting model on the test set are:
    - **accuracy score of 79%**, 
    - **sensitivity/recall score of 79%** 
    - **specificity score of 82%** 

![XGBoost_FeatureImportance](https://user-images.githubusercontent.com/61121277/199292805-566c278c-e1e8-4a4a-b643-044569ce0812.png)

* The most important 6 features in predicting whether a person would get the seasonal vacccine are:

- `doctor_recc_seasonal`
- `healht_insurance`
- `opinion_seas_vacc_effective`  
- `opinion_seas_risk`
- `age_group_65+ Years`
- `health_worker` 

## Conclusion
***

![MostImportantFeatures_Probability_BarPlot](https://user-images.githubusercontent.com/61121277/199609041-e03dd4f4-2340-4512-a684-608f90204cc6.png)

You are more likely to get the vaccine if you:

- have a doctor recommending the vaccine
- have health insurance
- think the vaccine is effective
- think you can get sick from flu
- are older, especially +65
- are a health worker
   
## Recommendations
***
* Educate the physicians on the importance of vaccination. Make sure they recommend it to their patients.
* Consider offering universal health coverage. Inform the public that flu vaccine is covered by insurance. 
* Inform people about the effectiveness and safety of the vaccine, and their risk of falling ill and developing complications if not vaccinated. 
* Keep focusing on older age groups, because they are at more risk of developing flu-related complications. Also target younger people since their vaccination rates are much lower.

## Next Steps
***
* Encrypted employment industry, employment occupation, and geographical region info, hard to make any specific suggestions based on these features. 
* Results on health insurance are not very reliable due to 40% of the data being null and being encoded using predictive modeling. More emphasis needs to be given to this variable next time the survey is conducted even it is a significant feature in predicting vaccine outcome. 
* More recent data needs to be collected after the Covid-19 pandemic since the pandemic might have altered people’s attitude towards flu vaccine as well. 

## Repository Structure
    .
    ├── images 
    ├── data 
    ├── Notebook.ipynb     
    ├── Notebook.pdf 
    ├── Presentation.pdf                                             
    └── README.md   

## Contact Info:
* Email: erdemiraysu@gmail.com
* GitHub: [@erdemiraysu](https://github.com/erdemiraysu/)
* [LinkedIn](https://www.linkedin.com/in/aysuerdemir)
