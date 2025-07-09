# Weather by City Name

This request fetches the current weather data for a specific city using its name.

**Endpoint:**  
`https://api.weatherapi.com/v1/current.json`

**Parameters:**
- `key`: Your API key (use environment variable `{{WeatherAPI}}`)
- `q`: The city name (e.g., `Iasi`)

---

## 🧪 Postman Test Scripts

```javascript
// ✅ Test that the status code is 200
// Verifies that the server responded successfully.
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

// ✅ Test that the city is correct
// Checks if the API returned data for the city "Iasi".
pm.test("Correct city is returned", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.location.name).to.eql("Iasi");
});

// ✅ Show the current temperature as a test message
var currentTemp = pm.response.json().current.temp_c;
pm.test("🌡️ Current temperature in Iasi: " + currentTemp + " °C", function () {
    pm.expect(typeof currentTemp).to.eql("number");
});

// ✅ Log the temperature in the Postman console
// Sends the temperature to Postman's internal console for review/debugging.
console.log("🌡️ Current temperature in Iasi is: " + currentTemp + " °C");

// ✅ Optional: check that it's not freezing 🧊
// Validates that the temperature is above 0°C.
pm.test("It's above freezing", function () {
    pm.expect(currentTemp).to.be.above(0);
});
```

---

## ✅ Sample Test Results in Postman

```
PASS  Status code is 200
PASS  Correct city is returned
PASS  🌡️ Current temperature in Iasi: 27.3 °C
PASS  It's above freezing
```

---

> Uses WeatherAPI.com data – works with valid API key and city.
