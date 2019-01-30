# Pneumonia_x_ray_classification
## Introduction  
This project's goal is to help doctor diagnose the pathological pneumonia from chest X ray pictures using a deep learning techniche.

So generally, a convolutional nerual network with 4 hidden layers to classify whether a x ray image is positive of pneumonia was trained by around 5 thousands of images mixed of both pneumonia negative and positive images. The model was created with Keras Framework.

## Data  
**Data Source:**  
https://www.kaggle.com/paultimothymooney/chest-xray-pneumonia

**Data List:**
1.  Training set: 5216 images  
2.  Dev set: 16 images  
3.  Testing set: 624 images  

**All the images are jpeg files. However, the formats of images are very varied. And some images in training set are in 'RGB' mode, while the others are in 'Greyscale' mode. Thus, all of these variations need to be consistent during the preprocessing step.**  

## Methodology  
**I.  Data preprocessing**  
1.  Load images with PIL in batch by glob.  
2.  Convert all the images to 'RGB' mode and resize them to 128 x 128 pixels (Using larger image would cause very complex computation, and the significance change is not worth of the computation cost).  
3.  Standardize the pixel value and convert the image data to numpy vectors, which are the X sets for the model inputs (including training, dev and testing). Create the related Y sets (vector of 0 for normal sets, 1 for pneumonia sets) based on the X set's shape.  
4.  Make the complete data sets by concatenating both normal and penumonia data sets for both X and Y.  
5.  Shuffle the data sets in random.  

**II. Building the model in Keras**  
The general idea is like model VGG-16 which keeps increasing filter units in the exponential of 2 and decreasing the image size by half with max pooling during every hidden layer. After 4 hidden layers of computation, the image data is converted from (128, 128, 3) to (5, 5, 256). The flatten vector is eventually computed by a sigmoid function to get the classification results (Fig.1).  




## Results  
*  For example, the user wants to search the most similar neighborhoods in Houston as where he lives in New York City with the zip code of **10030**. The results are:  
> The top three most similar neighborhoods as 10030 in Houston are:  
No.1 Greenway Plaza  
No.2 Rice/Museum District,West University/Southside Area  
No.3 Upper Kirby  

*  Also, if the user entered a zip code of Houston he/she would get the result that the most similar one was the area with the inputted zip code. This can be considered as a positive control of the project.

## Discussion  
*  The size of Houston's neighborhoods varies largely, which makes the data of venues from some areas less representing for the features of neighborhood.  
*  In this project, I combined the venues data from input and Houston together before performing the comparison. The reason of doing this was to ensure all the data sharing the same columns. Then the dataframe was split into two parts, one part for Houston's neighborhoods and the other one for the input area which was only one row.  

## Conclusion  
By analyzing the local venues information, this project can successfully find out the most similar neighborhoods in Houston as the queried one.  
