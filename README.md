# 🌩️Python Weather API Challenge:partly_sunny:

![equatorsign](https://user-images.githubusercontent.com/91695375/139562767-fa1b31b4-e106-489e-b4b7-d5d32542a5db.png)


# Python API Homework - What's the Weather Like?

# Background
>Whether financial, political, or social -- data's true power lies in its ability to answer questions definitively. So let's take what you've learned about Python requests, APIs, and JSON traversals to answer a fundamental question: "What's the weather like as we approach the equator?"
Now, we know what you may be thinking: "Duh. It gets hotter..."
But, if pressed, how would you prove it?
>

# Part I - WeatherPy
>In this example, you'll be creating a Python script to visualize the weather of 500+ cities across the world of varying distance from the equator. To accomplish this, you'll be utilizing a simple Python library, the OpenWeatherMap API, and a little common sense to create a representative model of weather across world cities.
The first requirement is to create a series of scatter plots to showcase the following relationships:
>

>
- Temperature (F) vs. Latitude

![image](https://user-images.githubusercontent.com/91695375/139562655-9533a28f-26dd-4075-9f98-c24718b938f5.png)
>
- Humidity (%) vs. Latitude


![image](https://user-images.githubusercontent.com/91695375/139562679-c0ab1648-3211-42f1-80e4-056b2e54f74d.png)
>
- Cloudiness (%) vs. Latitude


![image](https://user-images.githubusercontent.com/91695375/139562687-316fc966-c4b2-4e84-858a-37a64fcb770d.png)
>
- Wind Speed (mph) vs. Latitude


![image](https://user-images.githubusercontent.com/91695375/139562691-4da656ff-4e7d-4c81-8b59-8123ba28f965.png)

>
After each plot, add a sentence or two explaining what the code is analyzing.
The second requirement is to run linear regression on each relationship. This time, separate the plots into Northern Hemisphere (greater than or equal to 0 degrees latitude) and Southern Hemisphere (less than 0 degrees latitude):

After each pair of plots, take the time to explain what the linear regression is modeling. For example, describe any relationships you notice and any other analysis you may have.
>
>
- Northern Hemisphere - Temperature (F) vs. Latitude
  - R-square value is: -0.77, which shows strong negative correlation between Lat & Max Temperature 🌡️
- Southern Hemisphere - Temperature (F) vs. Latitude
  - R-square value is: 0.38, which shows a moderately positive correlation between Lat & Max Temperature 🌡️
- Northern Hemisphere - Humidity (%) vs. Latitude
  - R-square value is: 0.22, which shows a weak positive correlation between Lat & Humidity 🌧️💧
- Southern Hemisphere - Humidity (%) vs. Latitude
  - R-square value is: 0.09, which shows a very weak positive correlation between Lat & Humidity 🌧️💧
- Northern Hemisphere - Cloudiness (%) vs. Latitude
  - R-square value is: 0.23, which shows a moderately positive correlation between Lat & Cloudiness ☁️
- Southern Hemisphere - Cloudiness (%) vs. Latitude
  - R-square value is: 0.07, which shows a very weak positive correlation between Lat & Cloudiness ☁️
- Northern Hemisphere - Wind Speed (mph) vs. Latitude
  - R-square value is: 0.19, which shows a weak positive correlation between Lat & Wind Speed 🌬️
- Southern Hemisphere - Wind Speed (mph) vs. Latitude
  - R-square value is: 0.13, which shows a weak positive correlation between Lat & Wind Speed 🌬️
>
>
Randomly select at least 500 unique (non-repeat) cities based on latitude and longitude.
Perform a weather check on each of the cities using a series of successive API calls.
Include a print log of each city as it's being processed with the city number and city name.
```
Lower quartile of Humidity is: 65.0
Upper quartile of Humidity is: 88.0
Interquartile range of Humidity is: 23.0
Humidity Median: 78.0 
Values below 30.5 are possibly outliers
Values above 122.5 are possibly outliers
```


# Part II - VacationPy
Now let's use your skills in working with weather data to plan future vacations. Use jupyter-gmaps and the Google Places API for this part of the assignment.

Create a heat map that displays the humidity for every city from Part I.
```
#Pulling in Gmaps/generate heat map

fig = gmaps.figure(center=(22.0, -1.0), zoom_level = 2)
heat_layer = gmaps.heatmap_layer(locations, weights = weight, 
                                 dissipating = False, max_intensity = np.max(weight),
                                 point_radius = 4)
fig.add_layer(heat_layer)
fig
```
![map(2)](https://user-images.githubusercontent.com/91695375/139562831-225d86b1-0c0d-4ea7-9a5e-cd597e59bd8d.png)


Narrow down the DataFrame to find your ideal weather condition. For example:
A max temperature lower than 80 degrees but higher than 70.
Wind speed less than 10 mph.
Zero cloudiness.

Using Google Places API to find the first hotel for each city located within 5000 meters of your coordinates.

Plot the hotels on top of the humidity heatmap with each pin containing the Hotel Name, City, and Country.
```
filtered_cities = cities_new_df.loc[(cities_new_df["Max Temp"] <= 80) & 
                                    (cities_new_df["Max Temp"] >= 70) & 
                                    (cities_new_df["Wind Speed"] < 10) &  
                                    (cities_new_df["Cloudiness"] == 0)]
                                
filtered_cities
```
<img width="728" alt="Screen Shot 2021-10-30 at 9 20 44 PM" src="https://user-images.githubusercontent.com/91695375/139562890-edfe60a1-c783-4d51-a19c-fbdebadee53c.png">

![map(1)](https://user-images.githubusercontent.com/91695375/139562815-570a6825-016a-47b9-8c24-29b4029bb4f9.png)

😎 *Who's coming with me to Tenerife?!* 🌞
