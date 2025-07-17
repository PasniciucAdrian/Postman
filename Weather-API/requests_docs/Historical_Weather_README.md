# Historical Weather

This request retrieves past weather data for a city on a specific date using WeatherAPI.

**Endpoint:**  
`https://api.weatherapi.com/v1/history.json`

**Parameters:**
- `key`: Your API key (use environment variable `{{WeatherAPI}}`)
- `q`: The city name (e.g., `Iasi`)
- `dt`: The date in `YYYY-MM-DD` format (e.g., `2025-07-08`)

---

## 🧪 Postman Test Scripts

```javascript
const jsonData = pm.response.json();

// ✅ City name test with visible message
pm.test("📍 City: " + jsonData.location.name, function () {
    pm.expect(jsonData.location.name).to.eql("Iasi");
});

// ✅ Check and display weather info if forecast exists
if (jsonData.forecast && jsonData.forecast.forecastday && jsonData.forecast.forecastday.length > 0) {
    const dayData = jsonData.forecast.forecastday[0].day;

    const maxTemp = dayData.maxtemp_c;
    const minTemp = dayData.mintemp_c;
    const humidity = dayData.avghumidity;

    // ✅ Show temperature range
    pm.test(`🌡️ Max temp: ${maxTemp}°C | Min temp: ${minTemp}°C`, function () {
        pm.expect(maxTemp).to.be.a("number");
        pm.expect(minTemp).to.be.a("number");
    });

    // ✅ Show humidity
    pm.test(`💧 Humidity: ${humidity}%`, function () {
        pm.expect(humidity).to.be.within(0, 100);
    });
} else {
    pm.test("⚠️ No forecast data found", function () {
        pm.expect(false).to.be.true; // Force fail
    });
}
```

---

## ✅ Sample Test Results in Postman

```
PASS  📍 City: Iasi  
PASS  🌡️ Max temp: 36.9°C | Min temp: 20.6°C  
PASS  💧 Humidity: 37%  
```

---

> Note: Forecast data must exist for the provided historical date.
