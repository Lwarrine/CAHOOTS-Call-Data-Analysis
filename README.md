# CAHOOTS-Call-Data-Analysis
Crisis Assistance Helping Out On The Streets (CAHOOTS) is a service that can be deployed alongside or instead of the police to respond to 911 calls. They are equipped to handle medical and mental health emergencies. They have a maximum of two vans in service at any one time. There have been many complaints about CAHOOTS response times, claiming that they are very slow in responding and arriving to calls. This leads to the primary research question of this project; how EPD and CAHOOTS arrival times and clear times vary by call priority, by time of day, by day of week, and by call type.

*A full write up can be found in the CAHOOTS Project Report pdf
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

## Conclusion
Overall, when it comes to arrival times, CAHOOTS is generally slower than EPD, but when this happens can help give some insight as to possible causes for the difference in arrival times. CAHOOTS arrival times slow down when call volume increases, indicating a possibility that their resources (maximum of 2 vans at any given time) are stretched too thin, causing people to have to wait longer for service. There might also be systematic differences in how CAHOOTS handles calls from EPD (as seen with the “SELF” call source). One possible reason worth noting, but where this data is unable to give a clear answer, is how the absence of sirens affects CAHOOTS. The CAHOOTS vans are not equipped with sirens so they can get stuck in traffic like any other car. Once on the scene though, CAHOOTS is generally faster at clearing a call than EPD.

A caveat to this report is that it is a preliminary investigation into the results and limited by time and resources. Many of the conclusions and reasonings proposed in this report should be investigated further to confirm any relationships. Just because CAHOOTS is slower when there are more calls in an hour, doesn’t guarantee it's because of a lack of resources. It could also be because of another reason such as the general busyness of the city. 

Further investigation should be done into how sirens affect CAHOOTS arrival times, what the exact causes of CAHOOTS being slower to arrive are, and how arrival time might indicate clear times for certain types of calls. 
