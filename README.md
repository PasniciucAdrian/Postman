\# PostmanWeather Project



This project demonstrates how to interact with the \*\*OpenWeatherMap API\*\* using Postman, by retrieving weather data for a specific city. It also includes validation scripts and API key protection using Postman environments.



\## 🔧 API Endpoint



\- \*\*GET\*\* request to:  

&nbsp; `https://api.openweathermap.org/data/2.5/weather?q={{city}}\&appid={{apikey}}`



\- Example query used:  

&nbsp; `q=Iasi`  

&nbsp; `appid={{apikey}}`



Environment variables are used to avoid exposing sensitive information like the API key.



---



\## 📦 What this project includes



\### ✅ 1. Request: Get weather by city name

\- A GET request that fetches current weather data for a specified city.

\- API key is passed securely using a Postman environment variable `{{apikey}}`.



---



\## 🧪 2. Test Scripts



The request includes the following \*\*Postman test scripts\*\*:



\### ✔️ Status Code Check

```javascript

pm.test("Status code is 200", function () {

&nbsp;   pm.response.to.have.status(200);

});



