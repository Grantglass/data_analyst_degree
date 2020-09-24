# How COVID has influenced Bike use in the Bay Area
## by Grant Glass


## Dataset

It looked like the Ford Bikes Dataset is quite old, so I wanted to see what the current state of the service was and if COVID did anything to influence ridership.

Bay Wheels is a regional public bicycle sharing system in the San Francisco Bay Area, California operated by Motivate in a partnership with the Metropolitan Transportation Commission and the Bay Area Air Quality Management District. Bay Wheels is the first regional and large-scale bicycle sharing system deployed in California and on the West Coast of the United States. It was established as Bay Area Bike Share in August 2013. As of January 2018, the Bay Wheels system had over 2,600 bicycles in 262 stations across San Francisco, East Bay and San Jose. On June 28, 2017, the system officially re-launched as Ford GoBike in a partnership with Ford Motor Company. After Motivate's acquisition by Lyft, the system was subsequently renamed to Bay Wheels in June 2019. The system is expected to expand to 7,000 bicycles around 540 stations in San Francisco, Oakland, Berkeley, Emeryville, and San Jose.


On Mar 17, 2020 San Francisco enacted a shelter in place, which drastically reduced car traffic in the bay area. I am going to investigate whether how this might have reduced or increased ridership.

In response to COVID(starting on March 19th), Bay Wheels offered a 30-day program to give critical healthcare workers free bikeshare memberships. Eligible healthcare workers can sign up through their employer to access unlimited 45-minute trips on Classic bikes and ebikes for 30 days. Did anyone take advantage of this?

https://www.lyft.com/bikes/bay-wheels/system-data

This data set includes information about individual rides made in a bike-sharing system covering the greater San Francisco Bay area. I will merge both January, Februrary, and March's data together. The dataset includes the following features : Trip Duration in seconds , Start Time and Date , End Time and Date , Start Station ID , Start Station Name , Start Station Latitude , Start Station Longitude , End Station ID , End Station Name, End Station Latitude , End Station Longitude , Bike ID , User Type , and  Rental Access Method. 


The dataset is the result of merging 4 files(January, February, March, April (2020)). It has 23 features and 989,266 rows.

Pulling the data down and looking at it on Excel shows us that

January's Data: 295855 trips
February's Data: 432355 trips
March's Data: 176800 trips
April's Data: 84260 trips

We see that there is a clear downturn in April on overall trips.
But what can the data tell us about the behaviors of the users of Bay Wheels?


This dataset needed much cleanup! The April data was tagged a little differently like Ride ID instead of Bike ID. So I created a consistent id column. I dropped uneeded categories. Some of these like ridable_type and rental_access_method are completely different variables. user_type and member_casual are essentially the same thing, so I combined them. The wording for user types changed in April, so I made casual/customer the same and member/subscriber the same. April also didn't include a duration column, so I created that from the start and end times. I also needed to standarize the started at and end at to datetime data, so all the months fit together and I could look at all the data together. 




## Summary of Findings

Looking at the duration of the trips in mintues instead of seconds gave me a much clearer looking distribution. The average trip took about 15 minutes, but we see that in the end of March and in April, there was a huge spike in durations, due to the promotion of riding free for a month for healthcare workers. While there was a super user every now and then, there were much more in the COVID period. It also looked like more people took trips during COVID as seen in the density visualization. As I found in the scatterplot, there were many riders that never turned in their bike at the end of the day, since it was now free. It is interesting then, since there would be less available bikes, but there was still an increase in overall riding. 

I thought looking at where the bikes were being ridden might help me better understand trends and I saw three major areas (East Bay, San Jose, and San Francisco). The San Jose looks like it spreads out the most, which makes sense since there are less public transportation options in San Jose. When I connected the points using ArcGIS, I found that many people took the bikes between these areas (these were all the late March and early april trips). 


## Key Insights for Presentation

During the pandemic, we can see that there is a longer duration of trips for customers, but not an increase of distance. Since the rides were free for many customers, they just kept the bikes, but it looks like they took similar distance lengths (with some outliers). You can see that there are some customers that even go from the east bay into San Francisco, which were probably those longer trips. Looking at types of account against distance and duration of trip gave us a closer look into the behaviors of riders before and during the pandemic.


In March, we saw a sharp decrease in the casual/non-member riders, since many of these riders were probably just for fun or an alternative to other forms of transportation. However, the members seemed to always ride similar patterns, inidcating that even in the pandemic, this is their main mode of transportation.