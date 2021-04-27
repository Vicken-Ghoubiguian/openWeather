# openWeather

NPM module written in JavaScript to get, treat and return weather from OpenWeatherMap.

## Contents

1. [What is this project ?](#what_is_this_project)

2. [How to use it ?](#how_to_use_it)

3. [A little example](#a_little_example)

4. [A few usefull links](#a_useful_links)

5. [Conclusion](#conclusion)

<a name="what_is_this_project"></a>
## What is this project ?

<a name="how_to_use_it"></a>
## How to use it ?

<a name="a_little_example"></a>
## A little example

For a single location:
```js
// import the 'openWeather' module...
var openWeather = require('openWeather');

// definition and configuration of the wished city and country as hashtable (in this example, we will take the french capital Paris' weather - the country code of France is 'FR')...
var weatherReferencesHashTable = new Object();
weatherReferencesHashTable["Paris"] = "FR";

// Calling the 'getWeather' method from the 'openWeather' module 
openWeather.getWeather(weatherReferencesHashTable, openWeatherAPIKey).then(function(results) {

    //
    for(i = 0; i < results.length; i++)
    {
        // In the case that the current element is a valable weather structure...
        if(results[0].cod === 200) {

            //
            console.log("==========================================");
            console.log("City (country code): " + results[0].city + " (" + results[0].sys_country + ")");
            console.log("Geographic coordinates: (lat: " + results[0].latitude + ", lon: " + results[0].longitude + ")");
            console.log("Description: " + results[0].weather_description);
            console.log("Sunrise time (in timestamp): " + results[0].sys_sunrise);
            console.log("Sunset time (in timestamp): " + results[0].sys_sunset);
            console.log("Pressure: " + results[i].main_pressure);
            console.log("Temperature: " + results[0].main_temp + " Kelvin (K)");
            console.log("Maximum temperature: " + results[0].main_temp_max + " Kelvin (K)");
            console.log("Minimum temperature: " + results[0].main_temp_min + " Kelvin (K)");
            console.log("Feeling like temperature: " + results[0].main_feels_like + " Kelvin (K)");
            console.log("Clouds: " + results[0].clouds_all);
            console.log("Wind speed: " + results[0].wind_speed);
            console.log("Wind deg: " + results[0].wind_deg);
            console.log("Offset from UTC: " + results[0].timezone  + " seconds");
            console.log("Humidity: " + results[0].main_humidity + " %");
            console.log("UV index: " + results[0].uv_value);
            console.log("UV risk: " + results[0].uv_risk);
    
        // In other cases...
        } else {

            //
            console.log("==========================================");

        }
    }
}
```
For several locations:
```js
// import the 'openWeather' module...
var openWeather = require('openWeather');

//definition of wished cities and countries as hashtable
var weatherReferencesHashTable = new Object();

//configuration of the hashtable for the wished cities and countries for the following locations: 
weatherReferencesHashTable["Paris"] = "FR";
weatherReferencesHashTable["Osaka"] = "JP";
weatherReferencesHashTable["Kaesong"] = "KP";
weatherReferencesHashTable["Seoul"] = "KR";
weatherReferencesHashTable["Nauru"] = "NR";
weatherReferencesHashTable["Asmara"] = "ER";
weatherReferencesHashTable["Havana"] = "CU";

// Calling the 'getWeather' method from the 'openWeather' module 
openWeather.getWeather(weatherReferencesHashTable, openWeatherAPIKey).then(function(results) {

    //
    for(i = 0; i < results.length; i++)
    {
        // In the case that the current element is a valable weather structure...
        if(results[i].cod === 200) {

            //
            console.log("==========================================");
            console.log("City (country code): " + results[i].city + " (" + results[i].sys_country + ")");
            console.log("Geographic coordinates: (lat: " + results[i].latitude + ", lon: " + results[i].longitude + ")");
            console.log("Description: " + results[i].weather_description);
            console.log("Sunrise time (in timestamp): " + results[i].sys_sunrise);
            console.log("Sunset time (in timestamp): " + results[i].sys_sunset);
            console.log("Pressure: " + results[i].main_pressure);
            console.log("Temperature: " + results[i].main_temp + " Kelvin (K)");
            console.log("Maximum temperature: " + results[i].main_temp_max + " Kelvin (K)");
            console.log("Minimum temperature: " + results[i].main_temp_min + " Kelvin (K)");
            console.log("Feeling like temperature: " + results[i].main_feels_like + " Kelvin (K)");
            console.log("Clouds: " + results[i].clouds_all);
            console.log("Wind speed: " + results[i].wind_speed);
            console.log("Wind deg: " + results[i].wind_deg);
            console.log("Offset from UTC: " + results[i].timezone  + " seconds");
            console.log("Humidity: " + results[i].main_humidity + " %");
            console.log("UV index: " + results[i].uv_value);
            console.log("UV risk: " + results[i].uv_risk);
    
        // In other cases...
        } else {

            //
            console.log("==========================================");

        }
    }
}
```

<a name="a_useful_links"></a>
## A few usefull links

<a name="conclusion"></a>
## Conclusion

It has been an exciting project, easily usable by anyone in any other project written with NodeJS (therefore in Javascript language) regardless of its size (large or small) and which has broadened my knowledge in Javascript language and in NodeJS development as potentially every other beginner or confirmed developer.
