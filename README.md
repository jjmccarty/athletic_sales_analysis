# athletic_sales_analysis
This is the Module 5 Challenge for Pandas.  The goal of this challenge is to perform some basic data manipulation and evaluation using the GroupBy method, pivot_tables and binning. 

Work is completed using Jupyter labs and assumes that each prior portion of the exercises provided are run in sequence to ensure proper execution of the code. 

## Section 1
Section 1 of the exercise is used to perform some basic data validation to ensure assumptions about data structures and data types are valid before concatenation of the data. 

We pull in 2 data files for 2020 and 2021 fictious sales data, use Pandas to load this data as a DataFrame object and output the DataFrames.  

### Verifying columns and row couns
Initially we output to DataFrame for the both the 2020 and 2021 sales data.  This allows us to verify that the columns are of the same count (12 columns) and understand the number of rows in each in data set. 

We can further run the ```info``` method to output the columns and their datatypes giving some indication that both datasets are consist in the data they provide prior to concatenation. 

Once leveraging ```concat``` to merge the dataset we can verify the count from both prior individual datasets now equal the row counts in our merged data. 

### Checking for and handling null data values
We utilize the ```sum``` of the ```isnull``` method on the DataFrame to look for the occurance of NaN values and find that none are present so no additional action is required. 

### Modification of column data types
Evaluation of the data shows that the invoice_date is currently listed as an object datatype.  In this we wish to modify this datatype to a DateTime object in preparation for our analysis.  We can convert this data via multiple mechanisms

1. Leveraging ``` astype ``` on the DataFrame column as in:  
>```concat_sales['invoice_date'] = concat_sales['invoice_date'].astype('datetime64[ns]')```
2. Leveraging the ```to_datetime``` method from Pandas as in :
>```pd.to_datetime(concat_sales['invoice_date'])```

This will convert the data from an ```object``` to a ```DateTime``` and can be verfied through an ```.info``` call on the DataFrame.


## Section 2
Section 2 asks us to determine the answer to the following question:
> Which region/city/state sold the most units of product.

This utilizes the ```GroupBy``` method and the ```pivot_table``` method from our DataFrame to order our data set based a specified index of data and aggregating the data we wish we to interrogate.

Both the ```GropuBy``` and ```pivot_table``` methods are used to demonstrated that both options are viable for data manipulation and evaluation in the same way. 

For this exercise we are grouping data by ``` region, state, city ``` and finding the ```sum``` or total count of the ```units_sold``` for that grouping. 

Data is sorted highest to lowest for output

## Section 3

Section 3 asks the following:
> Which region/state/city has the most total sales?

Section 3 provides a repeat of the section 2 exercise, however we substitue the ```total_sales``` as the data to evaluate to find our answer.  

## Section 4

In section 4 we want to know
> What retailer had the most total sales by region/state/city?

This is simply a further extension of our Section 3 exercise, however we add an additional grouping value of ```retailer``` proving for an index of ```retailer, region, state, city```.  

Otherwise our exercise is similar to the prior sections. 

## Section 5
In section 5 our exercise we are looking as some analysis that is drilled down a little further.  In this case we want to know 
> What retailer sold the most units of products by region/state/city for Women's Athletic Footwear specifically. 

This requires that further filter the data by only ```product``` that is ```Women's Athletic Footwear```.  To do this we are using the ```.loc``` option on the DataFrame for the ```product``` data. 

When we determine how we want to identify these products it may be useful to understand how structured our data is.  In this case we are assuming the data has some standardization in how it is collected and are performing the following on the DataFrame

> ``` df.loc[df['product']=="Women's Athlethic Footwear']```

If our dataset was not standardized it might make more sense to evaluate the string contents for similar data rather than a hard ==.  Identifying the unique values in the ```product``` data coul assist with evaluating the standardization of the data in this case. 

From this point analysis of the data is simply utilzing the ```GroupBy``` and ```pivot_table``` as we have in prior exercises to answer the question asked. 

## Section 6

Section 6 asks:
> What is the day with the most total sales for Women's Athletic Footwear?

To perform this analysis we can utilized the DataFrame created in section 5 and create a pivot table with an ```index``` of the ```invoice_date``` and utilize the ```sum``` for the ```total_sales```

We further want to know the total sales for each day, so we utilze the ```resample``` method on the DataFrame to organize the data by the Day 

>```df.resample('D').sum()```

## Section 7

Section 7 allows us to further resample the data based on our dates.  In this case we are asking the question:

> What week had the most sales for Women's Athletic Footwear?

In this case we are using the ```resample``` method again, however we are specifing ```W``` as the rule to organization the data by week 

> ```df.resample('W').sum()```


