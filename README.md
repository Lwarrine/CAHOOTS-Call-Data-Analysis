# CAHOOTS-Call-Data-Analysis
Data Analysis of call data in order to answer whether CAHOOTS and EPD services arrival times vary by call priority, by time of day, by day of week, and by call type. A full project report can be found under the CAHOOTS Project Report file
## Combining Data
The data is initially sepearted into a different csv file for each year and needs to be combined into one csv file. Combine.ipynb combines these csv files into 1 csv file assuming it is run in same folder as all the individual files.
## Cleaning Data
Clean.ipynb takes the csv file made with Combine.ipynb and adds the following new columns:

dispatch_time - time for a unit to be dispatched in minutes  
arrival_time - time for a unit to arrive in minutes  
clear_time - time for a unit to clear call in minutes  
CAHOOT - wheter the call's primary response unit was a CAHOOTS unit  
Hour - the hour of the day using 24 hour time  
DoW - the day of the week (0-6, Mon-Sun)  

Additionally rows where dispatch_time, arrival_time, clear_time are missing or <= 0 are removed.
Calls where the call source are 'SELF' are also removed as many of these are incidents where the a unit is already on scene and not what I am intrested in looking at i.e, a traffic stop

## Analyzing Data
Graphs are created comparing arrival times between EPD and CAHOOTS for each hour of the day, day of the week, call priority, and call nature. This is additionally done with how long it takes EPD and CAHOOTS to clear a call and move on to the next one. An independtent t-test is used to see if the difference betwwen EPD and CAHOOTs is statistically significant. 
