## General Information
- Analyst Name : Prashant Lotlikar
- Date Started : 10 Sep 2023
- Completion Date : 13 Sep 2023
- Assignment type : Multiple Linear Regression

## Project Name - Bike Sharing Case Study
> You are required to model the demand for shared bikes with the available independent variables. It will be used by the management to understand how exactly the demands vary with different features. They can accordingly manipulate the business strategy to meet the demand levels and meet the customer's expectations. Further, the model will be a good way for management to understand the demand dynamics of a new market. 
> Which variables are significant in predicting the demand for shared bikes & How well those variables describe the bike demands

## Approach / Inferences 
- STEP 1 - Reading and Understanding the Data¶
* Inferences : There are 730 rows and 16 columns and no null values in any columns

- STEP 2 - Data Cleaning / Pre processing
* Inferences : no duplictes as size of both data frames after droppong dupicates is same

- STEP 3 - Visualising the Data / EDA 
- Visualising Numeric Variables : Using a pairplot
* Inferences : Linear model can be considered as atemp, temp show positive correlation with target variable

- Visualising Categorical Variables : Using a boxplot
*  	Inferences :
1. For the variable season, category 3 : Fall, has the highest median, which shows that the demand was high during this season. It is least for 1: spring.
2. The year 2019 had a higher count of users as compared to the year 2018.
3. There are no users when there is heavy rain/ snow indicating that this weather is quite adverse. 
4. Highest count is when the weather situation was Clear, Partly Cloudy.
5. The number of rentals peaked in September, whereas they peaked in December.
6. In December, rentals have declined.
7. The count is less during the holidays.
8. From the "Workingday" boxplot we can see those maximum bookings happening between 4000 and 6000, that is the median count of users is constant almost throughout the week. 
9. There is not much of difference in booking whether its working day or not.

- STEP 4 - Preparing data for the model
* Inferences : After adding dummies, There are 730 rows and 30 columns

- STEP 5 - Splitting the Data into Training and Testing Sets ((510, 30),(220, 30))
* Inferences : All units of the coefficients obtained are all on the same scale
* Inferences : atemp and temp seems to be poitively correlated to the target variable cnt.

- STEP 6 - Building a linear model Approach - Automated (RFE) + Manual (statsmodel )
* Inferences : p-value for all the variables is < 0.05 and VIF also is under 5. VIFs and p-values both are within an acceptable range. Hence, we finalise Model 4 (lm_4) as the final model for future prdeictions.

- STEP 7 - Residual Analysis of the train data
* Inferences : Error terms are centred around 0 and follows a normal distribution

- STEP 8 - Making Predictions Using the Final Model
* Inferences : r2_score of train dataset 0.7804505628068954 / r2_score of test dataset 0.7400661330012526

- STEP 9 - Model Evaluation
* Inferences : Model 4 is fitting on the test data set in a linear manner


## Conclusions
* Equation for best fitted line is : cnt = 0.540639 + 0.24782 x yr + 0.07369 x mnth_Sep + 0.056388 x weekday_Saturday + 0.048053 x workingday + -0.039325 x season_Summer-0.056258 x holiday-0.072982 x season_Winter-0.087864 x weathersit_Mist & Cloudy-0.102669 x mnth_Jan-0.187707 x windspeed-0.256802 x season_Spring-0.303522 x weathersit_Light Snow & Rain
* All the positive coefficients like yr, mnth_Sep indicate that an increase in these values will lead to an increase in the value of cnt.
* All the negative coefficients indicate that an increase in these values will lead to a decrease in the value of cnt
* From R-Sqaured and adj R-Sqaured value of both train and test dataset we could conclude that the above variables can well explain more than 74 % of bike demand.
* Top three features contributing significantly towards explaining the demand are:
	1. yr (0.247820),
	2. weathersit_Light Snow & Rain (-0.256802)
	3. season_Spring (-0.303522)
* Hence, it can be concluded that the variables yr, weathersit_Light Snow & Rain and season_Spring are significant in predicting the demand for shared bikes .
