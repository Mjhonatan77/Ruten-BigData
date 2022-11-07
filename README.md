# Ruten-Find-reasonable-category-price-of-goods
---
### PROBLEMATIC:
"Based on the demand for traffic, sellers do not take the initiative to un-list item from the shelves after the goods are sold. Instead, they deliberately increase the price of items to an unreasonable level, and let them stay on the shelf as an advertisement to earn traffic and attranck buyers to browse. If we can accurately identify the reasonableness of the price, it will help on optimizing the search on the site"


![ps5 example](https://user-images.githubusercontent.com/101158689/200383556-47e9a389-f0f2-4dfa-97cb-f7e2be7451ce.jpg)
In here we can observe that the price has exaggerated change may be due to unavailability.

### SOLUTION: 
In order to handle this problematic and find a feasible price range for a specific item 3 methods were used, an important thing to clarify is that all the items to be analyze have to be similar or the same:
#### Method 1(Confidence Interval Approach): 
Using the “Item_Id”, “Price”, “Order_qty” and “Order_Id” of the ''Order'' dataframe from the item you want to analyze, the mean and standard deviation of the prices of each item sold is found. Then a Confidence interval of  95% with Z=1.96 was used to find the Lower and Upper Limit. Finally, this will represent the minimum and maximum reasonable price.

#### Method 2(Regression Approach): 
Utilizing the results found in 2, we drop these items with Unreasonable prices, in order to clean the database and have a more accurate reasonable price. Next we clean the item_title field and create two new columns, one for the Chinese language and the other for the English language. Then, we preprocess each column depending on the features of the languages. Finally, we fit the mentioned columns and the price to a LGBM Regressor. To obtain the reasonable price we input a keyword and the model will return the reasonable price. This approach works under the assumption that all the items fed to the regressor are similar.

#### Method 3(Quartiles Approach): 
First, making a Box plot diagram of the Price of the item, from the ''Order'' dataframe,and also from the ''Goods'' data frame with dropped outliers found in step 2, was made. Then, the Quartiles 1 (25%) and 3 (75%) were utilized from the two Box plots to do an overlap. To do this, we have to find the max value of the Q1 between the tho dataframes and the min value of the Q3 also from the two dataframes. And these two values would represent the minimum and maximum reasonable price.
EXAMPLE IMAGE:




### Software
- Visual Studio Code
- Python
- Jupyter Notebook

### References
:::露天拍賣:::關於露天, https://pub.ruten.com.tw/about/indexen.html. 
