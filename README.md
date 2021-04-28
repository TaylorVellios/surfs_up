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

# Summary
