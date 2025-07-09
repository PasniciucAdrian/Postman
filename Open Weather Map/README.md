# 🌦️ PostmanWeather Project

This project demonstrates how to interact with the **OpenWeatherMap API** using **Postman**. It covers several endpoints using the free plan and applies test automation to ensure API functionality and data correctness.

---

## 🔧 API Endpoints Used

1. **Current Weather by City Name**  
   `https://api.openweathermap.org/data/2.5/weather?q={{city}}&appid={{apikey}}`

2. **Current Weather by City ID**  
   `https://api.openweathermap.org/data/2.5/weather?id={{cityid}}&appid={{apikey}}`

3. **Air Pollution Data**  
   `https://api.openweathermap.org/data/2.5/air_pollution?lat={{lat}}&lon={{lon}}&appid={{apikey}}`

4. **5-Day Forecast (3-hour intervals)**  
   `https://api.openweathermap.org/data/2.5/forecast?q={{city}}&appid={{apikey}}`

---

##  Included Requests

### ✅ 1. Weather by City Name
- Fetches current weather using a city name (e.g., `Iasi`).
- Validates:
  - Status 200
  - Correct city name
  - Temperature and weather data presence

### ✅ 2. Weather by City ID
- Example with `Paris` (city ID: 2988507).
- Validates:
  - Status 200
  - JSON structure
  - Accurate coordinates
  - Logs raw response (for debugging)

### ✅ 3. Air Pollution Data
- Example for coordinates of Paris.
- Validates:
  - AQI (Air Quality Index) is between 1 and 5
  - `pm2_5` and `CO` values are numbers
  - Coordinates are accurate

### ✅ 4. 5-Day Forecast
- Forecasted weather data in 3-hour intervals for `Iasi`.
- Validates:
  - Forecast list is not empty
  - Includes a `12:00 PM` entry
  - City is correct
  - Temperature is valid
  - Logs raw JSON for debugging

---

##  Test Automation

All requests include **Postman Test Scripts** that:
- Validate response status codes
- Parse JSON bodies
- Compare returned data with expected values
- Check weather data structure
- Output response for troubleshooting

---

##  Environment Variables

To use this collection, configure the following variables in your **Postman Environment**:

| Variable | Description |
|----------|-------------|
| `apikey` | Your OpenWeatherMap API key (hidden for security) |
| `city`   | City name for weather requests (e.g., `iasi`) |
| `cityid` | OpenWeatherMap City ID (e.g., `2988507` for Paris) |
| `lat`    | Latitude (e.g., `48.85` for Paris) |
| `lon`    | Longitude (e.g., `2.35` for Paris) |

---

##  Purpose

This collection was created as part of a **QA training exercise** to:
- Practice API testing
- Use Postman efficiently
- Automate validations
- Protect sensitive data via environment variables

---
