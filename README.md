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

## Section 3

## Section 4

## Section 5

## Section 6

## Section 7
