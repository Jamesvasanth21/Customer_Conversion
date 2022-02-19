# Customer Conversion - Audiobook App
 
## Problem Statement

We have data from an Audiobook app. Logically, it relates only to the audio versions of books. Each customer in the database has made a purchase at least once, that's why he/she is in the database. We want to create a machine learning algorithm based on our available data that can predict if a customer will buy again from the Audiobook company.

The main idea is that if a customer has a low probability of coming back, there is no reason to spend any money on advertizing to him/her. If we can focus our efforts ONLY on customers that are likely to convert again, we can make great savings. Moreover, this model can identify the most important metrics for a customer to come back again. Identifying new customers creates value and growth opportunities.


## Data Set

### How the data was gathered and designed?

The data was gathered from a Audiobook app, it represents two years worth of engagement. As we are doing **Supervised Learning**, we need targets. So targets was gathered, by taking extra six months after the two years period to check if the customer converted. So we took 2 years 6 months of data. The first two years are contained in the dataset are inputs, the next 6 months will show us if the person converted i.e bought another book. If yes, we count them as conversion and target will be '1', otherwise '0'.

We are taking a period of 2 years in our inputs, and the next 6 months as targets. So, in fact, we are predicting if: based on the last 2 years of activity and engagement, a customer will convert in the next 6 months. 6 months sounds like a reasonable time. 

If they don't convert after 6 months, chances are they've gone to a competitor or didn't like the Audiobook way of digesting information.

![Data_as_Image](https://github.com/Jamesvasanth21/Customer_Conversion/blob/main/images/Data_as_Image.JPG)

We have a **[Audiobooks_data - Before Processing.csv](https://github.com/Jamesvasanth21/Customer_Conversion/blob/main/Audiobooks_data%20-%20Before%20Processing.csv)** summarizing the data.

### Inputs

The below mentioned are the variables in the data:
- Customer ID,
- Book length (mins)_overall, 
- Book length (mins)_avg,
- Price_overall, 
- Price_avg,
- Review, 
- Review 10/10, 
- Minutes listened, 
- Completion, 
- Support Requests, 
- Last visited minus Purchase date .

**Note**:  Since we don't need the column names for model or prediction, we remove them from the csv and save the csv as **[Audiobooks_data.csv](https://github.com/Jamesvasanth21/Customer_Conversion/blob/main/Audiobooks_data.csv)**. And this csv will be used as input going further.

### Target

The targets are a Boolean variable (so 0, or 1), where 0 means the customer did not convert and 1 means the customer converted.

## Data Exploration

- **ID** - ID of the customers who have activity or engagement with the Audiobook App atleast once.
- **Book length (mins)_overall** - This column contains sum of the lengths of all purchases done by customer in Audiobook App.
- **Book length (mins)_avg** - This column contains average book length which is obtained by dividing the sum of the lengths of all purchases by total number of purchases. Number of purchases done by each Customer is not included as we can find it out using
Number of purchases = Book length (mins)_overall/Book length (mins)_avg
- **Price_overall** - This column contains price sum of all purchases done by customer in Audiobook App. The prices are in Dollars($), but they do not affect the prediction in anyway. Price is always a good predictor in such scenarios. 
- **Price_avg** This column contains average price of all purchases which is obtained by dividing the  sum(price) of all purchases by total number of purchases.,
- **Review** - Review is a Boolean variable. It shows if the customer left a review, where 1 is left a review and 0 is didn't. This show the enagagement of the user with the platform. Our assumption is that a customer who has left a review is most likely to convert
- **Reveiw 10/10** - Diffrent metric when compared with Review metric above. It measures the review of a Customer from 1 to 10.Logically we have only values for people who have left reviews, by examing the table we see that people leave no reviewas in most market places. this is bad for our dataset and bad in general. We perform **Data Imputing**  by leaaving the reviews posted on the platform and substitute all missing values with the average review which is **8.91**, which is obtained by Sum of all Reviews(1-10)/ Total Number of reviewsReview,. Hence for our ML mpdel **8.91** will be the **Status Quo**. Where a review > 8.91 indicates above average "feelings" and review < 8.91 indicates below average "feelings". Reveiw 10/10 is yet another variable that is an average i.e average reviews across purchases. This average review a person left indicates his/her feelings towards the content on the medium(or platform/content) or better, the medium as a whole.
A review of 2 indicates that person didnot have good experience with the audio book. Its likely for he/she to not buy again as the average review is 8.91.
- **Minutes listened** - Minutes listened indicates total minutes listened, and its a measure of engagement of user with the platform , - --- **Completion** - Completion is total minutes listened divided by the total length of the books a person has purchased. Assuming people don't listen to books twice. 
- **Support requests** - It is numerical and showa total number of support requests a person has opened. Where support requests is anything from forgotten password to assistance on using the platform. This is also a measure of engagement. It may turnout the more support a person needed, the more he or she got fed up with the platform and abandoned it or he or she likes it so much that by using it stumbles upon different issues, unlike someone who never opens the app
- **Last visited minus Purchase date** - This metric is measuring the difference between the last time a person interacted with the platform and their first purchase date(in days). Yet another measure of enagagement. The bigger the difference the better. If a person engages regularly with the platform this difference will be bigger. Thus the customer is likely to convert again. If the value of this variable is '0'. We are sure the customer has never accessed what he has bought,or perhaps he used it on the first day only, so its unlikely he/she will convert again.

So the above mentioned columns are the inputs (excluding ID, as it is completely arbitrary. It's more like a name, than a number).

- **Targets** - It is a categorical data with two categories '1' and '0', where if the customer converts in next 6 months we have 1 in Target for them and 0 if they do not convert.

## Task

Create a Machine Learning algorithm, that can predict if a customer will buy again.

This is a **classification problem** with two classes: won't buy and will buy, represented by 0s and 1s.

## Data Preprocessing

[Juypter Notebook](https://github.com/Jamesvasanth21/Customer_Conversion/blob/main/Customer_Conversion_Prediction_-_Preprocessing_-_Audiobook%20App.ipynb)

## Machine Learning Model

[Juypter Notebook](https://github.com/Jamesvasanth21/Customer_Conversion/blob/main/Customer_Conversion_Prediction_-_Machine%20Learning_-%20_Audiobook%20App.ipynb)