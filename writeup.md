# German Traffic Sign Classifier Project

## Purpose:
The purpose of this project is to build a neural network to classify images of German traffic signs.

## Data Description:
The training dataset consists of 34,799 total images with 43 different classes.  All of the images have been scaled to [32, 32, 3].  The data is highly imbalanced across the 43 classes.


## Data Pre-processing:
The following steps were taken to pre-process the data:

 1) Took a stratified sample of 1,000 images from each class (Training Dataset Only)
 2) The sampling procedure results in duplicate images within each class. To add variance across images, a gaussian blur with standard deviation in the range of [0,2] is applied (Training Dataset Only)
 3) Finally the pixels are normalized to a value between 0 and 1 (All Datasets)
 
 ## Model Architecture:
 The classification model was trained using a LeNet architecture, with dropout layers added to prevent overfitting.  The model layers are described below:
 
 1) Convolutional [5, 5, 3, 16]
 2) Activation (ReLU)
 3) Max Pooling [2,2]
 4) Convolutional [5, 5, 16, 32]
 5) Activation (ReLU)
 6) Max Pooling [2,2]
 7) Fully Connected [800, 400]
 8) Dropout w/ keep_prob = 0.5 (Training)
 9) Fully Connected [400, 200]
 10) Dropout w/ keep_prob = 0.5 (Training)
 11) Fully Connected [200, 43]
 
 ## Model Training:
 The model was trained using SGD (Batch size = 128, Epochs = 10) with the Adam optimizer.
 
 ## Model Validation:
 The model correctly classified 95.9% of images in the validation dataset and 93% in the test dataset.
 
 ## Applying Model to New Images
 The model was used to classify 5 images of German traffic signs that I found on the web.  These images had to be resized to [32, 32, 3] and normalized as we did in the pre-processing of the other datasets.  In addition, the images were manually labeled based on similarity to images in the training dataset.
 
 The model performs much worse on this dataset.  It correctly classifies only 40% (2/5) of the images.  However, the correct classification is amongst the top 5 predicted logits for 80% (4/5) of the images.
 
 
 


