# openWeather

NPM module written in JavaScript to get, treat and return weather datas from the OpenWeatherMap's API.

## Contents

1. [What is this project ?](#what_is_this_project)

2. [How to use it ?](#how_to_use_it)

    * [From locally...](#from_locally)

    * [From GitHub...](#from_github)

    * [From NPM...](#from_npm)

3. [Little examples](#little_examples)

4. [A few usefull links](#a_few_useful_links)

5. [Conclusion](#conclusion)

<a name="what_is_this_project"></a>
## What is this project ?

This project consists to develop an NPM module written in JavaScript to get, treat and return weather datas from OpenWeatherMap.

This NPM module is composed of 5 functions in total. They are presented right here:

* a function that returns all meteorological data for all cities with the country code of their respective countries. More specifically, this function will take as parameter an associative array, each element of which represents the identification of a city with the name of the latter as key and the code of the country where it is located as value. This function will then return a simple table containing the meteorological data for each city requested. The returned data will be structured into objects for each of the requested cities. Using the OpenWeather web service API, this function will also take your personal OpenWeather API key as a parameter.

* a function for converting the date and time for sunrise and sunset in various types of internationally recognized and used formats (timestamp - number of seconds elapsed since January 1, 1970 at midnight, DMY - day month year, MDY - month day year and YMD - year month day). All of this formats include the time as H:M:S. You can also get only the time as H:M:S. This function will therefore take as parameters the date and time in the form of a timestamp, the timezone corresponding to the city in the given country in the form of the number of seconds separating it from UTC (for coordinated universal time - the international reference of time elapsed) and the desired format for the time and date (timestamp for timestamp, DMYHMS for DMY, MDYHMS for MDY and YMDHMS for YMD). This function will then return a character string corresponding to the date and time in the desired format.

* a function of converting the atmospheric pressure between the different units of measurement that exist internationally (HectoPascal - hPa, Pascal - Pa, Bar - bar, Atmosphere - atm, Torr - torr and Pounds per square inch - psi) and taking into account cases where the requested pressure unit is the same as the current one or where the requested pressure unit simply does not exist.

* a function of converting temperatures between the different units of measurement that exist internationally (Celsius - ° C, Fahrenheit - ° F and Kelvin - K) and taking into account the cases where the requested temperature unit is the same as the current one or even where the requested temperature unit simply does not exist.

* a function internal to the module and making it possible to define the level of risk represented by the value of ultraviolet radiation passed as a parameter between all those defined internationally. This function will then return a string of characters corresponding to the level of ultraviolet risk represented.

Other functions can be added along the way to upgrade this NPM module to new features.

This NPM module is initially made to be used in computer programming and maker courses for the elements defined in the following list:

* introduction to the use and programming of APIs,

* introduction to the use of JSON format,

* initiation to the development of NodeJS modules,

* handling of NodeJS technology and initiation to development in this technology,

* algorithmic initialization and their coding,

* learning good programming practices,

* initiation to web requests and communication protocols.

<a name="how_to_use_it"></a>
## How to use it ?

There are 3 ways to use this NPM module. Here they are:

<a name="from_locally"></a>
### From locally...

First of all, create an empty folder whatever your location in the file system of your computer:
```bash
mkdir test
```
__Clarification:__ the empty folder created is named ```test``` and will be the case for the rest of the demonstration, however you can name it whatever you like.

Now, go to the newly created directory:
```bash
cd test
```
You have to clone the ```openWeather``` git repos on GitHub:
```bash
git clone https://github.com/Vicken-Ghoubiguian/openWeather
```
It's time to install the NPM module ```axios```:
```bash
npm install axios
```
Now it's time to create your JavaScript file and open it to then use the module ```openWeather```. To do so, create a file named ```index.js``` and open it:
```bash
touch index.js

nano index.js
```
__Clarification:__ the empty file created is named ```index.js``` and will be the case for the rest of the demonstration, however you can name it whatever you like.

In the newly created file ```index.js```, it is now time to import the module ```openWeather```. To do this, copy then paste the following line into the file ```index.js```:
```js
var openWeather = require('./openweather');
```
Now it's your turn to have fun. So...Get ready, get set and code.

<a name="from_github"></a>
### From GitHub...

First of all, create an empty folder whatever your location in the file system of your computer:
```bash
mkdir test
```
__Clarification:__ the empty folder created is named ```test``` and will be the case for the rest of the demonstration, however you can name it whatever you like.

Now, go to the newly created directory:
```bash
cd test
```
You have to install the NPM module ```openWeather``` from GitHub via NPM:
```bash
npm install https://github.com/Vicken-Ghoubiguian/openWeather
```
Now it's time to create your JavaScript file and open it to then use the module ```openWeather```. To do so, create a file named ```index.js``` and open it:
```bash
touch index.js

nano index.js
```
__Clarification:__ the empty file created is named ```index.js``` and will be the case for the rest of the demonstration, however you can name it whatever you like.

In the newly created file ```index.js```, it is now time to import the module ```openWeather```. To do this, copy then paste the following line into the file ```index.js```:
```js
var openWeather = require('@wicken/openweather');
```
Now it's your turn to have fun. So...Get ready, get set and code.

<a name="from_npm"></a>
### From NPM...

Coming soon...

<a name="little_examples"></a>
## Little examples

Below, there are 2 examples, one for each case (for a single location or many of them), to illustrate how to use this module in any NodeJS project.

For a single location:
```js
// import the 'openWeather' module...
var openWeather = require('@wicken/openweather');

// definition and configuration of the wished city and country as hashtable (in this example, we will take the french capital Paris' weather - the country code of France is 'FR')...
var weatherReferencesHashTable = new Object();
weatherReferencesHashTable["Paris"] = "FR";

// definition of the 'openWeatherAPIKey' variable which contain your current Openweather API key...
var openWeatherAPIKey = "Your OpenWeather API Key";

// Calling the 'getWeather' method from the 'openWeather' module...
openWeather.getWeather(weatherReferencesHashTable, openWeatherAPIKey).then(function(results) {

    // Display separator...
    console.log("==========================================");

    // Browse the array  returned by the 'getWeather' function and containing all wished results...
    for(i = 0; i < results.length; i++)
    {
        // In the case that the current element is a valable weather structure...
        if(results[0].cod === 200) {

            // Display all weather datas...
            console.log("City (country code): " + results[0].city + " (" + results[0].sys_country + ")");
            console.log("Geographic coordinates: (lat: " + results[0].latitude + ", lon: " + results[0].longitude + ")");
            console.log("Description: " + results[0].weather_description);
            console.log("Weather icon: " + results[0].weather_icon);
            console.log("Sunrise time: " + openWeather.dateAndTimeFormatConversionFunction(results[0].sys_sunrise, results[0].timezone));
            console.log("Sunset time: " + openWeather.dateAndTimeFormatConversionFunction(results[0].sys_sunset, results[0].timezone));
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
            console.log("==========================================");
    
        // In other cases...
        } else {

            // Display the error...
            console.log("Code: " + results[i].cod);
            console.log("Message: " + results[i].message);
            console.log("Server: " + results[i].server);
            console.log("Host: " + results[i].host);
            console.log("Protocol: " + results[i].protocol);
            console.log("Method: " + results[i].method);
            console.log("URL: " + results[i].url);
            console.log("Date: " + results[i].date);
            console.log("==========================================");
        }
    }

// Catching any possible errors...
}).catch(err => {

    // Display the error...
    console.error(err);
});
```
For several locations:
```js
// import the 'openWeather' module...
var openWeather = require('@wicken/openweather');

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

// definition of the 'openWeatherAPIKey' variable which contain your current Openweather API key...
var openWeatherAPIKey = "Your OpenWeather API Key";

// Calling the 'getWeather' method from the 'openWeather' module...
openWeather.getWeather(weatherReferencesHashTable, openWeatherAPIKey).then(function(results) {

    // Display separator...
    console.log("==========================================");

    // Browse the array  returned by the 'getWeather' function and containing all wished results...
    for(i = 0; i < results.length; i++)
    {
        // In the case that the current element is a valable weather structure...
        if(results[i].cod === 200) {

            // Display all weather datas...
            console.log("City (country code): " + results[i].city + " (" + results[i].sys_country + ")");
            console.log("Geographic coordinates: (lat: " + results[i].latitude + ", lon: " + results[i].longitude + ")");
            console.log("Description: " + results[i].weather_description);
            console.log("Weather icon: " + results[i].weather_icon);
            console.log("Sunrise time: " + openWeather.dateAndTimeFormatConversionFunction(results[i].sys_sunrise, results[i].timezone));
            console.log("Sunset time: " + openWeather.dateAndTimeFormatConversionFunction(results[i].sys_sunset, results[i].timezone));
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
            console.log("==========================================");

        // In other cases...
        } else {

            // Display the error...
            console.log("Code: " + results[i].cod);
            console.log("Message: " + results[i].message);
            console.log("Server: " + results[i].server);
            console.log("Host: " + results[i].host);
            console.log("Protocol: " + results[i].protocol);
            console.log("Method: " + results[i].method);
            console.log("URL: " + results[i].url);
            console.log("Date: " + results[i].date);
            console.log("==========================================");
        }
    }

// Catching any possible errors...
}).catch(err => {

    // Display the error...
    console.error(err);
});
```

<a name="a_few_useful_links"></a>
## A few usefull links

* [NodeJS official website](https://nodejs.org/en/),
* [NPM official website](https://www.npmjs.com/),
* [Creating NodeJS modules](https://docs.npmjs.com/creating-node-js-modules),
* [OpenWeather](https://openweathermap.org/),
* [OpenWeather API](https://openweathermap.org/api)

<a name="conclusion"></a>
## Conclusion

It has been an exciting project, easily usable by anyone in any other project written with NodeJS (therefore in Javascript language) regardless of its size (large or small) and which has broadened my knowledge in Javascript language and in NodeJS development as potentially every other beginner or confirmed developer.
