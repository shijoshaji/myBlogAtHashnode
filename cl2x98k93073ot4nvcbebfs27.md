## Create Angular weatherApp - Part 4

Welcome to final part of this series, hope you have completed [Part 3](https://shijoshaji.hashnode.dev/create-angular-weatherapp-part-3).
We have 2 pending things now, this will be the last part as development.

## Call the services created
Lets call the services we created in last part into our app.

We are making/calling the logic in the file `src\app\app.component.ts`,
we are importing the interface and service we created.

Add below code to the file:

```
import { Component, OnInit } from '@angular/core';
import { WeatherInterface } from './models/weatherAPI.models';
import { WeatherAPIService } from './services/weather-api.service';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css'],
})
export class AppComponent implements OnInit {
  constructor(private weatherService: WeatherAPIService) {}

  weatherData?: WeatherInterface;
  cityName: string = '';

  fetchData() {
    this.getWeather(this.cityName);
    this.cityName = '';
  }

  ngOnInit(): void {
    this.getWeatherByGeoLocation();
  }

  private getWeather(cityName: string) {
    this.weatherService.fetchWeatherData(cityName).subscribe({
      next: (response) => {
        this.weatherData = response;
      },
    });
  }

  private getWeatherByGeoLocation() {
    if (navigator.geolocation) {
      navigator.geolocation.getCurrentPosition((position) => {
        let long = position.coords.longitude;
        let lat = position.coords.latitude;
        this.weatherService.getlocation(lat, long).subscribe({
          next: (res) => {
            this.getWeather(res.city);
            this.cityName = '';
          },
        });
      });
    }
  }
}
```
In above code `fetchData()` method is called from front end when we type the city name in search box (will be doing this soon). On loading the page the method `getWeatherByGeoLocation()` calls to get latitude and longitude and converts the LAT & LONG to city name and calls the method `getWeather()`, this returns the data that we saw in RAPID API as we tested.
Now the response is in `weatherData` which will be used in our HTML file.

## Html component update
As we have configured the main part in fetching data, now its time to update our html file to show dynamic data rather than static data.

File `src\app\app.component.html` is updated with below code


```
<div class="search">
  <form #form="ngForm" (submit)="fetchData()">
    <input type="text" name="" id="" placeholder="Enter city to search" name="city" [(ngModel)]="cityName">

  </form>
</div>

<div class="container" *ngIf="weatherData">
  <div class="upper-data">
    <img src="../assets/hot.jpg" alt="" srcset="" *ngIf="(weatherData.main.temp -32 )*5/9  > 30">
    <img src="../assets/main.jpg" alt="" srcset="" *ngIf="(weatherData.main.temp -32 )*5/9  <= 30">
    <div class="weather-data">
      <div class="location">{{weatherData.name}}, {{weatherData.sys.country}}</div>
      <div class="temperature">{{(weatherData.main.temp -32 )*5/9 | number:'1.0-0'}} °C</div>
    </div>
  </div>
  <div class="lower-data">
    <div class="more-info-container">
      <div class="info-block">
        <div class="info-block-label">
          <img src="../assets/min.png" alt="" srcset="">
          <span>Min</span>
        </div>
        <div class="info-block-value">
          {{(weatherData.main.temp_min -32 )*5/9 | number:'1.0-0' }} °C
        </div>
      </div>

      <div class="info-block">
        <div class="info-block-label">
          <img src="../assets/max.png" alt="" srcset="">
          <span>Max</span>
        </div>
        <div class="info-block-value">
          {{(weatherData.main.temp_max -32 )*5/9 | number:'1.0-0' }} °C
        </div>
      </div>

      <div class="info-block">
        <div class="info-block-label">
          <img src="../assets/humidity.png" alt="" srcset="">
          <span>Humidity</span>
        </div>
        <div class="info-block-value">
          {{weatherData.main.humidity}} %
        </div>
      </div>

      <div class="info-block">
        <div class="info-block-label">
          <img src="../assets/wind.png" alt="" srcset="">
          <span>Wind</span>
        </div>
        <div class="info-block-value">
          {{weatherData.wind.speed}} km/hr
        </div>
      </div>
    </div>
  </div>

</div>
``` 

**Well done**,  now lets run the application and see if its working
```
ng serve  --open
```
this will open the browser automatically [http://localhost:4200/](http://localhost:4200/)
If all goes well you will see the below screenshot

I live in Bangalore, so based on my location I get this data.

![LowerTemp.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1652013037361/kVyFMUDwy.PNG align="left")

I am trying to search with Rajasthan, as you can see we get data.

![MaxTemp.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1652013049092/aYJ3j-uc5.PNG align="left")


> You can try any cities, not necessarily Indian cities. This API supports international Cities too

> That's it😇 You did great, Hope you have learned something :)


**Feel free to connect with me [Porfolio](https://shijoshaji.herokuapp.com/)**