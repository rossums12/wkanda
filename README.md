# KWantera Stock Sample Application 
This Node application is comprised into two sections /client and /server.  The client side contains the charting logic and the server side collects data located under the /data direcotry and provides access to them via a three different webapi get requests
 It requests data from its server component and displays stock market close data in a HighChart as shown below: 
![image not loaded](http://i.imgur.com/1t4msJN.png)
Each section of the application contains instructions in the readme to make getting started simple. 

## Features
* This project Utitlizes <b>Angular 2</b> built with <b>Typescript</b>.  
* The application was building us <b>Mongo</b>.  If you want to connect the application to your own mongoDB, adjust the URL variable under /server/server.js.   I have it pointing to my local DB on my network. 
```javascript
var URL = 'mongodb://172.16.0.9:27017/stocks';
```
* right click to zoom onto any date range to view a more detailed view. 
Highcharts has <b>interactive x-axis zooming</b> built in by passing the object a zoom type
```javascript
chart: { 
   type: 'line',
   zoomType: 'x' 
},
```
![image not loaded](http://i.imgur.com/qjLYO5Z.png)
* toggle the various series by clicking on the legends 
HighCharts does not include any regression on averages in its charting library, you need to use the stock charts for that type of funcitonality.    We can manually <b>calculate the moving average</b> and add it to the charting surface as a seperate series. 
```javascript
calculateMovingAverage(arr,currentIndex){
   var movingAverage = this.movingAverage,
       currentVal = 0,
       lowerBound = currentIndex - movingAverage;
            
    while ( lowerBound < currentIndex ) {
       currentVal = currentVal +  arr[lowerBound];
       lowerBound++;
    }
    currentVal = currentVal / movingAverage ;       
    return currentVal ; 
}
```
![image not loaded](http://i.imgur.com/USeudAE.png)
* the HighCharts line chart has native support for <b>interactive toggling</b> between the various stocks.   Click on the series in the legend to show or hide the various series. 

## Dependencies, Third Party libs, Notes 
* [NodeJS](https://nodejs.org/en/)
* [Angular 2](https://angular.io/) 
* [HighCharts](http://www.highcharts.com/) 
* [Express](http://expressjs.com/) 


Additionally, this project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 1.0.0-rc.1.
