About The Project:
Customer segmentation has a lot of potential benefits. It helps a company to develop an effective strategy for targeting its customers. This has a direct impact on the entire product development cycle, the budget management practices, and the plan for delivering targeted promotional content to customers. Customer segmentation can also help a company to understand how its customers are alike, what is important to them, and what is not. Often such information can be used to develop personalized relevant content for different customer bases.

As per the Pareto Principle, 80% of outcomes result from 20% of all the causes of any given event.

In business terms, we can say that 20% of customers contribute 80% share of the total revenue of a company. That’s why finding this set of people is important. I will explain the importance of customer segmentation in a detailed manner later in this article itself.

Problem Statement
The overall aim of this process is to identify high-value customer base i.e. customers that have the highest growth potential or are the most profitable.

Insights from customer segmentation are used to develop tailor-made marketing campaigns and for designing overall marketing strategy and planning.

Understanding Customer Segmentation
Customer segmentation is the process of separating customers into groups on the basis of their shared behavior or other attributes.

The type of segmentation criterion followed would create a big difference in the way the business operates and formulates its strategy. This is elucidated below.

1. Zero segments: This means that the company is treating all of its customers in a similar manner. In other words, there is no differentiated strategy and all of the customer base is being reached out by a single mass marketing campaign.

2. One segment: This means that the company is targeting a particular group or niche of customers in a tightly defined target market.

3. Two or more segments: This means that the company is targeting 2 or more groups within its customer base and is making specific marketing strategies for each segment.

4. Thousands of segments: This means that the company is treating each customer as unique and is making a customized offer for each one of them.
Factors for segmentation for a business to consumer marketing company:

Demographic: Age, Gender, Education, Ethnicity, Income, Employment, hobbies, etc.
Recency, Frequency, and Monetary: Time period of the last transaction, the frequency with which the customer transacts, and the total monetary value of trade.
Behavioral: Previous purchasing behavior, brand preferences, life events, etc.
Psychographic: Beliefs, personality, lifestyle, personal interest, motivation, priorities, etc.
Geographical: Country, zip code, climatic conditions, urban/rural areal differentiation, accessibility to markets, etc.
Ways to Segment your Customers?
To start with customer segmentation, a company needs to have a clear vision and a goal in mind.

The following steps can be undertaken to find segments in the customer base:

Analyze the existing customer pool
Develop an understanding of each customer
Define segment opportunities
Research the segment
Experiment with new strategies
Data Overview
Source: The UCI Machine Learning Repository

Data: This is a transnational data set which contains all the transactions occurring between 01/12/2010 and 09/12/2011 for a UK-based and registered non-store online retail. The company mainly sells unique all-occasion gifts. Many customers of the company are wholesalers.

Downloaded the xlxs file from Kaggle.

Data Attributes
1. InvoiceNo: Invoice number. Nominal, a 6-digit integral number uniquely assigned to each transaction. If this code starts with letter ‘c’, it indicates a cancellation.

2. StockCode: Product (item) code. Nominal, a 5-digit integral number uniquely assigned to each distinct product.

3. Description: Product (item) name. Nominal.

4. Quantity: The quantities of each product (item) per transaction. Numeric.

5. InvoiceDate: Invoice Date and time. Numeric, the day and time when each transaction was generated.

6. UnitPrice: Unit price. Numeric, Product price per unit in sterling.

7. CustomerID: Customer number. Nominal, a 5-digit integral number uniquely assigned to each customer.

8. Country: Country name. Nominal, the name of the country where each customer resides.

Data Snapshot
image
<img width="1053" height="432" alt="image" src="https://github.com/user-attachments/assets/077cfad9-3f5e-4a27-99d3-eb567cbf6306" />


Implementaion
Real-world/Business objectives and constraints

Interpretability is important.
Errors can be costly.
Segmantation should suit the retail business
Exploring the Data
Data was processed and cleaned. Here the duplicates were removed and the missing values were handled.

Country

Since the data, taken from the UCI Machine Learning repository describes the data to based on transactions for a UK-based and registered non-store online retail, let us check the percentage of orders from each country in the data.

<img width="1078" height="550" alt="image" src="https://github.com/user-attachments/assets/fe3432d9-64d1-4b15-ae75-57c559642556" />


The above graph shows the percentage of orders from the top 10 countries, sorted by the number of orders. This shows that more than 90% of orders are coming from United Kingdom and no other country even makes up 3% of the orders in the data.

Customers and Products

The total number of products, transactions, and customers in the data, which correspond to the total unique stock codes was found out

<img width="294" height="56" alt="image" src="https://github.com/user-attachments/assets/e7026867-3b01-4866-84a7-6716715a08b1" />


It can be seen that the data concern 4372 users and that they bought 3958 different products. The total number of transactions carried out is of the order of ∼ 24000.

Many Order were cancelled and across the countries. As per the data, if the invoice number code starts with the letter ‘c’, it indicates a canceled order.
<img width="402" height="262" alt="image" src="https://github.com/user-attachments/assets/d310228f-719b-454b-b772-3dacf36e0065" />


We note that the number of cancellations is quite large ( ∼ 16% of the total number of transactions). As we can see from the above figure, these cases are the ones where CustomerID values are NaNs and the decription mentioned check, lost, missing, smashed got these itmems. These cases were also removed from the data.

Stock Code

several types of peculiar transactions, connected i.e., port charges, bank fee, discount, free gifts, Carry bags, Samples, Amazon Fee,transaction fees which needed to be analysed.

<img width="619" height="368" alt="image" src="https://github.com/user-attachments/assets/cba60e9b-f469-41c2-9915-0713401c4fee" />


Net Amount/Invoice
<img width="433" height="394" alt="image" src="https://github.com/user-attachments/assets/4e7a91a1-a09b-46eb-9b4e-070a9d5e984c" />


*Amount shown are in UK Dollars

It can be seen that the vast majority of orders concern purcheses of low value ∼ 78% of purchases give prices in excess of £200.
<img width="1088" height="408" alt="image" src="https://github.com/user-attachments/assets/892c17de-020c-42d5-bb4a-db7f224fc0b1" />


*UK not included. UK as expected topped the list int this category.

Cohort Analysis
What is Cohort Analysis

A cohort is a set of users who share similar characteristics over time. Cohort analysis groups the users into mutually exclusive groups and their behaviour is measured over time.

There are three types of cohort analysis:

Time cohorts: It groups customers by their purchase behaviour over time.
Behaviour cohorts: It groups customers by the product or service they signed up for.
Size cohorts: Refers to various sizes of customers who purchase company's products or services. This categorization can be based on the amount of spending in some period of time.
In the following analysis, I created 'Time Cohorts'

Checking the date range of our data, we find that it ranges from the start date: 2010–12–01 to the end date: 2011–12–09.

Next, a column called 'CohortMonth' was created to indicate the month of the transaction by taking the first date of the month of InvoiceDate for each transaction. Then, information about the first month of the transaction was extracted, grouped by the CustomerID.
<img width="979" height="174" alt="image" src="https://github.com/user-attachments/assets/21f51b2d-2b68-4ac9-a7c5-92830c5b5612" />


Then I found the difference between the InvoiceMonth and the CohortMonth column in terms of the number of months to get the CohartIndex. Choartindex will tell us about the month of repurchase after their initial purchase.

<img width="986" height="114" alt="image" src="https://github.com/user-attachments/assets/4e98a681-5e89-4556-9070-6a6a73a57fd1" />

After obtaining the above information, I obtained the cohort analysis matrix by grouping the data by CohortMonth and CohortIndex and aggregating on the CustomerID column.

<img width="639" height="408" alt="image" src="https://github.com/user-attachments/assets/0b6bbd8d-4157-44dd-9344-f1d53482c8be" />


What does the above table tell us?

Consider CohortMonth 2010–12–01: For CohortIndex 0, this tells us that 948 unique customers made transactions during CohortMonth 2010–12–01. For CohortIndex 1, this tells that there are 341 customers out of 948 who made their first transaction during CohortMonth 2010–12–01 and they also made transactions during the next month. That is, they remained active.

Now I calculated the Retention Rate. It is defined as the percentage of active customers out of total customers.

<img width="723" height="473" alt="image" src="https://github.com/user-attachments/assets/341cba6a-f10d-4d69-936a-7d7718f49654" />


From the above retention rate heatmap, we can see that there is an average retention of ~35% for the CohortMonth 2010–12–01, with the highest retention rate occurring after 11 months (49.3%). For all the other CohortMonths, the average retention rates are around 18–25%

RFM Segmentation
RFM stands for Recency, Frequency, and Monetary.

RFM analysis is a commonly used technique to generate and assign a score to each customer based on how recent their last transaction was (Recency), how many transactions they have made in the last year (Frequency), and what the monetary value of their transaction was (Monetary).

RFM analysis helps to answer the following questions: Who was our most recent customer? How many times has he purchased items from our shop? And what is the total value of his trade? All this information can be critical to understanding how good or bad a customer is to the company.

After getting the RFM values, a common practice is to create ‘quartiles’ on each of the metrics and assigning the required order.

I used the net Amount to get the monetary value of each transaction i.e., per CustomerID For RFM analysis, we need to define a ‘snapshot date’, which is the day on which we are conducting this analysis. Here, I have taken the snapshot date as the highest date in the (last date on data + 1). This is equal to the date 2011–12–10.(YYYY-MM-DD)

<img width="1008" height="160" alt="image" src="https://github.com/user-attachments/assets/f29d06a0-6227-44c6-8c5c-eeb3e4a1db52" />


<img width="339" height="170" alt="image" src="https://github.com/user-attachments/assets/c1cd45e2-7968-49d4-8a58-4fe2e18517c2" />


Then, I created 4 quartiles segment on this data with split at [25%ile,50%ile,75%ile] and collate these scores into an RFM_Segment column by assigning a score(1,2,3,4) value [R,F,M] respectively to the attributes.

For the recency metric, the highest value, 4, will be assigned to the customers with the least recency value (since they are the most recent customers).
For the frequency and monetary metric, the highest value, 4, will be assigned to the customers with the Top 25% frequency and monetary values, respectively.
After dividing the metrics into quartiles, The RFM_Score is calculated by summing up the RFM quartile metrics and RFM_Segment is calulated by collating them as a string of characters.

<img width="576" height="164" alt="image" src="https://github.com/user-attachments/assets/2825089e-4456-4794-aaa3-c5bf8327accc" />


Now the data can be grouped on the basis of RFM Score and mean attributes value can be compared for varoius RFM scores.

<img width="318" height="355" alt="image" src="https://github.com/user-attachments/assets/c99020b8-0d85-4b68-8cfd-df8166b1f6f6" />


MY ANALYSIS FROM RFM SEGMENTATION

As expected, customers with the lowest RFM scores have the highest recency value and the lowest frequency and monetary value, and the vice-versa is true as well.

This data was clustred in three groups on the basis of RFM Score(3-12):

'Low': RFM Score < 5
'Middle': 5 <= RFM Score < 9
'Top': RFM Score >= 9
<img width="359" height="166" alt="image" src="https://github.com/user-attachments/assets/1a61353b-4483-4344-a9a4-9a957b39c1e2" />


In many scenarios, this would have been okay. But, if we want to properly find out segments on our RFM values, we can use a clustering algorithm like K-means.

Clustering
I chose K-Means clustering because the attribute were explicitly labelled.

Preprocessing data for Clustering

Firstly, I prepared the data for Kmeans clustering on RFM Score data so that it can meet the key assumptions of Kmeans algorithm, which are:

The varaiables should be distributed symmetrically
Variables should have similar average values
Variables should have similar standard deviation values
<img width="1081" height="589" alt="image" src="https://github.com/user-attachments/assets/fa811162-603e-4a52-a6d0-7e447d76eba5" />


As you can see from the above plots, all the variables do not have a symmetrical distribution. All of them are skewed to the right. To remove the skewness, we can try the following transformations:

Log transformations
Box-Cox transformations
Cube root transformations
The log transformation cannot be used for negative values. However, this data do not have any negative values since it is a customer transactions dataset.

After performming log transform and standardising the date, Skewness has been removed

<img width="1055" height="589" alt="image" src="https://github.com/user-attachments/assets/125e967b-c6c1-4261-b7ce-9a11d4f654fc" />



Clustering with K-means Algorithm

I performed K-means Clsutering on the data and follwed the 'Elbow Method' to get the optimal number of clusters. One can also use silhouette analysis to find the optimal number of clusters. For the purpose of this analysis, I have only used the elbow plot method.

<img width="625" height="279" alt="image" src="https://github.com/user-attachments/assets/a239be7e-0e66-4c46-95f5-7873546b76b5" />


From the above plot, the optimal number can be taken as 3 or 4 or 5.

So, after grouping the data in their clusters, for each value among 3, 4 and 5 For interpreting this segment, I drew Snake Plot fro all three values.

<img width="1088" height="278" alt="image" src="https://github.com/user-attachments/assets/a5721d99-eb33-440d-9c6a-0c6b677d290b" />


From the above snake plot, we can see the distribution of recency, frequency, and monetary metric values across the clusters. The clusters seem to be separate from each other, which indicates a good heterogeneous mix of clusters. Best happens for k=3. But k=4 happens to be more practical.

As the final step in this analysis,I extracted this information now for each customer and grouped them in the clusters formed that can be used to map the customer with their relative importance by the company:

This can be approched by finding the relative importance of each attributes for each clusters so that the company can focus more on the attribute of max importance for a particular cluster of customers. Ths was calculated by dividing the Mean value of attributes of each cluster and dividing it by the overall population average. A heatmap was plotted for the result:

<img width="449" height="264" alt="image" src="https://github.com/user-attachments/assets/2a7430c8-1cc7-4b3c-9892-f8e2defa8f5d" />


Final Thoughts
From the above analysis, we can see that there should be 4 clusters in our data. To understand what these 4 clusters mean in a business scenario, we should look back the table comparing the clustering performance of RFM Segmentation Model and 4 clusters for the mean values of recency, frequency, and monetary metric. On this basis, let us label the clusters as ‘New customers’, ‘Lost customers’, ‘Loyal customers’, and ‘At Risk customers’.

MY INTERPRETATION

<img width="1142" height="331" alt="image" src="https://github.com/user-attachments/assets/167633a0-8113-405d-9193-787f24fe4160" />


FURTHER IMPROVEMENT

Product Category could be incorporated into the segmentation. Further product description can be used to derive the product categories with the help of NLP.
Conducting deeper segmentation on customers based on their geographical location, and demographic and psychographic factors.
Taking other factors such as geographical location, demographic, psychographic factors and purchase history into consideration we can build a predictive model to predict thier next purchase for them and for the customers with similar attributes.# Customer-Classification
