# 🏭 GET - Air Pollution Data

**Endpoint:**
```
GET https://api.openweathermap.org/data/2.5/air_pollution?lat={{lat}}&lon={{lon}}&appid={{apikey}}
```

**Description:**
Retrieves air quality data for a specified location.

---

## ✅ Request

**Method:** GET  
**Query Parameters:**
- `lat`: Latitude (e.g., 48.85)
- `lon`: Longitude (e.g., 2.35)
- `appid`: Your API key

---

## 🧪 Test Scripts

```javascript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

pm.test("Validate AQI and pollutant data", function () {
    const jsonData = pm.response.json();
    pm.expect(jsonData.list[0].main.aqi).to.be.within(1, 5);
    pm.expect(jsonData.list[0].components.pm2_5).to.be.a("number");
    pm.expect(jsonData.list[0].components.co).to.be.a("number");
});
```

---

## 🧾 Sample Test Result

- ✅ AQI: 3  
- ✅ pm2_5: 11.2  
- ✅ CO: 245.6