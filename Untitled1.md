# Capstone Final Project 

## 1) Topic Selection

## 2) Acquiring the Data

## 3) Exploratory Data Analysis 

## 4) Machine Learning 

## 5) Deep Learning Using Tensorflow

## 6) Implementing on Spark

## 7) Conclusion















### 1) Topic Selection

####     1.1)Significance of This Issue

    India is an agricultural country and one third population depends on the agricultural sector directly or indirectly. Agriculture remains as the main stray of almost all Indian states economy. The primary income for large sector of people in each state in India is agriculture and most of the state produces same set of different variety of crops. Indian agriculture mostly depends on rainfall and other climatic conditions. India is a peninsula as it is surrounded by 3 different water bodies on three sides each state will be experiencing different climatic conditions which in turn effects the crop production. I am choosing perishable crops (Mostly fruits and vegetables) because unlike cash crops perishable crops should be transported and use within 1-2 weeks of harvesting. As seasonal weather forecast for is more reliable, I want to build a model such that government can plan their perishable crop trade for a season efficiently . Using this recommendation system government can plan imports and exports across the country to increase farm profitability. Trade plays a crucial role in providing livelihoods for farmers and people employed along the food supply chain. A well-planned trade model in case of exports will bring good revenue for sate government and high profit margins to the farmers for their crop. The government can also estimate the set of states to import a perishable to minimize the import price as much as they can. 


####     1.2)Strategy to Solve this Issue:- 

    I will be designing a machine learning model to predict the farm price of partucular food crop. Therefore In case of exporting a particular food crop the states can select the states where the food crop price is more and in case of importing they can go with the states where food crop prices are less.

Additional Appications of this model can be:- 

1) Predicting most profitable crop for a pirticular season in a pirticular state

2) Helping traders to make high profit margins 

3) What is the best perishable food crops to plant in a particular season at a particular state?

4) For a particular vegetable or food crop in a particular season what can be the highest expected farm price?

5) For a particular crop at a particular season is it possible to make desirable profit?


### 2) Acquiring the Data:

When I asked myself what are the factors that results to different food crop prices in different states then I came up with two different factors. First one is because of different climatic conditions and the second factor is because of different soil types in different states across India.

2.1) 1)Monthly data of different perishable cops at different states across the country.
1.1) Note: - In my project I am taking top 10 most produced perishable crop datasets from January 2011 till December 2020.

2.1.2) Source: - National Horticulture Board of India

2.1.3) [Click Here to Redirect to NHBI](http://nhb.gov.in/OnlineClient/MonthlyPriceAndArrivalReport.aspx?enc=3ZOO8K5CzcdC/Yq6HcdIxJ4o5jmAcGG5QGUXX3BlAP4=)

2.1.4) [Link to Dataset in my Google Drive(Anyone from UMBC group can access it)](https://drive.google.com/drive/folders/1OxtPZU1gt_ehgOiGhl_hpdmPWlvjO2ZW?usp=sharing)

2.1.5) Attributes of the datasets: - Each individual dataset consists of 6 attributes, namely

Centre Name: - Name of the state

Year: - Year in which data is collected

Month: - Month in which data is collected

W.sale avg.price: - Sale Price in rupees per quintal(100kg)

Retail Avg.price: - Retail Price in rupees per quintal

Total Arrival: - Arrival in metric tons(1000)



2.2)Monthly historical weather and soil report of each sate in India from January 2010 till December 2020.

2.2.1) Source: - NASA’s Data Access Viewer: - Its Provides solar and meteorological data sets from NASA research for support of renewable energy, building energy efficiency and agricultural needs.

2.2.2) [Link Here to Redirect to NASA's Data Access Viewer](https://power.larc.nasa.gov/data-access-viewer/) 

2.2.3) [Link to Dataset in my Google Drive(Anyone from UMBC group can access it)](https://drive.google.com/drive/folders/15zXCuLByVlfpdg5eg_yfT2qBmqdDHeif?usp=sharing)

2.2.4) Attributes of the Datasets: -

All Sky Surface PAR Total:- The total Photosynthetically Active Radiation (PAR) incident on a horizontal plane at the surface of the earth under all sky conditions.

Dew/Frost Point at 2 Meters:- The dew/frost point temperature at 2 meters above the surface of the earth.

Temperature at 2 Meters Maximum:- The maximum hourly air (dry bulb) temperature at 2 meters above the surface of the earth in the period of interest.

Temperature at 2 Meters Minimum:- The minimum hourly air (dry bulb) temperature at 2 meters above the surface of the earth in the period of interest.

Specific Humidity at 2 Meters:- The ratio of the mass of water vapor to the total mass of air at 2 meters (kg water/kg total air).

Precipitable Water:- The total atmospheric water vapor contained in a vertical column of the atmosphere.

Wind Speed at 2 Meters Maximum: - The maximum hourly wind speed at 2 meters above the surface of the earth.

Wind Speed at 2 Meters Minimum: - The minimum hourly wind speed at 2 meters above the surface of the earth.

Surface Soil Wetness:- The percent of soil moisture a value of 0 indicates a completely water-free soil and a value of 1 indicates a completely saturated soil; where surface is the layer from the surface 0 cm to 5 cm below grade.

Root Zone Soil Wetness:- The percent of root zone soil wetness a value of 0 indicates a completely water-free soil and a value of 1 indicates a completely saturated soil; where root zone is the layer from the surface 0 cm to 100 cm below grade.

Profile Soil Moisture: - The percent of profile soil moisture a value of 0 indicates a completely water-free soil and a value of 1 indicates a completely saturated soil; where profile is the layer from the surface down to the bedrock.



### 3) Exploratory Data Analysis:

3.1) Combining Crops Datasets:

    I have downloaded the crops dataset from NHRB website. For each crop for each pirticular year ther is CSV file as I am doining analysis on 10 different perishable food crop from 2011 to 2020(10 Years), I have to download 100 different files. After downloading all the files I have to a lot of data transformation. The data consists of many unwanted column in uneven shapes. I deleted all the non_english charecters and unwanted names with the help of regular expression. There are signigicient amount of null value rows. I filled all the null value columns with their mean or mode based on the column type. I defined a function to read each and every csv file into a pandas dataframe and did all the above mentioned along with other necessary transformations and reshaped each and every dataframe in such a way that it is possible to merge all the dataframes and form a single unique crops dataframe.
    

3.2) Combining Weather Datasets:

    Coming to the weather datasets I have datasets related to 29 different states starting from the year 2011 to 2020(10 Years). So, I have to download 290 different csv files related to different states weather data. As I have done in case of crops dataset, I have done different data transformations for this weather dataset too. I removed unwanter rows and columns, replaced or removed null values beased on the statistics, replaces or renamed column header and reshaped the entire individual datasets using a function defined by me and joined all these transformed datasets into a single pandas dataframe.
    
3.3) Combined all dataframes and making it as a signle individual dataframe :

    After doing data cleaning and transformation on all the individual datasets, I modified both the final datasets of crops and weather datasets in such a way that they both can be joined properly into a final sigle large dataframe. After combing all the dataframes, my final dataframe consists of 17 columns(dtypes: int(1), float(13) and object(3)), 28,632 rows with no null values.
    
    
    
3.4) Looking into the data:

    Here are some of the visulizations to look into the data 
    
![save_as_a_png%20%281%29.png](attachment:save_as_a_png%20%281%29.png)


    Above is the bar plot of the count of no:of rows related to a pirticular food crop. If we look int the bar plot the is an uneven distribution. For example the count for ONION is more when compared to that of a CABBAGE. This is because different crops are grown in different seasons. Some crops such as Onion are grown through out the year while the crops such as cabbage are grown only in winter or rainy season. This is the reason for the imbalance in the data collect.
  

![plot2.png](attachment:plot2.png)


    The bar plot above shows the average price of 10 different crops in the entire dataset. 

![newplot.png](attachment:newplot.png)

    I checked for potential outliers in the dataset using box plot.From the above box plot we can see that there are some outliers in the dataset. I have deleted these outliers using the interquartile ranges. After deleting these outliers the final dataset consists of 22120 rows out of 28632 original dataset rows

![save_as_a_png5%20%281%29.jpeg](attachment:save_as_a_png5%20%281%29.jpeg)


     By ploting the above line plot, I checked how different crops behave under similar conditions. For example if we check the price of bitter gourd and Chilly form the year 2011 to 2012 under the similar climatic change the price of bitter gourd changes got decreased from 2011 to 2012 and the price of chilly got increased. From this we can come to a conclusion that different crops grow differently under similar climatic conditions.

![save_as_a_png.png](attachment:save_as_a_png.png)


    After taking a look at different visulizations and removing the outliers, I have checked for the corelation among the features with the help of heatmap. If we observe the heatmap only a very few features such as min temp and max temp are co-related. Based on the above heat map I thought of avoiding feature selection or going for any Priciple Component Analysis as this might result to the information loss since most of the data is not highly corelated

### 4)Machine Learning 

#### Classification and Regression Analysis.

    I intially performed regresion analysis on the dataset to predict the price of a pirticular crop but the resulting root mean square error is very high. So, I while training for a pirticular crop in order to remove the unwanted noise from the training model I thought an idea.
    
![Screen%20Shot%202022-05-20%20at%2011.08.58%20AM.png](attachment:Screen%20Shot%202022-05-20%20at%2011.08.58%20AM.png)

    I thought of classifing the data into different crops first and then for each crop I want to divide it into 4 different categories namely Huge Loss, Loss, Profit and Huge Profit based on the percentile values. If a crops price is under 25percentile of the crop I labeled it as HUge Loss, Loss if in between 25 and 50 percentile values, Profit if the crops price lies in betweeen 50 and 75 percetile value and huge profit if it is greataer than 75 percentile. For that I created a new column named P_L_Statement and the categorical value under which the row datafalls. 
    
    My main idea behind this classification is if I can predict under which category the given data falls then I can train the ML regression model by grouping the data by pirticular crops and P_L_Statement there by removing unwanted noise in the data.
    
    I have done on hot encoding to encode the categorical features into value arrays, split the data into train validation and test datasets in 80:16:4 proportion, standardized the features using StandardScalar Class and performed different classification algorithms such as Stocaastic Gradient Decent, Logistic Regression, Support Vector Machine, Decision Trees and Random Forest.I did hyperparameter tuning using learning cures and found the best parameters and trained the models.  All the models validation accuracy is less than 70%. As there is much bias varince tradeoff in the data I though what more can I do inorder to decrease this bias varience tradeoff then I though of doing two things.
    
    First I added an extra feature wind speed into my feature set. I came to know that wind speed is crutial in plants growth. In ideal wind speed conditions, the plants grows deep into soil to stabilise the plant which inturn results in obsorving more amounts of water and nutrients from the soil. The ssecond thing I tried to do is to normalise the price values from 2011 to 2020. In general the price value in 2010 is cannot be compare to that of the price value in 2020 so to normalized that I brought the rupee exchange rate into data. I divided the average exchange rate of rupee in that pirticlar month with the crop price at that month to get a standardised value. I included the above two features into my dataset.
    
    Again doin the classification on the new modified dataset this time my validation accuracy went upto 76% incase of Random Forest. So now I took the test data performed the classification first then based on the classification type I trained my ML Decission Tree regrission and calculated the average root mean square error value. But in contradiction to my assumption the average RMS value is still worse.

### 5) Deeplearning using Tensorflow:

    Unable to decrease the root mean square error through regression, I thought of doing deeplearning on my dataset using keras tensorflow deeplearning framework. By setting the the loss considerabely low at 18th epoch and with sigle batch. The overall RMS value after with the help of tensorflow framework is better than DTree regression analysis which is 8.75. I cannot say that my model is good but with the help of including more revelant features I think my model can perform well. 

### 6) Implementing using Spark
    
    Apart from the accuracy one more import isuue which I want to address is the over all run time. My data transformation phase alone is taking almost 20min to to run. So, in order to address this issue I bought spark into picture. I want to run my entire model on top of Spark StandAlone Cluster. As the pandas dataframes can't be parllelised running those even in spark environment will be useless. So, I thought of using pySpark SQl dataframe in place of pandas dataframes. I tried to do the entire data transformation in pySpark dataframes but because of the immutable nature and inability to maintain the row order of spark dataframes, I have to use pandas dataframes in between. To over come this I tried to implement KOALAS which is an lightweight API framework which can be run on top of pandas and Spark Dataframes. But even using KOALAS I have to use pandas sometimes as koalas dont inherit all the functionalities of pandas. But running my MLmodel on top of spark standalone mode cluster with the help of 4 core process decreased the overall runtime to 15min. 

### 7) Conclusion

    I cannot say that my model is accurate and predicts the crop price with higher accurary. As the analysis is done on the entire coutry by taking just 16 features my dataset is having high varience. But if more number of revelant features which can effect the farm price of apirticular crop are identified and collected, I think the model can be well train with higher accuracy. We can also improve the overall run time by running on top of YARN where effective resource allocation can be done. 


```python

```
