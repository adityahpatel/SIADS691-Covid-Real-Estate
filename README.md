# SIADS691-Covid-Real-Estate
Aditya & Chris

THIS NOTEBOOK SUCCESSFULLY PULLS ALL HOME SALES TRANSACTIONS IN EACH OF THE 74 COUNTIES IN CALIFORNIA using ATTOM API. 
For each county, 1 text file is generated. This means 74 files will be generated. 71 are generated as 3 counties have no transactions with our criteria


Each of these generated files is imported & converted into pandas dataframe making it easy to work with.

The following variables in the code can be easily changed to expand or contract search results. Currently we set:
1) FROM DATE - 1st Oct 2019 (Covid start)
2) TO DATE - 1st April 2021
3) Minimum transaction size - $500K
4) Maximum transaction size - $5M

Set the maximum number of records fetched with each API call to be 50,000 which is more than sufficient. This is through the ‘pagesize’ query parameter.

####  -------------------- Documentation on challenges --------------------------

API Challenges:

1) Data is very granulated.
First find the geoID for all counties using the Area endpoint. Then iterate over geoID for all transactions using /properties/sale endpoint

2) Could not iterate over 74 counties with 74 API calls. After about 15 calls, the status header itself was not returned. 
Solution: Ran in batches of 10 api calls. So 10 counties in 1 for loop. Do this 7 times.

3) Usage limits exceeded
Solution: created another developer account for new API key

4) Determining how to run API calls so as to not meet the 250 call limit. How to split up the counties? Some had 100 transactions and some had 100,000 transactions. But we wouldn't know which county had how much without making API call. So used up a lot of calls in this process. 

6) Problem we ran into was API call returns 10,000 records maximum. 
Solution: For year 2019, make 74 API calls. 10 of those truncated i.e. fetched only 10,000 records. 6 of those 10 had over 10,000 transactions in 6 months, so made more 
API calls with time duration of 2 months. 1 of those 6 had more than 10,000 records in 2 months, so had to split again and run API calls for that county CO06037. Turns out
that was Los Angeles county. Total of 110 API calls were made in semi-automatic/manual way. This is excluding over other exploratory calls to figure out which county gave how many transactions. We had a limit of monthly 250 calls and we exhausted those with 2019 year alone!

5) Hit monthly limit of 250 calls. We had FULL data without truncation but only for 1 year i.e. 2019. Went on other macbook and created new attom api developer account in spouse's name and started fetching data for 2020. Just 250 calls is too low.  


####  -------------------- Data Sets --------------------------

COVID-19 DATASETS:

1) CDC_COVID-19_Case_Surveillance_Public_Use_Data_with_Geography.csv 
( source: https://data.cdc.gov/Case-Surveillance/COVID-19-Case-Surveillance-Public-Use-Data-with-Ge/n8mc-b4w4 )

2) jh_time_series_covid19_confirmed_US.csv , jh_time_series_covid19_deaths_US.csv
( source: )

3) nyt-us-counties.csv ( source: https://github.com/nytimes/covid-19-data)

INCOME DATASETS:

1) est19-all_income.xls , est19-ca_income.csv , est19-nj_income.csv , est19-ny_income.csv
( source: https://github.com/CSSEGISandData/COVID-19  )

REAL ESTATE DATASETS: