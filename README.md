# Image Classification with DeepLearning Project4

## Overview
***
- **Be Well Healthcare Center, Radiology Department is looking for an efficient way to screen chest x-ray images for pneumonia detection in pediatric patients.**

- They want to decrease the workload of its radiologists, minimize the diagnosis time, allow for faster treatment timelines, and lower the risk of human errors and improve patient safety.

- **GOAL**: is build a Neural Network that detects the presence of pneumonia in X-ray images. My main purpose was to  predict the status of the lungs (Normal vs pneumonia) as accurately as possible while maximizing recall: Identify majority of the True Positive cases correctly so that we catch as many kids with pneumonia as possible. 

## Data Understanding
***
* The data was obtained from [Kaggle](https://www.kaggle.com/datasets/paultimothymooney/chest-xray-pneumonia/). 

* The data involved chest X-ray images from 5,863 pediatric patients separated by the image categories that they belong to (Pneumonia/Normal). 

## Preprocessing:
***
* The data was split into train (80%), test (10%), validation (10%) sets.
* All images are downsized to a size of 128 x 128 pixels.
* Pixels values (0-255) normalized to 0-1.
* Converted to Grayscale.

* Below graph shows a sample image data before and after pre-processing:

Raw Images:
![RawImages](https://user-images.githubusercontent.com/61121277/214109773-9f22bee7-e258-443e-968a-9258c30a9e3f.png)
Processed Images:
![ProcessedImages](https://user-images.githubusercontent.com/61121277/214109823-50860662-402e-41d2-a2c1-51c5223fcac1.png)


## Modeling
***

Several types of naural networks were built, tuned and validated:

    - Baseline Artificial Neural Network ANN - fully connected multilayer perceptron (MLP) 
    - Deeper Artificial Neural Network ANN 
    - Baseline Convolutional Neural Network - subtype of NN mainly used for applications in image/speech recognition.
    - Deeper Convolutional Neural Network
    - Tuned Convolutional Neural Network(s)
    - Transfer Learning with VGG16
    - Transfer Learning with ResNest50V2

## Evaluation
4. Scoring Metric: Accuracy was used to be evaluated by the model during training, and recall values especailly for the pneumonia class were taken into 
 consideration for model evaluation during testing. 


## Evaluation
***

![Compare_RocCurve_Models](https://user-images.githubusercontent.com/61121277/199509396-629dd8df-bbb7-4715-85b8-e7626bf4c289.png)

* **CNN with Dropout regularization** gives the best performance on both train (tells if model is confident in it’s learning) and test datasets (tells if the results are negeralizable to an unknown dataset). 
* 
* It gives Roc_Auc values of 88% (on Train) and 87% (on test), which is considered **GOOD**.


![XGB_Results1](https://user-images.githubusercontent.com/61121277/199540455-5f1c29eb-cead-421f-bae3-2dad7efe6304.png)
![XGB_Results2](https://user-images.githubusercontent.com/61121277/199540456-eebd5573-1875-47c2-8501-edcb9ef0633b.png)

* Results from the best fitting model on the test set are:
    - **accuracy score of 79%**, 
    - **sensitivity/recall score of 79%** 
    - **specificity score of 82%** 

![XGBoost_FeatureImportance](https://user-images.githubusercontent.com/61121277/199292805-566c278c-e1e8-4a4a-b643-044569ce0812.png)


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
   
## Recommendations for use of CNN to classify x-ray images:

***
* Stream-line the diagnosing process  quicker return time and greater patient satisfaction.
* Begin the treatment right away for patients classified as high-risk.
* Have doctors to allocate time to go over the images that fall into the grey zone more rigorously, and for more demanding and complex procedures in general.

## Limitations and Improvements
***
* We can use data augmentation methods to increase the size of the training set. 
* We can crop the images to exclude the electrodes and letter R from the display which might be negatively affecting the image processing algorithm.
* We could address the class imbalance issue using oversampling techniques.

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
