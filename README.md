# clustering-ecommerce-DS008  
---  

## Ecommerce Clustering Project  
---

## Executive Summary  

Finding customer segmentation & characteristic are important for business operational and marketing purposes. K-Means clustering method is employed to define different customer segmentation. 3 out of 6 clusters were found to be meaningful to analyze. They were cluster number 0, 3, and 4.  

From these 3 clusters, they had different characteristics. Here're the list:  

| **Variable** | **cluster 0** | **cluster 3** | **cluster 4** |
| :--- | --- | --- | --- |
| Customer size % | 20.76% | 23.50% | 28.37% |
| Market Share (Million) | 3.00 | 2.80 | 4.05 |
| Payment sequential | 1.00 | 1.00 | 1.00 |
| Payment installment | 2.00 | 1.00 | 2.00 |
| Payment value | 115.95 | 90.36 | 114.22 |
| Order purchase in month (most likely) | 3 | 6 | 8 |
| Order purchase in date (most likely) | 15 | 16 | 16 |  

<br>  

## Planning Phase  
---

### 1. Business Needs
***How would you as a Data Scientist find meaningful segmentations for a better targeting marketing?***   

At the end of this research, the outcomes are:
- information on customer unique behaviours through EDA
- number of segmentations found through clustering
- description of unique attributes from each segment through descriptive statistics
- business recommendations  

### 2. Business Process  
From the dataset, the business is an online ecommerce.  


So, the business process or users funnel in online setting, I assume it would be like:
- Customers visit ecommerce -> search for items -> purchase items -> shipping items -> receiving items 
- Customers will have to sign up for purchasing items
- The ecommerce communicates with the customers through mails and/or push notifications


### 3. Business Requirements  
**a. The research timing**  
From the dataset, I assumed that the research is held after some periods of time (maybe 1-3 month), It would be not meaningful if the period is too short or it would be wasted for the owner if the period is too long too. Then, I would conclude that this research is held to give updated information about customer segmentation for each month/each quarter. Because of this updated information, the marketing team would be always well informed about the behaviour of customers and also make a better target marketing. On the other hand, the customers will receive more meaningful information.   

**b. The research frequency**  
From my conclusion above in the `a. The research timing`, I make another conclusion that this research runs montly/quarterly basis.  


### 4. Data Source  
The datasets are consisted of three different tables:
1. In the orders_dataset, the columns inside are:
    - `order_id` :Unique identifier of orders.  
    - `customer_id` : Key to the orders dataset. Each order has a unique customer_id.  
    - `order_status` : Reference to the order status (delivered, shipped, etc).
    - `order_purchase_timestamp` : Shows the purchase timestamp.
    - `order_approved_at` : Shows the payment approval timestamp.
    - `order_delivered_carrier_date` : Shows the order posting timestamp. When it was handled to the logistic partner.
    - `order_delivered_customer_date` : Shows the actual order delivery date to the customer.
    - `order_estimated_delivery_date` : Shows the estimated delivery date that was informed to customer at the purchase moment.
    
    
2. In the customers_dataset, the columns inside are:
    - `customer_id` : Key to the orders dataset. Each order has a unique customer_id.
    - `customer_unique_id` : Unique identifier of the customer.
    - `customer_zip_code_prefix` : First five digits of customer zip code.
    - `customer_city` : Customer city name.
    - `customer_state` : Customer state.  


3. In the order_payment_dataset, the columns inside are:
    - `order_id` : Unique identifier of the order.
    - `payment_sequential` : A customer may pay an order with more than one payment method. If they does so, a sequence will be created to accommodate all payments.
    - `payment_type` : Method of payment chosen by the customer.
    - `payment_installments` : Number of installments chosen by the customer.
    - `payment_value` : Transaction value.  
    
    
    
<br>  

## Solution - Model  
---

### 1. Exploratory Data Analysis  
1.1. Data Structure (datatype, number of samples, univariate stats, multivariate)    
1.2. Quality Investigation (duplication, missing value, outliers, unwanted entries)  
1.3. Content (correlation analysis, data visualisation= distribution, pairplot)  

### 2. Data Preprocessing  
2.1. Data Cleaning (remove or imputation)  

### 3. Feature Engineering  
3.1. Decompose timestamp, interval between each shipping process(from purchase until delivered), difference between estimated and delivered  
3.2. Numerical encode: encode order_status based on the number state of process  
3.3. Dummy encoder: `payment_type` - drop the undefined payment_type first  
3.4. Payment related: `total_payment` as `total_sequential` times `payment_value`  
3.5. Geography & economy related: avg/max/std/count `total_payment` for each city, avg/max/std/count `total_payment` for each state, avg/max/std/count `total_payment` for zipcode

### 4. Feature Selection  
4.1. Principal Component Analysis (PCA): for dimensionality reduction  

### 5. Training  
5.1. K-Means Clustering Method  
5.2. Elbow Methods  

### 6. Evaluation  
6.1. Descriptive statistics  

### 7. Conclusion  
6.2. Finding the unique attributes for each cluster  

    
