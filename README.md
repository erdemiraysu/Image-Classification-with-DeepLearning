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
- The data was split into train (80%), test (10%), validation (10%) sets.
- All images are downsized to a size of 128 x 128 pixels.
- Pixels values (0-255) normalized to 0-1.
- Converted to Grayscale.

* Below graph shows a sample image data before and after pre-processing:

**Raw Images:**
![RawImages](https://user-images.githubusercontent.com/61121277/214113785-859bb596-848a-4ec1-aa8d-f0c849146e1a.png)

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

![CompareModels_train_val_acc](https://user-images.githubusercontent.com/61121277/214378393-93dd8b02-2047-4cdb-981e-b8f51668751b.png)

All models reached overall accuracy levels of 94-95% and recall values of 97-98% for the pneumonia cases for the test set.

![CompareModels_ConfusionMatrices](https://user-images.githubusercontent.com/61121277/214377538-db24f824-5c7e-4e6c-a823-d6afe2f3010a.png)

**CNN with dropout regularization and a lower learning rate** was chosen as the final model since it gave the best performance on test dataset by missing only 10 pneumonia-positive cases out of 428, and 9 out of 159 normal cases. 

* Using tuned CNN results on the test set were:
    - overall accuracy score of 97%, 
    - recall score of 94% for class normal, and 98% for class pneumonia 
    - f1 score of 94% for class normal, and 98% for class pneumonia
   
## Visualize Features:
* Below is the visualization of the 25th channel for each of the activation layers of the CNN architecture. 
* As can be seen later layers are more abstract representations. This demonstrates how the representations learned by CNN architectures become increasingly abstract with the depth of the layers.
![ActivationChannels](https://user-images.githubusercontent.com/61121277/214377645-737d9135-0297-459f-807f-ec541cca8591.png)
    
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
    ├── data 
    ├── Notebook.ipynb     
    ├── Notebook.pdf 
    ├── Presentation.pdf                                             
    └── README.md   

## Contact Info:
* Email: erdemiraysu@gmail.com
* GitHub: [@erdemiraysu](https://github.com/erdemiraysu/)
* [LinkedIn](https://www.linkedin.com/in/aysuerdemir)
