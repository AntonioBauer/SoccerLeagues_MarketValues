# Top Soccer Leagues - Analysis 
![](https://images.vexels.com/media/users/3/132241/isolated/lists/0d413432a55194038d3266f8045868dd-soccer-player-silhouette-1.png)

## Table of Contents
1. [Installation](#Installation)
2. [Project Motivation](#Project)
3. [File Descriptions](#File)
4. [Results](#Results)
5. [Licensing, Authors, and Acknowledgements](#License)

## <a name="Installation"></a>Installation
There should be no necessary libraries to run the code here beyond the Anaconda distribution of Python. The code should run with no issues using Python versions 3.*.

## <a name="Project"></a>Project Motivation
For my Data Scientist Nanodegree Program by Udacity, I was interested in the 2019 Soccer Player information from the top 9 European Leagues to gain insights regarding the distribution of the market value. In order to do that I followed the  [CRIPSDM](http://www.datascience-pm.com/crisp-dm-2/ "CRISP-DM process").

![]( http://www.datascience-pm.com/wp-content/uploads/2018/09/crisp-dm-wikicommons.jpg)

### 1. Business Understanding
The European Football Market Values data set is available from [Kaggle](https://www.kaggle.com/aricht1995/european-football-market-values "Kaggle") and includes market values and other information like position and age on soccer players from the top 9 European leagues. For this analysis I would like to focus on these six business questions:

- How are the market values distributed?
- What's the average market value by position?
- Which league has the highest average market value per player?
- Which clubs has the highest average market value per player?
- Who are the most valuable soccer players?
- Can you predict the league of a player based on his specific position, nationality and market value by using the k-nearest-neighbor (KNN) classifier? 

### 2. Data Understanding
The data set has 4,308 rows and 35 columns. 26 out of 35 columns (74.39%) have NULL values. Also 8 out of these 26 columns having more than 75% NULL values. The distribution of the data types is as follows:
Object data type: 28, int64 data type: 4, float64 data type: 3

There were 6 columns (Birth Date, JoinedClub, LastExtension, ContractExpiration. Last Updated Date, Highest Market Value Date) defined as object type which were changed to datetime64[ns] type.

### 3. Data Preparation
#### 3.1. Columns Dropped
There were 18 columns dropped from the DataFrame that contained a high amount of NULL values and didn't add value to this analysis. For example Citizenship 1, Citizenship 2 and birthplace were dropped, as column Nationality, which doesn't contain any NULL values, is sufficient. Also column FullName was dropped and instead, column PlayerName was used. There is a lot of missing data for all Youth Club columns. Therefore, I decided to drop all of them since I'm not interested in a player history.

#### 3.2. Rows with NaN values
I dropped 20 rows with NULL values in columns Market Value (Euros) and Position. 
This approach was chosen since it's a good practice according to StatisticsSolutions [StatisticsSolutions](https://www.statisticssolutions.com/missing-values-in-data/ "StatisticsSolutions") to drop missing values if the number of cases of missing values is extremely small (less than 5%). In this case the percentage of missing values is 1.8%.
For the missing values in column Height (Meters) I decided to impute values by using the mean. I understand that using the best practice mentioned above, the missing values could've been dropped as well. However, this is part of a training program so my goal is to practice imputing quantitative and categorical variables. This is why I decided to impute the missing values in column Height (Meters) instead of dropping them. For the missing values in column Foot and Position 2 I decided to impute values by using the mode. Again, the best practice would've suggested to drop those missing values. I decided to impute the mode for training purposes and especially for column Position 2, the mode was used because it's more accurate as it's calculated based on column Position.
I replaced the missing values in columns Highest Market Value (Euros) and Highest Market Value Date, by the applicable values included in column Market Value (Euros) and Last Updated Date.

#### 3.3. Creating dummy variables
I created dummy variables for the categorical columns Nationality and Position 2 in order to use them as features in the ML model. I understand that creating dummy variables can create scaling issues by adding a great amount of columns. This is the reason I only encoded two categorical values. Given the size of the data set, the advantages (e.g. easy interpretation) outweigh the disadvantages of using dummy variables in this case.

### 4. Data Modeling
I used descriptive statistics to gain interesting insights regarding the market value and k-nearest-neighbor (KNN) classifier to predict the league of a player, based on his specific position, nationality and market value.

### 5. Evaluation
The variables used were sufficient to use descriptive statistics to gain interesting insights regarding the market value. For the k-nearest-neighbor (KNN) classifier, I used 3 features to predict the league of a player. The accuracy is around 40% which is not too high but acceptable for my first machine learning model.

### 6. Deployment
Results are summarized in my [medium](https://medium.com/@antonio.f.bauer/europes-2019-20-soccer-season-is-almost-over-don-t-be-too-sad-and-check-out-these-interesting-e81f489847a4?source=friends_link&sk=86d25c1fc79f3cc987f6b32338614d5b "medium") post.

## <a name="File"></a>File Descriptions
There is one Jupyter Notebook which includes the analysis to answer the questions above. Markdown cells were used to assist in walking through the process from gathering and assessing the data to cleaning, modeling and visualizing it.

## <a name="Results"></a>Results
The main findings of the code can be found at the post available  [here](https://medium.com/@antonio.f.bauer/europes-2019-20-soccer-season-is-almost-over-don-t-be-too-sad-and-check-out-these-interesting-e81f489847a4?source=friends_link&sk=86d25c1fc79f3cc987f6b32338614d5b "here").

## <a name="License"></a>Licensing, Authors, Acknowledgements
Must give credit to A Richt for the data. You can find the Licensing for the data and other descriptive information at the Kaggle link available [here](https://www.kaggle.com/aricht1995/european-football-market-values "here"). Otherwise, feel free to use the code here as you would like!