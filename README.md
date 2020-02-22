# Project-2

Shamber Goldstein | February 21, 2020 | B ME 450 | Project 2: Meteorology Package 

# Introduction:

The goal of this project was to analyze the patterns of rain rate and wind speed over a year at two different sites. This was done by extracting data from the Bulk Meteorology Instrument Package on the Ocean Observatories Initiative (OOI) website. The Bulk Meteorology Instrument Package measures a variety of parameters that characterize weather conditions above the sea surface, including wind speed at the surface and rain rate. Data was analyzed at the Oregon Shelf Surface Mooring site and the Oregon Offshore Surface Mooring site. As described on the OOI website, “the Coastal Endurance Oregon Shelf Surface Mooring is located on the Continental Shelf, approximately 80 meters deep. The Continental Shelf-Slope area off the Oregon coast is a highly productive, dynamic upwelling environment…the Surface Mooring contains instruments attached to a Surface Buoy floating on the sea surface, Near Surface Instrument Frame 7 meters below the surface, and a Seafloor Multi-Function Node (MFN) located on the seafloor” [1]. The Coastal Endurance Oregon Offshore Surface Mooring is the same but located approximately 550 meters deep. 

In this project there were three main sections. The first was to plot wind speed and rain rate vs. time for each site. These plots were to also include color indicated time periods demonstrating when the sites were windy and rainy, rainy but not windy, windy but not rainy, and not windy or rainy. The next section was to plot the cross cross-correlation functions between the wind speeds at each site and between the rain rates at each site then analyze their maximum correlations, time lags, and any existing relationships. The final section was to plot the monthly averages of wind speed and rain rate for each site and analyze patterns, as well as which months had the maximum and minimum wind speed and rain rate. 

# How I Did It:

My approach for this project was to use what I learned while coding Project 1 and make tweaks to make it fit this projects requirements. I imported my data from the OOI website in the same way that I did in Project 1, through the use of the link to the data. However, this project required me to separate out the data because the file sizes were too large. I did this by separating out the data into a different URL for each month. I did it this way because a month had an acceptable amount of data points and doing it by month would help me later when needing to plot the monthly averages. The function in this section created a different URL for each month of data. This was possible because the URL for the data at a site is the same for different months with the exception of the start date. I was able to use an inputted start month, day, and year to append it to its corresponding section in the URL. I used a for loop to cycle through progressing months and create this URL for each one. I had to do this function separately for each site because the general URLs were different. 

Once my data was retrieved, I went on to extract the needed variables for the project: wind speed, rain rate, the index of the start of each month, and time. I started this by using the URLs I created to receive the actual data. This simply involved using the provided code on the OOI website that creates a list of all of the data at each URL. I then extracted out only the data I needed for the project. I did this by looping through each data point in a URL, checking if the data point was under one of the needed variable lists, and appending it to a new list of just that variable. This returned me with lists of only wind speed, rain rate, the month index, and time. The time however, was not in the correct format so I had to convert it to local time. I did this by using the provided code on the OOI website that converts the time into the local date. I then converted this local date back into seconds to make it easier to work with. This was done by simply looping though the dates and converting each of them. I also made a function that verifies that the converted time is in order. This simply loops through the data and checks that each consecutive time value increases.

After converting the time I was able to start on the first goal of the project: plotting wind speed and rain rate. A big part of this section was to create the time windows for when the sites were windy and rainy, rainy but not windy, windy but not rainy, and not windy or rainy. I did this by creating a loop that went through the data and passed it through a series of if statements. Each statement would check for one of the time windows by looking at how large the values were for wind speed and rain rate at a time point. I chose numbers for this section that I considered low enough to classify little-to-no rain or wind. After finishing my code, I went back and also made sure these numbers were significantly below most of the monthly averages. If the data fell into one of the windows, it would be plotted as a vertical span in a specified color. Outside the for loop, I plotted all of the wind speed and rain rate values vs. the converted time, on the same plot as the windows. This resulted in a plot with two colored sets of dots representing rain rate and wind speed and 4 different colored backgrounds (vertical spans) showing the different time windows.

After completing this section I went on to the next one: plotting the cross-correlation function. I did this by using the code shown on the website provided in the project instructions [2]. I then simply altered the code slightly so that it would use my variables instead of the ones in the example the website provided. I did this once for wind speeds and again for the rain rates.

The final section was to plot the monthly average wind speeds and rain rates at each site. To do this I created a list of the month names to use for the x-axis of my plot. I then made a nested loop to go through each time value and check if it corresponded to the start of a month by using my month index list. If it did it would take the average wind speed and rain rate from that time value to the time value at the end of the month. When the loop finished I had arrays of the average wind speeds and rain rates which I then plotted against their corresponding months.

# Results/Plots:

Figure 1: Plot of Wind Speed and Rain Rate with Indicated Time Windows: Oregon Shelf Surface Mooring
![alt text](https://github.com/shamgold/Project2/blob/master/Picture1.png "Shelf Plot") 

Figure 2: Plot of Wind Speed and Rain Rate with Indicated Time Windows: Oregon Offshore Surface Mooring
![alt text](https://github.com/shamgold/Project2/blob/master/Picture2.png "Offshore Plot")  

Figure 3: Plot of Cross Correlation Function for Wind Speed at Each Site 
![alt text](https://github.com/shamgold/Project2/blob/master/Picture3.png "Shelf Average Plot") 

Figure 4: Plot of Cross Correlation Function for Rain Rate at Each Site 
![alt text](https://github.com/shamgold/Project2/blob/master/Picture4.png "Offshore Average Plot") 

Figure 5: Monthly Wind Speed and Rain Rate Averages: Oregon Shelf Surface Mooring
 

Figure 6: Monthly Wind Speed and Rain Rate Averages: Oregon Offshore Surface Mooring
 

# Analysis/Conclusions:

Assignment Questions - 

1.	What is the highest correlation and at what time lag for…

a.	Wind Speed?  
b.	Rain Rate? 


2.	What patterns do you see in the monthly averages?

The monthly average wind speeds and rain rates at both sites seem to follow a similar pattern. There a couple exceptions to this. The wind speed peaks up in June-August while the rain rate it low. Then, the rain rate peaks up in October-December while the wind speed is low. You can also see this pattern in the plots with the time windows indicated. Toward the beginning of the year, the time window indicates a lot of times that are both windy and rainy, then in July it gets to be wind and not rainy, then it becomes not windy or rainy, then it becomes rainy and not windy. These patterns make sense if you think about how the weather patterns tend to be in the pacific northwest over a year. The winter months tend to have high amounts of rain and the summer months have low amounts. Wind seems to pick up at the end of winter and continues through spring and summer.  


3.	Which month had the highest rain rate? Which month had the lowest rain rate?

For the shelf site, the highest rain rate was in February and the lowest was in August. It makes sense for this to be the case because there is typically more rainfall in the winter than the summer. For the offshore site, the highest rain rate appeared to also be in February and the lowest was in October.


4.	Which month had the highest wind speed? Which month had the lowest wind speed?

For both sites, the highest average wind speed was in March and the lowest was in October. This makes sense because the weather tends to be windier in Spring and Summer than in Fall and Winter. 


This project resulted in three different sets of graphs that demonstrated the relationships between wind speed, rain rate, time of year, and location. These showed that the site location, on the shelf or offshore, did not make a big difference in rain rate or wind speed, but there was a slightly greater wind speed and lower rainfall rate offshore. The results also showed that both rain rate and windspeed are highest at the end of winter/beginning of spring and the lowest at the end of summer. Finally, the plots showed that rain rate and wind speed follow similar patterns during winter and spring, but tend to follow different patterns in Summer and Fall.

# References:

[1]	Ocean Observatories Initiative. (2020). METBKA. [online] Available at: https://oceanobservatories.org/instrument-series/metbka/ [Accessed 21 Feb. 2020].

[2]	Currents.soest.hawaii.edu. (2020). SEM_EDOF. [online] Available at: https://currents.soest.hawaii.edu/ocn_data_analysis/_static/SEM_EDOF.html [Accessed 21 Feb. 2020].

