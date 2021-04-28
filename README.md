# surfs_up
SQLite, SQLAlchemy, Pandas

# Overview
Analyzing weather data on Hawaii for a prospective Surf Shop/Ice Cream Parlor.</br>
The biggest roadblock for obtaining potential investors is the local weather of hawaii - temperature and precipitaion.</br>
Can we find data to convince investors to jump on board?<br></br>

hawaii.sqlite is a database file containing two tables:
* Measurement
* Station


### Measurement
This table contains daily temperature and precipitation data for 9 weather stations across Hawaii.</br>
The Measurement table contains almost 8 years of weather data (2010-01-01 to 2017-08-03)</br>
Its columns include:
* Index
* Station ID Number ("station")
* Date ("date")
* Precipitation ("prcp")
* Temperature ("tobs")


### Station
This table contains specific information regarding each weather station</br>
Its columns are:
* Index
* Station ID Number ("station")
* Name ("name")
* Latitude Coordinate ("latitude")
* Longitude Coordinate ("longitude")
* Elevation ("elevation")

Using sqlalchemy with a Jupyter Notebook, let's dive in and see if we can query some useful data.</br>

# Results
The first question we are asked is the annual sustainability of a Surf Shop/Ice Cream Parlor.</br>
Hawaii is known for being warm, but does it stay that way year round?</br>

After setting up our sqlalchemy session, I used two simple queries to pull all temperatures from the Measurement table filtered by month: June and December.</br>
After making the results DataFrames, the descriptions of each are below.</br>

![june](https://user-images.githubusercontent.com/14188580/116469089-4f2dc780-a837-11eb-9c29-73fbd4452d1c.PNG)
![dec](https://user-images.githubusercontent.com/14188580/116468988-2c9bae80-a837-11eb-95c9-f12ff973a16f.PNG)
</br>

From looking at average temperatures for two months from 8 years worth of temperature data, it is pretty evident that Hawaii live up to its warmth claims.</br>

Takeaways:
* With a maximum temperature of 83 in December, and an average of 71.04, the surfing/ice cream market can survive year round in Hawaii (temp wise)
* Temperatures between June and December are not very different, the biggest difference is the minimun value.
* Beware that with our current dataset, we have more values for June than we do for December.</br>
While another month's worth of data might not outweight the current results significantly, it's good to stay on your toes.</br>

# Summary and Diving Deeper
Since there is no reasonable investor who would be satisfied with results for only July and December, I wrote a function that can return average temperatures or precipitation levels for each month across every weather station. The output for monthly precipitation averages is below:</br>
![function_output](https://user-images.githubusercontent.com/14188580/116471045-d54b0d80-a839-11eb-87f0-414275313441.PNG)
</br>
Next, I made a dataframe of the Station table and merged it with our average data per station.</br>
From this point on I have obtained all of the data I would need to plot to show potential investors.</br>

After some initial plotting, I made an executive decision to drop two stations from these results:
* USC00518838
* USC00516128

Below is a depiction of the scaled value of average precipitation in December for each Station along with that station's elevation.</br>
![elev](https://user-images.githubusercontent.com/14188580/116474576-4db3cd80-a83e-11eb-837e-eae3ce53d784.png)

While the ratio between elevation and precipitation is not significant, there are two reasons why I chose to omit these locations:
1. We are looking at weather data to avoid precipitation as much as possible for maximum yearly profits.</br>
   With elevation comes increased precipitation.</br>
2. Why on earth would anybody open a surf shop anywhere but as close to sea-level as possible?</br>
   Our goal here is to get a return on an investment for a specific retail store and the higher elevation weather data is only going to skew our averages upwards.</br>
   
From here, I decided to plot every month's average by every station to see if there were specific areas in Hawaii that average lower than the rest.</br>
![download (1)](https://user-images.githubusercontent.com/14188580/116476065-50afbd80-a840-11eb-9218-7ca129e16e73.png)
</br>
Given the data above, I would feel confident researching the areas by USC00519397, USC00511918, or USC00517948 as prime locations for a surf shop/ice cream parlor.</br>

![prim_locs](https://user-images.githubusercontent.com/14188580/116476585-0aa72980-a841-11eb-9922-506a273ec35c.PNG)

Now to find out if there is any foot-traffic or a surfable beach nearby....

   
