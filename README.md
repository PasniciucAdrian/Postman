\# 🌦️ Postman API Testing Collection



This repository contains organized Postman collections for testing two different weather APIs. It is intended as a practical reference for \*\*manual testers\*\* who are exploring API responses, validating key data fields, and logging critical outputs in Postman.



---



\## 📁 Folder Structure



\### 📂 Open Weather Map



This folder contains test requests and documentation for the \[OpenWeatherMap](https://openweathermap.org/api) API.  

It includes tests for:



\- \*\*Weather by city name\*\*

\- \*\*Weather by city ID\*\*

\- \*\*Air pollution data\*\*

\- \*\*5-day hourly forecast\*\*



Each request is saved as a `.json` collection, and there's a separate `requests\_docs` folder with individual `README.md` files that explain the tests and responses.



---



\### 📂 Weather API



This folder uses the \[WeatherAPI](https://www.weatherapi.com/) service. It includes:



\#### ✅ Tested Requests:



1\. \*\*Weather by city name\*\* – current weather and temperature check

2\. \*\*Astronomy data for a specific date\*\* – sunrise, sunset, moon phase

3\. \*\*Historical weather\*\* – past temperature and humidity

4\. \*\*Weather alerts by city\*\* – current alerts, if any



The collection includes:

\- `Weather API.postman\_collection.json`: importable collection

\- `requests\_docs/`: markdown files with detailed test scripts and expected responses for each request



---



\##  Who is this for?



This project is ideal for \*\*manual testers\*\* or \*\*QA analysts\*\* who:



\- Want to learn how to write and validate Postman tests

\- Need to extract and log specific values (temperature, alerts, etc.)

\- Are looking to practice API test planning and scripting

\- Prefer descriptive test result output (not just "PASS", but values like "🌡️ Temp: 26.3 °C")



---



\##  How to use this project



1\. Clone the repo locally  

2\. Open Postman and import any `.postman\_collection.json` file  

3\. Use the `requests\_docs/\*.md` files to understand what each request does  

4\. Run the full collection or individual requests  

5\. Review Test Results and Postman Console logs for clarity



---







