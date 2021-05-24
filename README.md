# Covid-19’s Impact on the Value of Single Family Residences 

Authored by: Aditya & Chris

## Step 1: Pull ATTOM Data
https://github.com/adityahpatel/SIADS691-Covid-Real-Estate/blob/main/00.API_CA.ipynb
https://github.com/adityahpatel/SIADS691-Covid-Real-Estate/blob/main/00.API_NY.ipynb
These two notebooks pull real estate transaction in each of the 74 California counties and 90 New York Counties.
#### Maximum API results returned per query is limited to 10,000 
Using custom function salesdata_scraper_bycounty() used on https://api.gateway.attomdata.com/propertyapi/v1.0.0/sale/snapshot to query:
1) FROM DATE - 1st January 2019
2) TO DATE - 1st April 2021
3) Minimum transaction size - $200K
4) Maximum transaction size - $50M
5) County_geoid

Each of these generated a JSON file, which is saved in: (https://github.com/adityahpatel/SIADS691-Covid-Real-Estate/tree/main/datasets) 

The incremental time slicing method left us with 322 files for California, 166 New York files and over 1.5 million transaction records with 43 features for transactions between January 1, 2019 to March 4, 2021
 
## Step 2: Dask Setup : Data Manipulation
https://github.com/adityahpatel/SIADS691-Covid-Real-Estate/blob/main/01.DASK_Setup_Processing_API_Files.ipynb

## Step 3: Exploratory Data Analysis
https://github.com/adityahpatel/SIADS691-Covid-Real-Estate/blob/main/02.EDA.ipynb
- Due to data integrity issues we decide to focus on California. Specifically Los Angeles & San Francisco

## Step 4: Correlation Analysis California
https://github.com/adityahpatel/SIADS691-Covid-Real-Estate/blob/main/03.Correlation_CA.ipynb
- Regression line
- AutoCorrelation
- Time Decomposition
## Step 5: Causal Inference 
https://github.com/adityahpatel/SIADS691-Covid-Real-Estate/blob/main/04.Causal%20Inference_Piece.ipynb
- Difference in Difference Method

Treatment Variable: 7-day Rolling Average Per 100k
Outcome Variable: Median home price of Single Family Homes (in USD)

Treatment group: Los Angeles County   
Control group: San Francisco County

Post-Treatment Period: 
June 22, 2020 to July 22, 2020

Pre-Treatment Period: 
June 22, 2019 to July 22, 2019

## Step 6: Report
https://github.com/adityahpatel/SIADS691-Covid-Real-Estate/blob/main/final_exports_pdf_charts_pkl/57-cwestend-adityahp.pdf

- Charts, python objects(pkl), and PDF exported to final_exports_pdf_charts_pkl folder

##  -------------------- Data Sets --------------------------

Covid-19 Cumulative Data
https://github.com/nytimes/covid-19-data/blob/master/us-counties.csv

Covid-19 Rolling Data
https://github.com/nytimes/covid-19-data/tree/master/rolling-averages

Real Estate Transaction Data
https://api.gateway.attomdata.com/propertyapi/v1.0.0/sale/snapshot


Informational resource for descriptive purposes or referenced for calculations.(*) 

Area Median Income Data*
https://www2.census.gov/programs-surveys/saipe/datasets/2019/2019-state-and-county/est19all.xls

Mortgage Rates*
http://www.freddiemac.com/pmms/docs/30yr_pmmsmnth.xls

Home Price Index*
https://fred.stlouisfed.org/series/CSUSHPISA

CA Population Data*
https://worldpopulationreview.com/us-counties/states/ca

NY Population Data*
https://worldpopulationreview.com/us-counties/states/ny
