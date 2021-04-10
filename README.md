# SIADS691-Covid-Real-Estate
Aditya & Chris

THIS NOTEBOOK SUCCESSFULLY PULLS ALL HOME SALES TRANSACTIONS IN EACH OF THE 74 COUNTIES IN CALIFORNIA using ATTOM API. 
For each county, 1 text file is generated. This means 74 files will be generated. 71 are generated as 3 counties have no transactions with our criteria

The following variables in the code can be easily changed to expand or contract search results. Currently we set:
1) FROM DATE - 1st Oct 2019 (Covid start)
2) TO DATE - 1st April 2021
3) Minimum transaction size - $500K
4) Maximum transaction size - $5M

Set the maximum number of records fetched with each API call to be 50,000 which is more than sufficient. This is through the ‘pagesize’ query parameter.

## ignore below

API Challenges:

1) Data is very granulated.
First find the geoID for all counties using the Area endpoint. Then iterate over geoID for all transactions using /properties/sale endpoint

2) Could not iterate over 74 counties with 74 API calls. After about 15 calls, the status header itself was not returned. 
Solution: Ran in batches of 10 api calls. So 10 counties in 1 for loop. Do this 7 times.

3) Usage limits exceeded
Solution: created another developer account for new API key



