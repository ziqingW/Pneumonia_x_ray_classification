# FindYourNeighborhood
## Introduction  
This project is designed to help people find the similar neighborhood in Houston as the one they are fond of. It can be useful for business expansion like choosing a new branch’s location, or for the new comer to choose the comfortable place to settle down with the similar environment as the one they’ve enjoyed before. 

So basically, this project would ask user to input a zip code(US only) as template. Then the project would analyze the data of the surrounding venues for the template zip code by Foursquare, and compare the similarity with the neighborhoods from the data of Houston. The result would show the top three neighborhoods with the highest similarities for user to choose. And these neighborhoods will be displayed on the map of Houston.  
## Data  
**The data required to accomplish this project will include:**  
1.  List of postal codes with their corresponding coordinates in the US. https://gist.github.com/erichurst/7882666  
    A pandas dataframe displaying postal code, latitude, longitude can be generated from the .csv file by these data.

2.	List of postal codes with their corresponding neighborhoods in Houston.  https://www.houstoniamag.com/articles/2017/3/24/neighborhoods-by-the-numbers-real-estate-data-2017  
    The data need to be scraped from web page by BeautifulSoup first for use. Then combine it with the dataframe from data 1 to make a new dataframe showing the postal code, neighborhoods and coordinates in Houston.

3.	Data of venues in the surrounding area of the particular coordinates from Foursquare.  
    Make the API request to Foursquare for the data of the venues at the queried coordinates which come from the dataframe made by data 1 and data 2. Segment the neighborhoods by their venues categories to find out the top three neighborhoods with the highest similarity to the template.  
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
