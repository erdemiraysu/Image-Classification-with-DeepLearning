# Image Classification with DeepLearning

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
- The data was split into train (80%), test (10%), validation (10%) sets.
- All images are downsized to a size of 128 x 128 pixels.
- Pixels values (0-255) normalized to 0-1.

* Below graph shows a sample image data before and after pre-processing:

**Raw Images:**
![RawImages](https://user-images.githubusercontent.com/61121277/214430135-ec55af63-9ae7-47b0-b4bb-90feefec8e56.png)

**Processed Images:**
![ProcessedImages](https://user-images.githubusercontent.com/61121277/214377441-b4529e73-7e39-453f-b3cd-0cfbb4120e46.png)

## Modeling
***
Several types of naural networks were built, tuned and validated:

    - Artificial Neural Network ANN 
    - Convolutional Neural Network 
    - Transfer Learning with VGG16
    - Transfer Learning with ResNest50V2

## Evaluation
**Scoring Metrics**: **Accuracy** was used by the model during training, and **recall** values especially for the pneumonia class were taken into consideration for model evaluation on the test set. 

All models performed similarly well with no apparent signs of overfitting as seen by the loss and accuracy trends for the training and validation sets:
![CompareModels_train_val_acc](https://user-images.githubusercontent.com/61121277/215303767-e5d89de7-0ad2-4db6-acf7-3c55b44241bb.png)

All models reached overall accuracy levels of 94-95% and recall values of 97-98% for the pneumonia cases for the test set.
![CompareModels_ConfusionMatrices](https://user-images.githubusercontent.com/61121277/215303772-c702e469-89d5-49cb-a0b1-b506b7be6123.png)

**ResNet50** was chosen as the final model since it gave the best performance on test dataset by missing only 9 pneumonia-positive cases out of 428, and 12 out of 159 normal cases. 

* Using ResNet50 performance on the test set was:
    - overall accuracy score of 96%, 
    - recall score of 92% for class normal, and 98% for class pneumonia 
    - f1 score of 93% for class normal, and 98% for class pneumonia
<img width="596" alt="Screen Shot 2023-01-28 at 9 49 48 PM" src="https://user-images.githubusercontent.com/61121277/215303833-62f4a8da-9ac0-4e3c-9c63-4d34c60a9b54.png">

## Visualize Features:
* Below is the visualization of a sample channel for each of the activation layers of teh dropout CNN architecture. 
* As can be seen as the layers get deeper the representations learned by CNN become increasingly more abstract. 
![ActivationChannels](https://user-images.githubusercontent.com/61121277/215303865-1430d6c7-720d-4a60-9f36-695ff866ea98.png)

## Recommendations for use of CNN to classify x-ray images:
***
* Stream-line the diagnosing process which leads to quicker return time and greater patient satisfaction.
* Begin the treatment right away for patients classified as high-risk.
* Doctors/radiologists can allocate more time to go over the images that fall into the grey zone more rigorously, and for more demanding and complex procedures in general.

## Limitations and Improvements
***
* We can use data augmentation methods to increase the size of the training set. 
* We can crop the images to exclude the electrodes and letter R from the display which might be negatively affecting the image processing algorithm.
* We could address the class imbalance issue using oversampling techniques.

## Repository Structure
    .
    ├── images 
    ├── Notebook.ipynb     
    ├── Notebook.pdf 
    ├── Presentation.pdf                                             
    └── README.md   

## Contact Info:
* Email: erdemiraysu@gmail.com
* GitHub: [@erdemiraysu](https://github.com/erdemiraysu/)
* [LinkedIn](https://www.linkedin.com/in/aysuerdemir)
