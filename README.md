# West Nile Virus Prediction
___
<p align = 'center'>
  <img src = 'https://raw.githubusercontent.com/86lekwenshiung/West-Nile-Virus-Prediction/main/image/rossmann-westnile.jpg' width = 75%>
<p/>
Source : https://www.purdue.edu/uns/html4ever/2006/060814.Rossmann.westnile.html


## Problem Statement

West Nile virus (WNV) is a single-stranded RNA virus that causes West Nile fever. It is a member of the family Flaviviridae, from the genus Flavivirus, which also contains the Zika virus, dengue virus, and yellow fever virus. The virus is primarily transmitted by mosquitoes, mostly species of Culex. It has been causing significant and sometimes severe human diseases. Although pesticides are known to be effective in dealing with the virus-carrying mosquitoes, it is expensive to deploy pesticides throughout the city. 

As data scientists, we want **to understand the factors driving the spread of WNV by leveraging on data collected by Chicago's surveillance system, weather stations, and pesticide spray deployment, in order to develop a classfication model that could predict the presence of WNV within the area of the city. Through these studies, we hope to suggest a cost-efficient and effective method of deploying pesticides within the area.**

## Summary

This project is the fourth project for General Assembly Singapore's Data Science Immersive Flex Batch 2 program (DSIF2) and was part of a Kaggle competition to predict the occurance of West Nile Virus in the city of Chicago.<br><br>
The project explores data collected from various sources, namely:<br>
&emsp;• Mosquito trap data collected by the city's surveillance and control system<br>
&emsp;• Location data of spraying efforts<br>
&emsp;• Weather data<br>

The data from these three sources were combined to form a dataset for analysis and modelling. Feature engineering exercise were perfomed to add information relevant to the classification models. **The two best models will be selected as final result for this project.**<br>

## Project Team Members

&emsp;• Julian **Chang**<br>
&emsp;• Ahmad **Khalil**<br>
&emsp;• Terence **Lek**<br>
&emsp;• Henri David **Oei**<br>
&emsp;• Elang **Setiawan**<br>

### Github repository

https://github.com/86lekwenshiung/West-Nile-Virus-Prediction

## Implementation

### Data
The following datasets were provided for this project:<br>
&emsp;• train.csv<br>
&emsp;• test.csv<br>
&emsp;• spray.csv<br> 
&emsp;• weather.csv<br>

### Data Dictionary

|Data                   |Source          |Description                              |  
|---                    |---             |---                                      |  
|Date                   |train.csv       |Date of sample collected (yyyy-mm-dd)    |  
|Address                |train.csv       |Street address of mosquito trap          |  
|Species                |train.csv       |Species of mosquite trapped              |  
|Block                  |train.csv       |Block number of mosquito trap            |  
|Street                 |train.csv       |Street name of mosquito trap             |  
|Trap                   |train.csv       |Mosquito Trap ID. Letter behind Trap ID indicate it is near a main Trap |    
|AddressNumberAndStreet |train.csv       |Full address of mosquito trap            |   
|Latitude               |train.csv       |Latitude coordinate of mosquito trap     |  
|Longitude              |train.csv       |Longitude coordinate of mosquito trap    |  
|AddressAccuracy        |train.csv       |Accuracy of the address                  |  
|NumMosquitos           |train.csv       |Number of mosquitos caught in trap       |  
|WnvPresent             |train.csv       |Presence of West Nile Virus (0=No, 1=Yes)|  
|Date                   |spray.csv       |The date of mosquito spray (yyyy-mm-dd)  |  
|Time                   |spray.csv       |The time of mosquito spray (H:mm:ss AM/PM)|  
|Latitude               |spray.csv       |Latitude coordinate of mosquito spray    |  
|Longitude              |spray.csv       |Longiture coordinate of mosquito spray   |  
|Station                |weather.csv     |Weather Station ID                       |
|Date                   |weather.csv     |Date of reading (yyyy-mm-dd)             | 
|Tmax                   |weather.csv     |Maximum Temperature                      |
|Tmin                   |weather.csv     |Minimum Temperature                      |
|Tavg                   |weather.csv     |Average Temperature                      |
|Depart                 |weather.csv     |                                         |
|DewPoint               |weather.csv     | |               
|WetBulb                |weather.csv     | |                   
|Heat                |weather.csv     | |
|Cool                |weather.csv     | |
|Sunrise                |weather.csv     | |
|Sunset                |weather.csv     | |
|CodeSum                |weather.csv     | |
|Depth                |weather.csv     | |
|Water1                |weather.csv     | |
|SnowFall                |weather.csv     | |
|PrecipTotal                |weather.csv     | |
|StnPressure                |weather.csv     | |
|SeaLevel                |weather.csv     | |
|ResultSpeed                |weather.csv     | |
|ResultDir                |weather.csv     | |
|AvgSpeed                |weather.csv     | |

## 3. EDA and Pre-processing 


**Workflow**


In this section, we undergo studying, understanding and feature engineering of the datasets. After that, datasets were combined. The following actions are taken:

Analyzing the train data and removing features that are not needed. Feature Engineering of species and distance of traps' locations and weather station.

Analyzing the spray and trap data. Feature Engineering of trap_sprayed feature.

Analyzing the weather data and removing features that are not need. Creating weekly average and time-lagged features for all remaning weather conditions. Feature Engineering of Codesum feature.

Combined all datasets together into one. Analyzing the combined dataset. Feature Engineering of traps feature. Drop features that will not be used and prepare for modeling.
We discovered that the time of the day where the sun is out was where the presence of Wnv was the strongest. Also, we observed that the more competent vectors for the spread of Wnv were the culex pipiens and culex restuans species. In order to deploy pesticides in a more cost-efficient way, we recommend spraying in areas where culex pipiens/restuans are most prominent and during the day as the Sun rises where the mosquitoes are most active.

1. EDA
2. Feature Engineering 
3. Data Preprocessing
4. Modelling to predict WNV probability (without pesticide)
5. Select best Model to study the effect of pesticide
  * 5.1 Hypothesis : Pesticide has no effect on Mosquito population


Contents:
1. Exploratory Data Analysis & Data Cleaning
2. Modeling & Evaluation
3. Additional Modeling
4. Cost Benefit Analysis
5. Conclusion and Recommendations
6. Python Library Used


 1. Exploratory Data Analysis & Data Cleaning


 2. Modelling & Evaluation


Several classifier models were developed, where the hyperparameters were tuned for each model to obtain the best cross-validated AUC scores. Because there were heavy imbalances in the data collected (about 95% of the data indicated no Wnv), an over-sampling method known as SMOTE (Synthetic Minority Over-sampling Technique) was adopted. It was also the reason for optimizing the models on AUC scores instead of accuracy. Comparing the AUC and recall scores, the production model selected was the AdaBoost model. Comparing the train and test accuracy scores of the selected model, there was evidence of slight overfitting of the data but the small difference was acceptable by our means


*Models used:*
- Logistic Regression
- Bernoulli Naive Bayes
- Random Forest Classifier
- ExtraTrees Classifier
- AdaBoost Classifier
- Gradient Boost Classifier
- Support Vector Classifier


*Evaluation Metrics used:*
- ROC-AUC score
- F1-Score
- Recall
- Precision
- Accuracy


 3. Additional Modelling
We also explored into deep learning and neural networks. However, our neural network did not outperform the selected model, likely due to the fact it had low complexity. We decided not to further develop the deep learning model since it is not easily interpretable and we had to keep within the limited timeframe of this project.


 4. Cost Benefit Analysis
For our project, we use trap-sprayed feature as a strong predictor of the presence of the Wnv in some of the models, suggesting that the spraying was effective in dealing with the Wnv to a large extent. Using our production model to predict where we should spray as a benchmark for future assessments, the benefits of $1,048,789.03 would out-weigh the cost, which is the amount that would be saved from excessively spraying the whole city. The cost of spraying the whole city is $$1,653,467.04, whereas the direct cost and indirect cost of targeted spraying are $145,060.68 and $459,617.30.


 5. Conclusion & Recommendation
In this project,we gained many useful insights about the mosquito population in Windy City and its relation to the epidemic of West Nile Virus(Wnv). Using our production model which is AdaBoost algorithm which gave us a high AUC and recall score. From our model, we can see the top features of importance contain result speed, wet & dry condition, sunlight, station pressure and some of the traps.


Moving forward, more geographic and demographics information could also be useful in studying the presence of Wnv. Since Wnv is spread through moquitoes, we could expect that proportion of open water sources, percentage of grass land, forests, and urban landscape are all factors of the livelihood of these mosquitoes. We can expand the studies to the rest of United States with more data on more mosquitoes species as other states have other species as the main vector species.


 6. Python Library Used
- Pandas
- Numpy
- Seaborn
- Matplotlib
- Pickle
- Sklearn
- Imblearn
- Tensorflow
- Folium
- Branca
- Datetime
- Suntime
- Pytz
- Geopy

## References
1. https://github.com/pushshift/api
2. https://pbpython.com/interactive-dashboards.html
3. https://machinelearningmastery.com/roc-curves-and-precision-recall-curves-for-classification-in-python/
4. https://towardsdatascience.com/text-analysis-basics-in-python-443282942ec5
**Model Explored**

**Key Insight**

We need to derive an effective plan to deploy pesticides throughout the city, and that is exactly where you come in!  

