# World Weather Analysis

## Overview of Project

### Purpose
The purpose of this project was to generate (lat,lng) locations to then narrow down these locations for a vacation search which eventually would turn into a vacation itinerary.
To do this we used citipy to get the nearest city to our randomly generated locations, then used our weather api key along with ```requests``` to extract relevant information about each location (city, country, max temp, humidity, cloudiness, wind speed, etc.). In addition, we generated figures using gmaps to place markers on our desired locations, along with routes to multiple locations like a typical travel itinerary would do.


## Results

Below is an example of what our figure looked like after filtering the dataframe to only include locations with a min temp above 70° F and below 90° F. Keep in mind, these are randomly generated points on a map and will look different each time when creating the initial database. 

![WeatherPy_vacation_map](https://github.com/brand0j/World_Weather_Analysis/blob/main/Vacation_Search/WeatherPy_vacation_map.PNG)

Next we would like to select multiple locations that are clustered somewhat close to one another to illustrate a possible travel itinerary. In this case I chose Australia since all the cities generated here meet our travel preferences while also belonging to the same country. Using the following code we can generate a route between travel destinations:

```
fig = gmaps.figure()
travel_destinations = gmaps.directions_layer(
                            start,end,
                            waypoints=[stop1,stop2,stop3],
                            travel_mode = 'DRIVING')
fig.add_layer(travel_destinations)
fig
```

![WeatherPy_travel_map](https://github.com/brand0j/World_Weather_Analysis/blob/main/Vacation_Itinerary/WeatherPy_travel_map.PNG)

Finally we can show lodging info along with the current weather at each of our travel destinations. I was trying to figure a way to reduce the size of the info box displayed on the map but was unable to find anything useful on [gmaps api documentation](https://jupyter-gmaps.readthedocs.io/en/latest/api.html) regarding this issue.

![WeatherPy_travel_map_markers](https://github.com/brand0j/World_Weather_Analysis/blob/main/Vacation_Itinerary/WeatherPy_travel_map_markers.png)

## Summary
One small inconvenience while working on this was that for some reason when I tried to ```pd.read_csv('filepath')``` it wasn't working properly which resulted in me having to deposit the corresponding .csv file into the same folder as the .ipynb file I was working in. This was an interesting project once the api's were set up along with the config.py file to import the api keys. In the future I would like to take the main concepts learned in this project and apply it to popular backpacking trips to help people find nearby lodging while hiking (an example would be the Appalachian Trail). 

