\# 🌦️ Weather API – Postman Collection



This project contains a \*\*Postman collection\*\* for testing the most relevant and useful endpoints provided by \[WeatherAPI](https://www.weatherapi.com/). The collection is designed to demonstrate real-world weather queries with dynamic testing using Postman scripts.



\## ✅ Covered Endpoints



The following GET requests are included:



1\. \*\*Weather by city name\*\*

&nbsp;  - Retrieves current weather by city.

&nbsp;  - ✔️ Tests:

&nbsp;    - Status code is 200

&nbsp;    - City is correct (`Iasi`)

&nbsp;    - Temperature is shown in the results (ex: `🌡️ 27.3 °C`)

&nbsp;    - Temperature is above freezing



2\. \*\*Astronomy data for a specific date\*\*

&nbsp;  - Retrieves data such as sunrise, sunset and moon phase.

&nbsp;  - ✔️ Tests:

&nbsp;    - Sunrise time (ex: `🌅 05:24 AM`)

&nbsp;    - Sunset time (ex: `🌇 09:06 PM`)

&nbsp;    - Moon phase (ex: `🌕 Waxing Gibbous`)



3\. \*\*Historical Weather\*\*

&nbsp;  - Displays weather conditions for a past date.

&nbsp;  - ✔️ Tests:

&nbsp;    - City name is displayed (`📍 Iasi`)

&nbsp;    - Max and Min temperature are logged (ex: `🌡️ Max: 36.9°C | Min: 20.6°C`)

&nbsp;    - Humidity level is shown (ex: `💧 Humidity: 37%`)



4\. \*\*Weather Alerts by city\*\*

&nbsp;  - Fetches alerts for severe weather conditions.

&nbsp;  - ✔️ Tests:

&nbsp;    - City name is displayed

&nbsp;    - If no alert, displays message: `✅ No alerts for Iasi`



\## 🧪 Postman Testing Strategy



Each test uses `pm.test()` and logs key information in the \*\*Postman Console\*\* and the \*\*Test Results\*\* tab. Data validation includes:



\- Status code

\- Location match

\- Numeric type assertions

\- Threshold checks (temperature > 0°C)

\- Conditional alerts (humidity, moon phase, etc.)



\## 🔐 Security



The API key is stored in a \*\*Postman environment variable\*\* (`{{WeatherAPI}}`) and not exposed in any request URL.



---







