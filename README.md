# Will a Customer Accept the Coupon?

# Data Description

The attributes of this data set include:
1. User attributes
    -  Gender: male, female
    -  Age: below 21, 21 to 25, 26 to 30, etc.
    -  Marital Status: single, married partner, unmarried partner, or widowed
    -  Number of children: 0, 1, or more than 1
    -  Education: high school, bachelors degree, associates degree, or graduate degree
    -  Occupation: architecture & engineering, business & financial, etc.
    -  Annual income: less than \\$12500, \\$12500 - \\$24999, \\$25000 - \\$37499, etc.
    -  Number of times that he/she goes to a bar: 0, less than 1, 1 to 3, 4 to 8 or greater than 8
    -  Number of times that he/she buys takeaway food: 0, less than 1, 1 to 3, 4 to 8 or greater
    than 8
    -  Number of times that he/she goes to a coffee house: 0, less than 1, 1 to 3, 4 to 8 or
    greater than 8
    -  Number of times that he/she eats at a restaurant with average expense less than \\$20 per
    person: 0, less than 1, 1 to 3, 4 to 8 or greater than 8
    -  Number of times that he/she goes to a bar: 0, less than 1, 1 to 3, 4 to 8 or greater than 8
    

2. Contextual attributes
    - Driving destination: home, work, or no urgent destination
    - Location of user, coupon and destination: we provide a map to show the geographical
    location of the user, destination, and the venue, and we mark the distance between each
    two places with time of driving. The user can see whether the venue is in the same
    direction as the destination.
    - Weather: sunny, rainy, or snowy
    - Temperature: 30F, 55F, or 80F
    - Time: 10AM, 2PM, or 6PM
    - Passenger: alone, partner, kid(s), or friend(s)


3. Coupon attributes
    - time before it expires: 2 hours or one day


<hr>

## Table of Contents: 
1. [Loading The Dataset](https://github.com/arezazadeh/data_analysis_projects#Loading-The-Dataset)
2. [Missing And Duplicated Data](https://github.com/arezazadeh/data_analysis_projects#missing-and-duplicated-data)
3. [Consolidating Redundant Columns](https://github.com/arezazadeh/data_analysis_projects#Consolidating-Redundant-Columns)
4. [Total Observation of Coupon Acceptance](https://github.com/arezazadeh/data_analysis_projects#Total-Observation-of-Coupon-Acceptance)
5. [Visualizing The Coupon Column](https://github.com/arezazadeh/data_analysis_projects#Visualizing-The-Coupon-Column)
6. foot 
7. foot
8. foot 
- bunch 
- daylight come and we want go home 
<br>

<h3>Pending Completion</h3>

<hr>

### Loading The Dataset
```python
import pandas as pd 

data = pd.read_csv('data/coupons.csv')
pd.set_option('display.max_columns', 100)
```
<hr>
<br>

### Missing And Duplicated Data

```python
destination              0.000000
passanger                0.000000
weather                  0.000000
temperature              0.000000
time                     0.000000
coupon                   0.000000
expiration               0.000000
gender                   0.000000
age                      0.000000
maritalStatus            0.000000
has_children             0.000000
education                0.000000
occupation               0.000000
income                   0.000000
car                     99.148534
Bar                      0.843582
CoffeeHouse              1.710817
CarryAway                1.190476
RestaurantLessThan20     1.024913
Restaurant20To50         1.490066
toCoupon_GEQ5min         0.000000
toCoupon_GEQ15min        0.000000
toCoupon_GEQ25min        0.000000
direction_same           0.000000
direction_opp            0.000000
Y                        0.000000
```
* The `car` column is 99% Null, and it seems like it doesnt have any impact to the overall of the dataset. Hence dropping the entire column
* The columns `Bar, CoffeeHouse, CarryAway, RestaurantLessThan20, Restaurant20To50` have some missing values, I have decided to fill them with `never` 
* There are also 74 duplicated row, which are dropped 
```
False    12610
True        74
```
<hr>

### Consolidating Redundant Columns

* below columns have been consolicated:
    - New column is created based on the `Y` column, `acceptance`
    - `toCoupon_GEQ5min`, `toCoupon_GEQ15min`, `toCoupon_GEQ25min` are consolicated to one column `distance` 

    ```
        -----------------------------------------
        | 5 |   15   |   25   |  distance       |
        |----------------------------------------
        | 1 |   0    |    0   |  within 5 min   |
        | 1 |   1    |    0   |  within 15 min  |
        | 1 |   1    |    1   |  within 25 min  |
        -----------------------------------------
    ```
    - `direction_same`, `direction_opp` columns are consolicated to one column `dir` <br>
    - Rename values in `temperature` column to low medium and high in a new column `temp_cat` <br>

<hr>

### Total Observation of Coupon Acceptance
<br>

<li> as shown below, around 56% of the  drivers have accepted a coupon and around 43% of the drivers have rejected it.</li>
<br>
<div style="text-align:center">
<img src="images/total_observation_coupon.png" width=550>
</div>

<hr>

### Visualizing The Coupon Column

* The overall distribution of coupons among the drivers. as indicated below, 32% of the coupons were Coffee House Coupons, and 22% Cheap Restaurants. 
<br>
<br>
<div style="text-align:center">
<img src="images/all_coupons.png" width=550>
</div>


