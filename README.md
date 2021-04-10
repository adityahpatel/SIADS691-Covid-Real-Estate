# SIADS691-Covid-Real-Estate
SIADS691 project 

THIS NOTEBOOK SUCCESSFULLY PULLS ALL SALES TRANSACTIONS OF HOMES IN EACH OF THE 74 COUNTIES IN CALIFORNIA.

I’ve named each file with the geoID of the county. Total 74 counties are there in California as per ATTOM. 71 of them contain transactions between $500K and $5M between 1 Oct 2019 and 1 April 2021. The others have 0 transactions - too small

I’ve set the maximum number of records fetched with each API call to be 50,000 which is more than sufficient. This is through the ‘pagesize’ query parameter.

Challenges:


Data is too granulated
First find the geoID for all counties using the Area endpoint. Then iterate over geoID for all transactions using /properties/sale endpoint
 Could not iterate over 74 counties with 74 API calls. After about 15 calls, the status header itself was not returned. 
Solution: Ran in batches of 10 api calls. So 10 counties in 1 for loop. Do this 7 times.
Usage limits exceeded
Solution: created another developer account for new API key

Following can be changed in the code easily:
From date and to date
Prices of housing. $500 seemed reasonable though.


