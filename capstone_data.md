# CAPSTONE PROJECT : LONDON vs PARIS

## Once upon a time...

Among the best cities to visit in Europe, Paris and London are two historical cities that are well rated. It is sure that, we don't have the same criteria to state how much we like a city over an other. The reasons can be very diverse from one person to another. Something is certain, if not ,let's make it an assumption, What   people may like in a city is about how they can enjoy themselves there : food, drink, art, culture, park, nightlife and so on... 
To put in a nutshell, people may be interested in the type of activities they can have. One can relevantly wonders if London and Paris meet this expectation. We will not discuss demography data in this project.


Furthermore,as far as tourism is concerned, weather is also an important subject. The impact of weather on tourism may depends on various parameters such as precipitation, sun, temperature, most common day condition. We must also take into account that, the weather preference can differ with the kinds of activities that a tourist may pursue. Y
ou know what? Nevermind! To make it simple and less theoretical, Let's just assume that a blue sky is most appreciated than a grey one.
A most spread idea is that London has a very bad weather and it rains pretty much there. 
Anyway, for people who want to enjoy outdoors under the sun, this might not be a positive intel. Is it only a 'cliché'?

## What are we going to discuss ?

The main problem we will discuss is whether Paris is so different of London. 
We are going to argue how similar and dissimilar London and Paris are.

## To whom it may concern

The topic may interest anyone particularly prospective tourists who want know the two cities and decide where to go for holidays for instance.

## Itinerary

To achieve our goal, our work will consist in two big parts. Firstly, we are going to explore both cities in order to discover the kind of attractions/stuffs one can enjoy in London and Paris. Then we are going to analyze and compare the weather is both cities.



## Data of the project

The data we will need for this project are:
  * list of stuffs/places/attraction of interest in both cities: We are going to leverage on the Foursquare API to get the information we need. It is very important that for each place we get the category that we can aggregate on.
  * Historical weather data for last year: We will need for each day in 2018, the temperature,precipitation amount, presence of sun and the global day condition. We will use the worldweatheronline API to get our data.

So we are going to use, two API mentioned above.
  
### Foursquare API

The API will be used here to get list of venues within a radius of 1Km around our cities. The sample of the response is a JSON that 
looks like 
the following :
```
{
  "meta": {
    "code": 200,
    "requestId": "5ac51d7e6a607143d811cecb"
  },
  "response": {
    "venues": [
      {
        "id": "5642aef9498e51025cf4a7a5",
        "name": "Mr. Purple",
        "location": {
          "address": "180 Orchard St",
          "crossStreet": "btwn Houston & Stanton St",
          "lat": 40.72173744277209,
          "lng": -73.98800687282996,
          "labeledLatLngs": [
            {
              "label": "display",
              "lat": 40.72173744277209,
              "lng": -73.98800687282996
            }
          ],
          "distance": 8,
          "postalCode": "10002",
          "cc": "US",
          "city": "New York",
          "state": "NY",
          "country": "United States",
          "formattedAddress": [
            "180 Orchard St (btwn Houston & Stanton St)",
            "New York, NY 10002",
            "United States"
          ]
        },
        "categories": [
          {
            "id": "4bf58dd8d48988d1d5941735",
            "name": "Hotel Bar",
            "pluralName": "Hotel Bars",
            "shortName": "Hotel Bar",
            "icon": {
              "prefix": "https://ss3.4sqi.net/img/categories_v2/travel/hotel_bar_",
              "suffix": ".png"
            },
            "primary": true
          }
        ],
        "venuePage": {
          "id": "150747252"
        }
      }
    ]
  }
}
```
We could simply use the category selected but to make it simple to aggregate with less detailed category, we will get the category
in the prefix. For instance from ``` "prefix": "https://ss3.4sqi.net/img/categories_v2/travel/hotel_bar_" ```, we will extract 
```travel ```

### World Weather Online API

orld Weather Online offers Weather Data and API for Businesses and Developers. 
Historical Weather is available as one off download or via our API by using a variety of search queries to receive 
historical weather data. The data will be received in a JSON which :

  * date for which the weather is forecasted,
  * location specific sunrise and sunset in the local time,
  * day max and min temperature in °C (Celsius) and °F (Fahrenheit),
  * hourly temperature in °C (Celsius) and °F (Fahrenheit),
  * wind speed in mph (miles per hour), knots, metre per sec and kmph (kilometre per hour),
  * 6-Point compass wind direction,
  * a unique weather condition code,
  * weather description text,
  * weather symbol image URL,
  * precipitation in millimetre (mm) and inches,
  * humidity in percentage (%),
  * visibility in kilometre (km) and miles,
  * pressure in millibar (mb) and inches,
  * cloud cover in percentage (%).
  
Here is a sample of the JSON returned:
```
{'date': '2018-01-01',
 'astronomy': [{'sunrise': '08:06 AM',
   'sunset': '04:02 PM',
   'moonrise': '03:48 PM',
   'moonset': '07:00 AM',
   'moon_phase': 'Waxing Gibbous',
   'moon_illumination': '97'}],
 'maxtempC': '8',
 'maxtempF': '46',
 'mintempC': '6',
 'mintempF': '43',
 'avgtempC': '7',
 'avgtempF': '44',
 'totalSnow_cm': '0.0',
 'sunHour': '6.8',
 'uvIndex': '3',
 'hourly': [{'time': '24',
   'tempC': '8',
   'tempF': '46',
   'windspeedMiles': '12',
   'windspeedKmph': '19',
   'winddirDegree': '250',
   'winddir16Point': 'WSW',
   'weatherCode': '113',
   'weatherIconUrl': [{'value': 'http://cdn.worldweatheronline.net/images/wsymbols01_png_64/wsymbol_0001_sunny.png'}],
   'weatherDesc': [{'value': 'Sunny'}],
   'precipMM': '0.4',
   'precipInches': '0.0',
   'humidity': '71',
   'visibility': '10',
   'visibilityMiles': '6',
   'pressure': '998',
   'pressureInches': '30',
   'cloudcover': '32',
   'HeatIndexC': '7',
   'HeatIndexF': '45',
   'DewPointC': '2',
   'DewPointF': '36',
   'WindChillC': '4',
   'WindChillF': '39',
   'WindGustMiles': '18',
   'WindGustKmph': '29',
   'FeelsLikeC': '4',
   'FeelsLikeF': '39',
   'uvIndex': '3'}]}

```

As a matter of fact, we cannot say immediately what is the day condition. We have only the ```weatherCode```. SO we will use another file 
to get the description of each weathercode.
```
WeatherCode	Condition	DayIcon	NightIcon
395	Moderate or heavy snow in area with thunder	wsymbol_0012_heavy_snow_showers	wsymbol_0028_heavy_snow_showers_night
392	Patchy light snow in area with thunder	wsymbol_0016_thundery_showers	wsymbol_0032_thundery_showers_night
389	Moderate or heavy rain in area with thunder	wsymbol_0024_thunderstorms	wsymbol_0040_thunderstorms_night
386	Patchy light rain in area with thunder	wsymbol_0016_thundery_showers	wsymbol_0032_thundery_showers_night
377	Moderate or heavy showers of ice pellets	wsymbol_0021_cloudy_with_sleet	wsymbol_0037_cloudy_with_sleet_night
374	Light showers of ice pellets	wsymbol_0013_sleet_showers	wsymbol_0029_sleet_showers_night
371	Moderate or heavy snow showers	wsymbol_0012_heavy_snow_showers	wsymbol_0028_heavy_snow_showers_night
368	Light snow showers	wsymbol_0011_light_snow_showers	wsymbol_0027_light_snow_showers_night
365	Moderate or heavy sleet showers	wsymbol_0013_sleet_showers	wsymbol_0029_sleet_showers_night
362	Light sleet showers	wsymbol_0013_sleet_showers	wsymbol_0029_sleet_showers_night
359	Torrential rain shower	wsymbol_0018_cloudy_with_heavy_rain	wsymbol_0034_cloudy_with_heavy_rain_night
356	Moderate or heavy rain shower	wsymbol_0010_heavy_rain_showers	wsymbol_0026_heavy_rain_showers_night
353	Light rain shower	wsymbol_0009_light_rain_showers	wsymbol_0025_light_rain_showers_night
350	Ice pellets	wsymbol_0021_cloudy_with_sleet	wsymbol_0037_cloudy_with_sleet_night
338	Heavy snow	wsymbol_0020_cloudy_with_heavy_snow	wsymbol_0036_cloudy_with_heavy_snow_night
335	Patchy heavy snow	wsymbol_0012_heavy_snow_showers	wsymbol_0028_heavy_snow_showers_night
332	Moderate snow	wsymbol_0020_cloudy_with_heavy_snow	wsymbol_0036_cloudy_with_heavy_snow_night
329	Patchy moderate snow	wsymbol_0020_cloudy_with_heavy_snow	wsymbol_0036_cloudy_with_heavy_snow_night
326	Light snow	wsymbol_0011_light_snow_showers	wsymbol_0027_light_snow_showers_night
323	Patchy light snow	wsymbol_0011_light_snow_showers	wsymbol_0027_light_snow_showers_night
320	Moderate or heavy sleet	wsymbol_0019_cloudy_with_light_snow	wsymbol_0035_cloudy_with_light_snow_night
317	Light sleet	wsymbol_0021_cloudy_with_sleet	wsymbol_0037_cloudy_with_sleet_night
314	Moderate or Heavy freezing rain	wsymbol_0021_cloudy_with_sleet	wsymbol_0037_cloudy_with_sleet_night
311	Light freezing rain	wsymbol_0021_cloudy_with_sleet	wsymbol_0037_cloudy_with_sleet_night
308	Heavy rain	wsymbol_0018_cloudy_with_heavy_rain	wsymbol_0034_cloudy_with_heavy_rain_night
305	Heavy rain at times	wsymbol_0010_heavy_rain_showers	wsymbol_0026_heavy_rain_showers_night
302	Moderate rain	wsymbol_0018_cloudy_with_heavy_rain	wsymbol_0034_cloudy_with_heavy_rain_night
299	Moderate rain at times	wsymbol_0010_heavy_rain_showers	wsymbol_0026_heavy_rain_showers_night
296	Light rain	wsymbol_0017_cloudy_with_light_rain	wsymbol_0025_light_rain_showers_night
293	Patchy light rain	wsymbol_0017_cloudy_with_light_rain	wsymbol_0033_cloudy_with_light_rain_night
284	Heavy freezing drizzle	wsymbol_0021_cloudy_with_sleet	wsymbol_0037_cloudy_with_sleet_night
281	Freezing drizzle	wsymbol_0021_cloudy_with_sleet	wsymbol_0037_cloudy_with_sleet_night
266	Light drizzle	wsymbol_0017_cloudy_with_light_rain	wsymbol_0033_cloudy_with_light_rain_night
263	Patchy light drizzle	wsymbol_0009_light_rain_showers	wsymbol_0025_light_rain_showers_night
260	Freezing fog	wsymbol_0007_fog	wsymbol_0007_fog
248	Fog	wsymbol_0007_fog	wsymbol_0007_fog
230	Blizzard	wsymbol_0020_cloudy_with_heavy_snow	wsymbol_0036_cloudy_with_heavy_snow_night
227	Blowing snow	wsymbol_0019_cloudy_with_light_snow	wsymbol_0035_cloudy_with_light_snow_night
200	Thundery outbreaks in nearby	wsymbol_0016_thundery_showers	wsymbol_0032_thundery_showers_night
185	Patchy freezing drizzle nearby	wsymbol_0021_cloudy_with_sleet	wsymbol_0037_cloudy_with_sleet_night
182	Patchy sleet nearby	wsymbol_0021_cloudy_with_sleet	wsymbol_0037_cloudy_with_sleet_night
179	Patchy snow nearby	wsymbol_0013_sleet_showers	wsymbol_0029_sleet_showers_night
176	Patchy rain nearby	wsymbol_0009_light_rain_showers	wsymbol_0025_light_rain_showers_night
143	Mist	wsymbol_0006_mist	wsymbol_0006_mist
122	Overcast	wsymbol_0004_black_low_cloud	wsymbol_0004_black_low_cloud
119	Cloudy	wsymbol_0003_white_cloud	wsymbol_0004_black_low_cloud
116	Partly Cloudy	wsymbol_0002_sunny_intervals	wsymbol_0008_clear_sky_night
113	Clear/Sunny	wsymbol_0001_sunny	wsymbol_0008_clear_sky_night
```
As there a two many day conditions, we are going to cluster them into five categories: SUNNY, CLOUDY, RAINY, FOGGY,SNOWY
