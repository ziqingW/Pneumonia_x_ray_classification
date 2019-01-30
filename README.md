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

**All the images are jpeg files. However, the formats of images are very varied. And some images in training set are in 'RGB' mode, while the others are in 'Greyscale' mode. Thus, all of these variations need to be consistent during the preprocessing step.  

## Methodology  
Basically, this project analyzes the data of venues located in the area with the queried zip code and compares the similarity of the template area with Houston's neighborhoods based on the venues' category. The more venues with the same category, the more similar the two areas. To do that, I use euclidean formula to calculate the distance of venues' categories between the template area with every neighborhood in Houston. The lower the distance, the higher the similarity. Eventually, three neighborhoods in Houston with the lowest distance will be the candidates for user to choose from.   

Steps of the procedure include:  
1.  Load data from resources(as discussed in the Data section).  
2.  Process data for the appropriate format.  
3.  API request for venues data through Foursquare.  
4.  Convert data of venues into a one-hot table representing the existence percentage of every different venue's category grouped in one same neighborhood.  
5.  Calculate the distance of venues' categories between the inputted area with every neighborhood in Houston to find out the most similar three.  
6.  Visualize the results on map.  
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
