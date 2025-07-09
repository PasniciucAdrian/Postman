# Astronomy Data for a Specific Date

This request retrieves astronomical data (sunrise, sunset, and moon phase) for a specific date using WeatherAPI.

**Endpoint:**  
`https://api.weatherapi.com/v1/astronomy.json`

**Parameters:**
- `key`: Your API key (use environment variable `{{WeatherAPI}}`)
- `q`: The city name (e.g., `Iasi`)
- `dt`: The date in `YYYY-MM-DD` format (e.g., `2025-07-09`)

---

## 🧪 Postman Test Scripts

```javascript
// ✅ Check status code
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

// ✅ Extract astronomy data
var astro = pm.response.json().astronomy.astro;

// ✅ Test that sunrise exists and show it
pm.test("🌅 Sunrise: " + astro.sunrise, function () {
    pm.expect(typeof astro.sunrise).to.eql("string");
});

// ✅ Test that sunset exists and show it
pm.test("🌇 Sunset: " + astro.sunset, function () {
    pm.expect(typeof astro.sunset).to.eql("string");
});

// ✅ Test that moon phase exists and show it
pm.test("🌕 Moon phase: " + astro.moon_phase, function () {
    pm.expect(typeof astro.moon_phase).to.eql("string");
});
```

---

## ✅ Sample Test Results in Postman

```
PASS  Status code is 200  
PASS  🌅 Sunrise: 05:24 AM  
PASS  🌇 Sunset: 09:06 PM  
PASS  🌕 Moon phase: Waxing Gibbous  
```

---

> Make sure your API key is active and valid for date-specific astronomy queries.
