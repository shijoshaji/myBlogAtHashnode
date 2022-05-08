## Create Angular weatherApp - Part 3

Welcome to this series, hope you have completed [Part 2](https://shijoshaji.hashnode.dev/create-angular-weatherapp-part-2)

## Dynamic Data
In part 2 we created a html app with static values and data (I usually create this way to see first how I must expect data and design as such ). In this part 3 lets make it as more of Angular 😜 than plain html css, js.

Before working on Html part, what we need is dynamic data(based on geo location & search with city name) for that we need a API.

API that I have used are:
- [Rapid API weather](https://rapidapi.com/community/api/open-weather-map) -> get weather data
- [BigDataCloud](https://www.bigdatacloud.com/blog/convert-getcurrentposition-free-reversegeocoding-api) -> get city name with geo location
> **Note:** There are many API's out there you can make use of it, I just wanted to try with multiple API provider

## Rapid API Account
You got to sign up to Rapid API first to make use of the API's.

Lets go to [Rapid API weather](https://rapidapi.com/community/api/open-weather-map) the one I used and signup/login if already registered
Once login, go to the API and select the `Current Weather Data` end point and subscribe it to get API KEY.
Make sure to get all the info in header parameters as below screenshot as this will be used in our Environment file of our App (*my API KEY is blued out, Please use yours *)

![Capture.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1652009574214/pQlaif3u7.PNG align="left")

> Hope you have signed up, you can test the endpoint by mentioning the city name in 'q' in Required Parameter and click on Test Endpoint button, you will get the response with status code 200 if its success.
![Capture.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1652010072102/Q1wyjTvN8.PNG align="left")

Copy that sample response you got (you can choose my sample response from [here](https://github.com/shijoshaji/weatherApp/blob/main/src/app/services/sampleResponse.json)), we need that to create our Interface

## Create Interface from response
Created by exporting the json response from API and generated this interface using the [URL]( https://transform.tools/json-to-typescript) just paste you json (left side)and interface is generated (right side)

Copy that interface generate, lets create a folder 'models' in `src\app\` create a new file 'weatherAPI.models.ts' in models folder ie`src\app\models\weatherAPI.models.ts` paste the generated code in that file like this

```
/** NOTE:
 Created by exporting the json response from API and generated this interface using the below URL
 
 https://transform.tools/json-to-typescript
 */

export interface WeatherInterface {
  coord: Coord;
  weather: Weather[];
  base: string;
  main: Main;
  visibility: number;
  wind: Wind;
  clouds: Clouds;
  dt: number;
  sys: Sys;
  timezone: number;
  id: number;
  name: string;
  cod: number;
}

export interface Coord {
  lon: number;
  lat: number;
}

export interface Weather {
  id: number;
  main: string;
  description: string;
  icon: string;
}

export interface Main {
  temp: number;
  feelslike: number;
  temp_min: number;
  temp_max: number;
  pressure: number;
  humidity: number;
}

export interface Wind {
  speed: number;
  deg: number;
}

export interface Clouds {
  all: number;
}

export interface Sys {
  type: number;
  id: number;
  country: string;
  sunrise: number;
  sunset: number;
}

``` 

Great you have created interface of the Rapid API into our App.
Now lets work on the environment file as said earlier

## Environment file
Angular creates 2 environment files when we created our app using `ng new` 
Its in location `src\environments` we have two files one for test `src\environments\environment.ts` and other for prod `src\environments\environment.prod.ts`

Lets add below code to these files:

`src\environments\environment.ts`

```
export const environment = {
  production: false,
  baseURL: 'https://community-open-weather-map.p.rapidapi.com/weather',
  reverseGeoCodeURL:
    'https://api.bigdatacloud.net/data/reverse-geocode-client?',
  XRapidAPIHostName: 'X-RapidAPI-Host',
  XRapidAPIHostValue: 'community-open-weather-map.p.rapidapi.com',
  XRapidAPIKeyName: 'X-RapidAPI-Key',
  XRapidAPIKeyValue: 'YOUR API KEY VALUE HERE',
};
```
`src\environments\environment.prod.ts`

```
export const environment = {
  production: true,
  baseURL: 'https://community-open-weather-map.p.rapidapi.com/weather',
  reverseGeoCodeURL:
    'https://api.bigdatacloud.net/data/reverse-geocode-client?',
  XRapidAPIHostName: 'X-RapidAPI-Host',
  XRapidAPIHostValue: 'community-open-weather-map.p.rapidapi.com',
  XRapidAPIKeyName: 'X-RapidAPI-Key',
  XRapidAPIKeyValue: 'YOUR API KEY VALUE HERE',
};
```
Great, if you have noticed in code `reverseGeoCodeURL` this is from bigdatacloud api I have added, will explain on this when i create services to call these API's

## Create Service
This holds the logic on calling API we want to use, this has logic to call both the API

Use this cmd to create service
```
ng generate service services/weather-api
```
 Once created in file `src\app\services\weather-api.service.ts` lets add the below code

```
import { Injectable } from '@angular/core';
import { HttpClient, HttpHeaders, HttpParams } from '@angular/common/http';
import { environment } from '../../environments/environment';
import { WeatherInterface } from '../models/weatherAPI.models';
import { Observable } from 'rxjs';

@Injectable({
  providedIn: 'root',
})
export class WeatherAPIService {
  constructor(private http: HttpClient) {}

  fetchWeatherData(placeName: string): Observable<WeatherInterface> {
    return this.http.get<WeatherInterface>(environment.baseURL, {
      headers: new HttpHeaders()
        .set(environment.XRapidAPIHostName, environment.XRapidAPIHostValue)
        .set(environment.XRapidAPIKeyName, environment.XRapidAPIKeyValue),
      params: new HttpParams()
        .set('q', placeName)
        .set('units', 'imperial')
        .set('mode', 'json'),
    });
  }

  getlocation(lat: any, long: any) {
    var geoAPI = `${environment.reverseGeoCodeURL}latitude=${lat}&longitude=${long}&localityLanguage=en`;

    return this.http.get<any>(geoAPI);
  }
}
```
This above code has 2 method where `fetchWeatherData` returns the data based on city name we pass from front end ie it calls the RAPID API
`getlocation` returns the city name based on the geo location we pass 

These logic are getting called from file `src\app\app.component.ts` we are to create the logic.

> That's it😇 You did good

*Recap: *
- Created API accounts
- Updated the required info in environment file
- Created Services



