# Weather Alerts by City

This request checks for any active weather alerts for a specified city using WeatherAPI.

**Endpoint:**  
`https://api.weatherapi.com/v1/alerts.json`

**Parameters:**
- `key`: Your API key (use environment variable `{{WeatherAPI}}`)
- `q`: The city name (e.g., `Iasi`)

---

## 🧪 Postman Test Scripts

```javascript
const jsonData = pm.response.json();

// ✅ Test city name
pm.test("📍 City: " + jsonData.location.name, function () {
    pm.expect(jsonData.location.name).to.eql("Iasi");
});

// ✅ Check if there are any alerts
if (jsonData.alerts && jsonData.alerts.alert && jsonData.alerts.alert.length > 0) {
    const alert = jsonData.alerts.alert[0]; // Show only the first alert

    // ✅ Display alert headline and severity
    pm.test(`⚠️ Alert: ${alert.headline}`, function () {
        pm.expect(alert.headline).to.be.a("string");
    });

    pm.test(`📛 Severity: ${alert.severity}`, function () {
        pm.expect(alert.severity).to.be.a("string");
    });

    // ✅ Optional: show effective date
    pm.test(`🕒 Effective from: ${alert.effective}`, function () {
        pm.expect(alert.effective).to.be.a("string");
    });
} else {
    // ✅ No active alerts
    pm.test("✅ No weather alerts for Iasi", function () {
        pm.expect(true).to.be.true;
    });
}
```

---

## ✅ Sample Test Results in Postman

```
PASS  📍 City: Iasi  
PASS  ✅ No weather alerts for Iasi  
```

*or if an alert exists:*

```
PASS  📍 City: Iasi  
PASS  ⚠️ Alert: Extreme Heat Warning  
PASS  📛 Severity: Severe  
PASS  🕒 Effective from: 2025-07-10T12:00:00+03:00  
```

---

> Use this endpoint to monitor current weather warnings issued by official sources.
