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






