### Credit Card Fraud Detection

### Abstract

The project aims to classify the fraudulent transactions of credit cards, with high accuracy. The Credit Card Fraud Detection problem includes modeling credit card transactions with the knowledge of the ones that turns out to be fraud. Such modeling will enable companies to efficiently flag a transaction which may be fraudulent. 

### The dataset 
The dataset consists of simulated credit card transactions containing both legitimate and fraudulent transactions. The dataset is in csv format and has been taken from the Kaggle public dataset. Data has been generated using Sparkov Data Generation tool created by Brandon Harris (Duration-Jan 1, 2019 to Dec 31, 2020). 
  - The data consists of around 1.3 million transactions having details of 1000 customers with a pool of 800 merchants. 
  - It consists of 21 features. Some of the important features are cc_num, merchant, category, amount, gender, city_population, job, date of birth, is_fraud, city, state,zip etc.

### Goal 
To predict the fraudulent transaction with 100% accuracy.

Steps followed in notebook :
### 1. Loading the data 

```ruby
df_train = pd.read_csv("fraudTrain.csv")
df_test = pd.read_csv("fraudTest.csv")
```
### 2. Data Exploration
#### 2.1 Data Information
```ruby
df.info()
```
#### 2.2 Shape of Data


```ruby
print(df_train.shape,df_test.shape)
df_train.isnull().sum()
df_train.corr()
```
#### 2.3 Taking a fraction to run the model faster
```ruby
# taking smaller sample to run the model faster
df_train= data_train.sample(frac = 0.1,random_state=1)
df_test= data_test.sample(frac = 0.05,random_state=1)
print(df_train.shape,df_test.shape)
```
#### 2.4 Checking the null values
```ruby
df_train.isnull().sum()
df_test.isnull().sum()
```
#### 2.5 Correlation Matrix
#get correlations of each features in dataset
corrmat = df_train.corr()
top_corr_features = corrmat.index
plt.figure(figsize=(15,15))

#plot heat map
g=sns.heatmap(df_train[top_corr_features].corr(),annot=True,cmap="RdYlGn")

#### 2.6 Histograms
```ruby
#visual representation of the data using histograms 
df_train.hist(figsize = (15, 15))
plt.show()
```
#### 2.7  Getting the Fraud and the Normal  transaction numbers for test and train datase
```ruby
fraud_train = df_train[df_train['is_fraud']==1]
normal_train = df_train[df_train['is_fraud']==0]
fraud_test = df_test[df_test['is_fraud']==1]
normal_test = df_test[df_test['is_fraud']==0]

print("Normal cases in train set :",len(df_train)-len(fraud_train),"\nFraud cases in train set :",len(fraud_train))
print("Normal cases in test set :",len(df_test)-len(fraud_test),"\nFraud cases in test set :",len(fraud_test))
```

### 3. Data transformation and feature engineering

From the exploratory data Analysis we make the following observations:   

1. The first column contains just the indices and is not useful so we will drop it.   
2. The third column with customer card number is also not useful , so we will drop it. 
3. "first name" and "last name" can also be dropped.  
4. Transaction number - is it really needed? can be dropped.
5. Date time column can be used to calculate the age of the customer

#### 3.1 Dropping the columns not needed
```ruby
# function to drop tbe columns
def dropCol(data):
    col_to_drop = ['trans_date_trans_time','Unnamed: 0','cc_num','first','last','trans_num']
    res = data.drop(col_to_drop,axis = 1)
    return res
```
```ruby
# dropping the columns
# dropping the columns ['trans_date_trans_time','Unnamed: 0','cc_num','first','last','trans_num']
# train data set
df_train = dropCol(df_train)

# test data set
df_test = dropCol(df_test)
print ( df_train.shape, df_test.shape)
```
#### 3.3 Creating Independent and Dependent Features
```ruby

# Create independent and Dependent Features
columns = train_sample.columns.tolist()

# removing the dependent feature is_fraud
columns = [c for c in columns if c not in ["is_fraud"]]
X_train = train_sample[columns]
Y_train = train_sample['is_fraud']
X_test = df_test[columns]
Y_test = df_test['is_fraud']
print ( X_train.shape, Y_train.shape,X_test.shape, Y_test.shape)
```

#### 3.4 Feature engineering
##### 3.4.1 Convering the date of birth to age

```ruby
import numpy as np
import datetime
from datetime import date
def age_years(born):
    return 2019 - int(born[0:4])

X_train['age'] = X_train['dob'].apply(lambda x: age_years(x))
X_train = X_train.drop(['dob'],axis =1)

X_test['age'] = X_test['dob'].apply(lambda x: age_years(x))
X_test = X_test.drop(['dob'],axis =1)
print(X_train.shape,X_test.shape)
```

```ruby

```
##### 3.4.2 One hot encoding
```ruby

```
```ruby

```

### 4. Handling the imbalance in dataset.
#### 4.1 Under Sampling
```ruby

```
```ruby

```
#### 4.2 Over Sampling
```ruby

```
```ruby

```
#### 4.3 SMOTE (Synthetic Minority Oversampling Technique)
```ruby

```
#### 4.4 Near Miss (NearMiss Algorithm – Undersampling)
```ruby

```

### 5. Model Implementation
```ruby

```
```ruby

```
```ruby

```
```ruby

```
```ruby

```
```ruby

```
```ruby

```
### 6. Predictions
### 7. Results


