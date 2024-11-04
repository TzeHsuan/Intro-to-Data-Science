# Exploratory Data Analysis

The programmnig language I used was R and I used R Studio to conduct the analysis.

## Introduction

In order to conduct Exploratory Data Analysis (EDA), I choose to use the dataset about sleep efficiency, which has some missing data. I will be explaining why I choose to use certain EDA methods and what results I find. Moreover, I will detect whether there exists some outliers in the dataset. If there are some outliers, I will explain how I will deal with them. Last but not least, I will discuss some possible questions to be investigated for future studies.

## The Key Elements of EDA
1. Handling Missing Data
2. Outlier Detection
3. Data Summarization
4. Data Visualization
5. Correlation Analysis

## Process
### 1. Handling Missing Data
#### Finding unique characters
<img width="915" alt="Screenshot 2024-11-04 at 3 50 17 PM" src="https://github.com/user-attachments/assets/fb923e36-72bf-41f5-a3a2-e6b581108eb9">

#### Mean Imputation
<img width="918" alt="Screenshot 2024-11-04 at 3 52 12 PM" src="https://github.com/user-attachments/assets/463ff083-3066-4361-b9ed-0f4a9579c6d8">

Since there are a total number of 64 rows and 4 columns with missing values, I decide to use mean imputation to fill in those missing values. If I choose to delete those rows, I think there will be too many rows to be deleted, and this might affect the analysis’s accuracy. Moreover, due to the fact that the true values are unknown, we cannot conduct MAE or R-Squared tests to see the accuracy of mean imputation. However, the number of possible values of those columns are small, and the ranges are also small. Thus, I believe using mean would give highly accurate imputations.

### 2. Outlier Detection
#### Box plot
<img width="681" alt="Screenshot 2024-11-04 at 3 53 35 PM" src="https://github.com/user-attachments/assets/94f6a21a-0928-4392-90b5-65e05c050606">

The above box plots are the variables that have outliers. The reason I choose to use a box plot is because I wanted to find out if the dataset contains any outliers, and I think this is the most straight-forward method. Also, the box plot gives me information about the central tendency, interquartile range, and the shape and skewness of distribution. For sleep duration, the box plot illustrates that there are 2 outlier values, the variety of sleep duration hours is small, and the distribution is slightly skewed to the left. As for deep sleep percentage, it is demonstrated that there is 1 outlier values, the variety of percentages is slightly large, and the distribution is skewed to the left. Lastly, the box plot for caffeine consumption portrays that there is 1 outlier values, the variety of percentages is small, and the distribution is skewed to the right.

#### Z-Score
<img width="500" alt="Screenshot 2024-11-04 at 3 56 06 PM" src="https://github.com/user-attachments/assets/03c4801e-3ca9-4fe1-b620-68b2d09dfc1b">
<img width="500" alt="Screenshot 2024-11-04 at 3 56 21 PM" src="https://github.com/user-attachments/assets/f0df2c91-33f7-4cbb-869d-9c78751bdf0e">
<img width="500" alt="Screenshot 2024-11-04 at 3 56 32 PM" src="https://github.com/user-attachments/assets/e8102b46-166d-4ec4-8406-48296d1185ef">


Apart from box plot, I also conduct a z-test to reinforce the outliers illustrated in the box plots. We can see that the values for the outliers are same as that detected by box plots. Furthermore, we are able to see how the number of outliers from the z-test.

#### Delettion of Outlier
I decided to delete the outliers detected by box plot. The reason why I delete those outliers is because those values are true values, unlike the missing values, so I think it will somehow affect the accuracy of the dataset and the analysis, if I use other methods to change the values. After deleting the outliers, the number of rows dropped from 452 to 431.
<img width="918" alt="Screenshot 2024-11-04 at 3 58 28 PM" src="https://github.com/user-attachments/assets/115d0790-a428-498c-8ad1-80ffb50bebc0">


### 3. Data Summarization
#### Check data type & structure
<img width="918" alt="Screenshot 2024-11-04 at 4 00 22 PM" src="https://github.com/user-attachments/assets/3190bdaf-6d26-4bf7-924a-560475d5857e">

The above functions allow us to see that this dataset is a dataframe. After data cleaning, the number of rows decreased to 431, and the number of variables is 15. The structure function demonstrates each variable’s value format (whether it’s an integer, character, or number), and also the first few rows’ values.

#### Summary
<img width="918" alt="Screenshot 2024-11-04 at 4 01 19 PM" src="https://github.com/user-attachments/assets/1e33c3bd-73d3-404e-b527-0e2be128c867">

I decide to use the summary function is because it provides us with a quick overview of the variables, including the minimum and maximum values, the mean, the mode, and the quartiles. For variables in the type of characters, the function shows the number of rows (length), the class, and the mode.

<img width="916" alt="Screenshot 2024-11-04 at 4 02 25 PM" src="https://github.com/user-attachments/assets/a5888bd0-1f07-49bc-a87c-95ab47d57d04">

The describe function provides us with descriptive statistical information about the variables. The information include the mean, the standard deviation (sd), the median, the trimmed mean (trimmed), the mean absolute deviation (mad), the minimum and maximum values, the range, the skewness (skew), the kurtosis, and the standard error (se).

#### Summary of correlation
<img width="823" alt="Screenshot 2024-11-04 at 6 11 03 PM" src="https://github.com/user-attachments/assets/e49e001e-5906-4b4b-9dc3-e8d568497a5c">

Since the dataset is composed of both character and numerical variables, I pick out the numerical variables only, so that I am able to implement the correlation matrix. The correlation matrix allows us to see the correlation coefficient for each pair of variables. This is a simple and easy method to get an idea of the correlations.

<img width="827" alt="Screenshot 2024-11-04 at 6 11 55 PM" src="https://github.com/user-attachments/assets/1f37a5f0-13de-441b-b306-9c6812baa02e">

The corrplot function allows us to visualize the correlation coefficient in colors and they’re arranged in a more organized matrix. The lighter the colors are, the closer to 0 the correlation coefficients are. The darker the colors are, the more correlated the pair of variables are.

#### Correlation heatMap
<img width="828" alt="Screenshot 2024-11-04 at 6 16 17 PM" src="https://github.com/user-attachments/assets/36c6dfdd-2a3a-4784-9bae-8ab2b3a00d06">

The correlation heatmap is another visualization method of getting a quick idea of how each pair of variables are correlated. The difference between this and the above corrplot function is that the heatmap is a square matrix, which means that it will have the same squares opposite sides of the diagonal line. Also, the color range for heatmap is smaller, so it is not as clear and straigh-forward to spot the color differences.

#### Gini coefficient
<img width="826" alt="Screenshot 2024-11-04 at 6 17 02 PM" src="https://github.com/user-attachments/assets/e5115a4b-d27b-4b07-a506-73764a4b351d">

Using a for loop, I print out the Gini coefficients for all numeric variables. The Gini coefficient measures the inequality in a dataset. It tells us how unequal the distribution of values within a variable is. If the value is 0, that means all values are the name, there is an equal distribution. Yet, if the Gini coefficient is 1, this represents that there is a perfect inequality, meaning that there is one value dominating the others.

### 4. Data Visualization
#### Pie chart
<img width="827" alt="Screenshot 2024-11-04 at 6 18 15 PM" src="https://github.com/user-attachments/assets/8727b151-d75a-445a-9900-5dc48320ddb5">
<img width="596" alt="Screenshot 2024-11-04 at 6 18 27 PM" src="https://github.com/user-attachments/assets/27355f97-8e12-4e9d-9215-472b67284489">

I used a pie chart because the values of gender are either “Male”, or “Female” and the values of smoking status are either “Yes”, or “No. Plus, they’re all in the type of characters. Thus, it would be easier to know the gender and smoking status distribution by just looking at the pie chart at first glance. The results show that the gender distribution is almost evenly distributed, half male and half female. As for smoking status, there’re more than half of the people who are non-smokers.

#### Histogram & Density Plot
##### a. Age
<img width="597" alt="Screenshot 2024-11-04 at 6 31 06 PM" src="https://github.com/user-attachments/assets/767a0f1f-256f-46a5-8673-203a55d353d2">

I decided to use a histogram to illustrate the distribution of age in the dataset. The reason behind this is because the values of age are integers, and they range from 9 to 69. Hence, it would be a good idea to use histogram combined with density curve in order to observe the distribution of test subject’s age. It can be observed that most test subjects fall between the age of around 20 to 30, and 40 to 60. The density plot illustrates the same concept, but the curve is more smooth. Furthermore, the value of skewness is positive and close to 0, which means that the distribution is right skewed and it’s close to symmetrically distributed. In addition, the value of kutosis indicates a platykurtic distribution. The distribution has thinner tails and a flatter peak. It also suggests that the data has fewer outliers, and extreme values are less common.

##### b. Exercise frequency
<img width="614" alt="Screenshot 2024-11-04 at 6 32 26 PM" src="https://github.com/user-attachments/assets/282a3800-e6c5-4d81-9d45-1ea413925ee8">

From this histogram and density plot, we can see that most test subjects exercise around 0 to 3 days per week, with a highest density around 3 days. The value of skewness is around 0.163, indicating that the distribution is right skewed and it’s slightly close to symmetrically distributed. In addition, the negative value of kutosis tell us there is a platykurtic distribution.

##### c. Caffeine consumption
<img width="603" alt="Screenshot 2024-11-04 at 6 33 51 PM" src="https://github.com/user-attachments/assets/b3a713f4-b919-4fd5-acbf-68f740de3734">

It can be observed that most test subjects consume none caffeine. Though the number of test subjects consuming around 50 mg per day doesn’t follow the trend, we can see that the number of test subjects decreases as the consumption amount increases. The value of skewness is roughly 0.682, indicating that the distribution is more right skewed. Also, the negative value of kutosis tell us there is a platykurtic distribution.

##### d. Alcohol consumption
<img width="609" alt="Screenshot 2024-11-04 at 6 34 35 PM" src="https://github.com/user-attachments/assets/f4565d66-2b84-4b22-bf41-e473c814825c">

It can be observed from both the histogram and density polt that most test subjects consume none alcohol. In addition, there are still some test subjects who consume alcohol, but their density is about the same, while slightly decreasing as the consumption level increases. Both the value of skewness and kutosis reinforce the idea. The value of skewness is around 1.139, showing that the distribution is more right skewed. The positive value of kutosis tell us there is a leptokurtic distribution, meaning that the distribution has fatter tails and a sharper peak. It also suggests that the data has more outliers, and extreme values occur more frequently.

#### Bar Plot
<img width="599" alt="Screenshot 2024-11-04 at 6 36 23 PM" src="https://github.com/user-attachments/assets/eef9d9a7-3099-4ef7-92c6-3395b1950535">

This bar plot compares the percentage of the sleep stages (deep sleep, light sleep, and REM sleep) for the test subjects that have the highest and lowest value of sleep efficiency. It is suggested that the test subject with the highest value of sleep efficiency has a very high percentage of deep sleep, and the lowest percentage is light sleep. On the other hand, the test subject with the lowest value of sleep efficiency has a high percentage of light sleep, and a low percentage of deep sleep.

### 5. Correlation Analysis
#### Linear regression
##### a. Scatter Plot For Sleep Duration & Sleep Efficiency
<img width="605" alt="Screenshot 2024-11-04 at 6 37 59 PM" src="https://github.com/user-attachments/assets/54bbf01c-5ba5-48c4-b158-3ad6207dfd2a">
<img width="605" alt="Screenshot 2024-11-04 at 6 38 22 PM" src="https://github.com/user-attachments/assets/1ae253c3-a46c-48ed-bcae-04bcdbf552a6">

The scatter plot with regression line shows the correlation of 2 variables. By looking at the plot and the r-value, we can say that sleep duration and sleep efficiency does not have any correlation.

##### b. Scatter Plot For Sleep Efficiency & REM Sleep Percentage
<img width="619" alt="Screenshot 2024-11-04 at 6 39 07 PM" src="https://github.com/user-attachments/assets/02686162-05ce-4860-802f-a34194a83b9e">
<img width="619" alt="Screenshot 2024-11-04 at 6 39 22 PM" src="https://github.com/user-attachments/assets/902a3436-5795-4b5f-afae-8adaac8cc441">

The scatter plot for sleep efficiency and REM sleep percentage implies that they have a very weak positive correlation. Yet, the r-value tells us that they almost have no correlation at all (very close to 0).

##### c. Scatter Plot For Sleep Efficiency & Age
<img width="598" alt="Screenshot 2024-11-04 at 6 40 04 PM" src="https://github.com/user-attachments/assets/650197fe-4db0-4c57-9ad2-fd2363d240f8">
<img width="598" alt="Screenshot 2024-11-04 at 6 40 18 PM" src="https://github.com/user-attachments/assets/f1fb7168-a1bb-457e-a939-cf9ccc58dace">

By both the scatter plot and r-value, it can be inferred that the sleep efficiency and age has a weak positive correlation.

## Conclusion

By conducting EDA, I understand better about the structure of the dataset, as well as some patterns. For example, the 3D scatter plot suggests that sleep efficiency is negatively correlated with light sleep percentage, and it’s positively correlated with deep sleep percentage. From the bar plot, I find out that the test subject with the highest value of sleep efficiency has the highest percentage of deep sleep, and the lowest percentage of light sleep. Thus, both the 3D scatter plot and bar plot convey the same message, that is in order to have a good night sleep, one needs to have higher percentage of deep sleep, and a lower percentage of light sleep.

## Possible Problems To Investigate For Future Studies
1. Are deep sleep & light sleep the 2 most significant factors affecting the sleep efficiency or are there other factors ?
2. Does other variables such as amount of time using smart phone affect sleep efficiency ?
3. What is the best time of day to go to bed in order to achieve good quality of sleep ?
4. To predict whether one will have a good quality of sleep
5. Does sleep efficiency affect the smoking status ? (Perhaps low sleep efficiency could cause stress and thus become a smoker?)


