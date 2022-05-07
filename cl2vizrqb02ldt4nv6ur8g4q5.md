## Create Angular weatherApp - Part 2

Welcome to this series, hope you have completed [Part 1](https://shijoshaji.hashnode.dev/create-angular-weatherapp-part-1)

## Remove code/files 
First thing first, lets open our **weatherApp ** is VS code / or any IDE.
Lets remove unwanted code which was generated from previous step


1. Go to this file and remove the entire content: `src\app\app.component.html`

1. Lets create a simple div in the file
```
<div>Weather App code</div>
```

1. Open VS code terminal and type this below command, you must be able to see you app still runs fine
```
ng serve --open
``` 

## Design CSS part of APP
Our app design will have 2 parts 

- Upper Data - Holds the city name and main temperature
- Lower Data - Holds additional data like humidity, wind etc

So lets design the CSS part first, go to file `src\styles.css` and add below code

```
/* ROOT */
:root {
  --blue-1: #3c429e;
  --blue-2: #4c52ad;
  --yellow-1: #fac742;
  --white: #fff;
  --grey-1: #ededed;
  --shadow-dark: rgba(0, 0, 0, 0.3);
  --shadow-light: rgba(255, 255, 255, 0.1);
}

* {
  margin: 0px;
  padding: 0px;
  box-sizing: border-box;
}

body {
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  font-size: 16px;
  width: 100%;
  height: 100vh;
  background-color: var(--blue-1);
  display: flex;
  justify-content: center;
  align-items: center;
}

.container {
  width: 400px;
  height: 90vh;
  background-color: var(--blue-2);
  border-radius: 20px;
  box-shadow: 20px 20px 20px var(--shadow-dark);
}

.upper-data {
  position: relative;
  overflow: hidden;
  width: 100%;
  height: 50%;
  border-top-left-radius: 20px;
  border-top-right-radius: 20px;
}

.upper-data img {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.lower-data {
  position: relative;
  overflow: hidden;
  width: 100%;
  height: 50%;
  border-bottom-left-radius: 20px;
  border-bottom-right-radius: 20px;
  padding: 0.7em;
  display: flex;
  flex-direction: column;
}

.weather-data {
  position: relative;
  z-index: 1;
  width: 100%;
  height: 100%;
  background-color: var(--shadow-dark);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  color: var(--white);
  text-align: center;
}

.location {
  font-size: 1.2em;
}

.temperature {
  font-size: 4em;
  font-weight: 900;
}

.more-info {
  color: var(--white);
}

.more-info-container {
  flex: 1;
  background-color: var(--shadow-light);
  border-bottom-left-radius: 20px;
  border-bottom-right-radius: 20px;
  margin-top: 1em;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}

.info-block {
  width: 50%;
  display: flex;
  flex-direction: row;
}

.info-block-label {
  width: 50%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.info-block-label img {
  width: 1.5em;
}

.info-block-label span {
  color: var(--white);
  font-size: 0.8em;
}

.info-block-value {
  width: 50%;
  display: flex;
  justify-content: flex-start;
  align-items: center;
  color: var(--white);
}

.search {
  margin-bottom: 1em;
  text-align: center;
}

.search input {
  background-color: var(--shadow-light);
  outline: none;
  border: none;
  border-radius: 20px;
  padding: 1em;
  color: var(--white);
  font-size: 0.8em;
  text-align: center;
}

::placeholder {
  /* Chrome, Firefox, Opera, Safari 10.1+ */
  color: var(--white);
  opacity: 1; /* Firefox */
}

``` 
## Add images to APP
Lets add images needed for the app in this folder `src\assets` you can get the images from [Github](https://github.com/shijoshaji/weatherApp/tree/main/src/assets)

## HTML part of APP

Will add our HTML part of the app in this file: `src\app\app.component.html`
Lets remove the content added earlier, and replace with this code for Upper Data

```
<div class="container">
  <div class="upper-data">
    <img src="../assets/hot.jpg" alt="" srcset="" *ngIf="14 > 15">
    <img src="../assets/main.jpg" alt="" srcset="" *ngIf="14 < 15">
    <div class="weather-data">
      <div class="location">Bangalore</div>
      <div class="temperature">{{14.55 | number:'1.0-0'}} °C</div>
    </div>
  </div>
  <div class="lower-data"></div>

</div>
``` 
Lets do the Lower Data part

```
<div class="lower-data">
    <div class="more-info-container">
      <div class="info-block">
        <div class="info-block-label">
          <img src="../assets/min.png" alt="" srcset="">
          <span>Min</span>
        </div>
        <div class="info-block-value">
          10 °C
        </div>
      </div>

      <div class="info-block">
        <div class="info-block-label">
          <img src="../assets/max.png" alt="" srcset="">
          <span>Max</span>
        </div>
        <div class="info-block-value">
          30 °C
        </div>
      </div>

      <div class="info-block">
        <div class="info-block-label">
          <img src="../assets/humidity.png" alt="" srcset="">
          <span>Humidity</span>
        </div>
        <div class="info-block-value">
          55 %
        </div>
      </div>

      <div class="info-block">
        <div class="info-block-label">
          <img src="../assets/wind.png" alt="" srcset="">
          <span>Wind</span>
        </div>
        <div class="info-block-value">
          16 km/hr
        </div>
      </div>
    </div>
  </div>
``` 

Now the final HTML file will look like this

```
<div class="container">
  <div class="upper-data">
    <img src="../assets/hot.jpg" alt="" srcset="" *ngIf="14 > 15">
    <img src="../assets/main.jpg" alt="" srcset="" *ngIf="14 < 15">
    <div class="weather-data">
      <div class="location">Bangalore</div>
      <div class="temperature">{{14.55 | number:'1.0-0'}} °C</div>
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
          10 °C
        </div>
      </div>

      <div class="info-block">
        <div class="info-block-label">
          <img src="../assets/max.png" alt="" srcset="">
          <span>Max</span>
        </div>
        <div class="info-block-value">
          30 °C
        </div>
      </div>

      <div class="info-block">
        <div class="info-block-label">
          <img src="../assets/humidity.png" alt="" srcset="">
          <span>Humidity</span>
        </div>
        <div class="info-block-value">
          55 %
        </div>
      </div>

      <div class="info-block">
        <div class="info-block-label">
          <img src="../assets/wind.png" alt="" srcset="">
          <span>Wind</span>
        </div>
        <div class="info-block-value">
          16 km/hr
        </div>
      </div>
    </div>
  </div>

</div>
``` 

Save the file and run the app using, to see how it looks
```
ng serve --open
```  

> That's it😇 You did good











