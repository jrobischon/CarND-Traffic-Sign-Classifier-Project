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
The classification model is a convolutional neural network (CNN).  CNNs have proven to be useful in image classification, as they translation-invariant (i.e. can identify features at any location in an image) and require much fewer parameters than a fully-connected feed-forward network

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
 
The LeNet architecture was chosen, as it has been show to perform well on image classification tasks (MNIST in particular).  The number of output parameters in each layer were chosen mainly through trial and error.  The dropout layers were added, as the default LeNet architecture was prone to overfitting.
 
## Model Training:
The model was trained using SGD with the Adam optimizer.  A batch size of 128 was used with 10 epochs.  These values were chosen as they provided a good balance between model performance and model training time.  Increasing either of these values should lead to improved model performance.
 
## Model Validation:
The model correctly classified 95.9% of images in the validation dataset and 93% in the test dataset.
 
## Applying Model to New Images
The model was used to classify 5 images of German traffic signs that I found on the web.  These images had to be resized to [32, 32, 3] and normalized as we did in the pre-processing of the other datasets.  In addition, the images were manually labeled based on similarity to images in the training dataset.
 
The model performs much worse on this dataset.  It correctly classifies only 40% (2/5) of the images. Looking at the softmax probabilities across the different classes, we can see that the model is assigning classifications with a high degree of certainty (even when incorrect):

 ![Img0](https://github.com/jrobischon/CarND-Traffic-Sign-Classifier-Project/blob/master/softmax0.jpg)
 ![Img1](https://github.com/jrobischon/CarND-Traffic-Sign-Classifier-Project/blob/master/softmax1.jpg)
 ![Img2](https://github.com/jrobischon/CarND-Traffic-Sign-Classifier-Project/blob/master/softmax2.jpg)
 ![Img3](https://github.com/jrobischon/CarND-Traffic-Sign-Classifier-Project/blob/master/softmax3.jpg)
 ![Img4](https://github.com/jrobischon/CarND-Traffic-Sign-Classifier-Project/blob/master/softmax4.jpg)
 
 
Despite the high degree of certainty amongst incorrect predictions, the correct classification is amongst the top 5 predicted classes for 80% (4/5) of the images.
 

 


