# OlistAnalysis
An Analysis of the Brazilian E-commerce Platform - Olist

Understanding the Business Problem

We were tasked with conducting exploratory data analysis to help Olist’s stakeholders gain a better understanding of its historical performance and any recurring trends to take advantage of. To gain a better understanding of the business problem, we had to delve deeper into Olist’s business model and identify the relevant stakeholders.
Olist’s Business Model at a Glance

Olist is an online platform that connects small and micro businesses to larger retailers and marketplaces such as Amazon, Mercado Livre, Americanas, Submarino, and others. Essentially, Olist is a B2B2C business.
Once a customer places an order on any one of these marketplaces, the transaction data is captured by Olist. The sellers are then required to package and ship the order to the customer themselves.

Data Preparation and Cleaning

Identifying Inconsistencies in the Data

1. Difference in Unique Order Count Across the ‘orders’ and ‘order_items’ table:
   
The orders table contains 99,441 unique order ids whereas the order_items table contains 98,666 unique order ids, this suggests that the order_items table does not contain data corresponding to each of the 99,441 unique orders.
To identify the source of this discrepancy, we tried to get a count of the distinct order ids in the orders table by the order status, using the following query:
This time, we found the count of the distinct order ids in the joint order and order_ids table by the order status, using the following query:
By comparing the breakdown across both tables, we found out that a total of 775 orders with different order statuses were not being accounted for in the order_items table, mostly consisting of unavailable orders:

3. Identifying inconsistencies in product categories present in the products table but not in the product_category_name_translation table.
Some rows in the product_category_name column of the products table were left blank. These values were replaced by ‘unspecified’ to indicate that it is not known which category or categories the particular product corresponds to.
Since the blank values were causing problems during the data importation process, these were replaced in Excel using the find and replace feature.
In addition to the blank values, there were two categories that were not present in the product_category_name_english column of the product_category_name_translation table. To ensure a one to one mapping, we added these two categories to the product_category_name_english columns as well.

4. Dealing with blank values in the products table
Upon visual inspection of the products table, we realized some of the rows in each of the fields namely, product_name_length, product_description_length, product_photos_qty, product_weight_g, product_length_cm, product_height_cm, product_width_cm were left blank. These were replaced with 0 to indicate that these dimensions of the product were not specified. However, we chose the number 0 mainly because we were not using these columns in our analysis.

5. Changing format of dates to the MYSQL required format i.e. YYYY-MM-DD HH:MM:SS
While importing the data to workbench, we were prompted to correct the format of the dates in each of the tables where either a date or a timestamp was included. This was accomplished by using Excel’s custom number format feature to the desired format i.e. YYYY-MM-DD HH:MM:SS. Once the date format had been altered, the data was easily imported to workbench.

Data Analysis
After completing the necessary data cleaning and processing steps, we were able to create informative and insightful visualizations. These visual representations allowed us to effectively communicate patterns, trends, and meaningful insights extracted from the processed data. By transforming raw data into visual formats, we made it easier for ourselves and our stakeholders to understand complex information. This process of converting data into visualizations not only facilitated better decision-making but also provided a clearer understanding of the underlying information.

Recommendations

Capitalize on Peak Sale Days and Months
Based on our analysis, we discovered November, December, and October to be the three most popular months in terms of sales volume. Similarly, we also uncovered Mondays, Tuesdays, and Fridays to be the three most popular days of the week. With these insights, Olist can better align its promotional campaigns with these high activity periods.

Offer Improved More Attractive Credit Terms
From our analysis, it is evident that the most popular payment method happens to be credit cards, accounting for nearly 74% of all payments. This suggests offering discounts or promotional pricing specifically on credit card usage can entice customers to shop even more frequently on Olist.
Promote Boleto and Voucher Utilization
Boleto and Voucher collectively account for the remaining 24% of all payments. This suggests boleto and vouchers are also a popular payment method among customers. Encouraging greater utilization of boleto and vouchers could result in greater sales for Olist.
Furthermore, comparing customer demographics with voucher utilization could unveil even more insights to be taken advantage of.

Focus on Growth by Value
Since Olist is a new entrant in the e-commerce landscape, breaking even is likely to be its priority. Unlike larger more established businesses, competing on the basis of order volume or diversification could be more costly.
Based on the dataset, product categories such as pcs, appliances and musical instruments among others have greater order average values than most other categories. Offering promotional campaigns on these specific product categories or prioritizing resources over these could help Olist achieve profitability sooner rather than later.

Go Local!
15% of Olist’s revenue comes from Sao Paulo and 7% from Rio de Janeiro alone. The top 10 cities collectively makeup around 40% of all revenue. By prioritizing these cities and tailoring promotional initiatives to align with local preferences, Olist has the potential to increase its order volume significantly from these specific urban areas.
Incentivize Reviews
59% of all reviews did not leave a detailed comment. This reflects a low level of customer engagement. In the online marketplace, social proof helps build trust among potential customers. Not only should Olist incentivize customers to leave detailed reviews on its own platform but also encourage sharing reviews on popular local social media channels.
