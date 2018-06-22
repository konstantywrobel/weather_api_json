# Weather Api JSON  

```
let lat;
let lon;
let api = 'https://fcc-weather-api.glitch.me/api/current?';
(function(){
            if (navigator.geolocation) {
                navigator.geolocation.getCurrentPosition(function (position) {
                    lat = 'lat=' + position.coords.latitude;
                    lon = 'lon=' + position.coords.longitude;
                    getWeather(lat, lon);
                    console.log( lat + lon );
                });
            }
    else {
        console.log('error');
    }
})();
function getWeather(lat, lon) {
    let urlString = api + lat + "&" + lon;
    fetch(urlString)
        .then(resp => resp.json())
.then(resp => {
   document.getElementById("city").textContent = (resp.name + ', ');
   document.getElementById("country").textContent = (resp.sys.country);
   document.getElementById("temp").textContent = (resp.main.temp + '℃');
   document.getElementById("desc").textContent = (resp.weather[0].main);
   document.getElementById("wind").textContent = ('Wind: ' + resp.wind.speed);
   document.getElementById("pressure").textContent = ('Pressure: ' + resp.main.pressure + ' hPa');
   document.getElementById("humidity").textContent = ('Humidity: ' + resp.main.humidity + '%');
});
};

```

## Example

[demo](https://www.konstantyw.pl/api-weather)
