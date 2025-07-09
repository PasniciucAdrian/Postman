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

##  Test Scripts

```javascript
// ✅ Make sure the request was successful
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

// ✅ Ensure 'list' array exists and contains at least one element
pm.test("List array is present and not empty", function () {
    const jsonData = pm.response.json();
    pm.expect(jsonData.list).to.be.an("array").that.is.not.empty;
});

// ✅ Check Air Quality Index is within expected range (1 to 5)
pm.test("AQI is between 1 and 5", function () {
    const jsonData = pm.response.json();
    const aqi = jsonData.list[0].main.aqi;
    pm.expect(aqi).to.be.within(1, 5);
});

// ✅ Check PM2.5 and CO are numbers
pm.test("PM2.5 and CO are valid numbers", function () {
    const jsonData = pm.response.json();
    const components = jsonData.list[0].components;
    pm.expect(components.pm2_5).to.be.a("number");
    pm.expect(components.co).to.be.a("number");
});

// ✅ Confirm returned coordinates match the ones requested (within a margin)
pm.test("Coordinates are close to expected values", function () {
    const jsonData = pm.response.json();
    pm.expect(jsonData.coord.lat).to.be.closeTo(48.85, 0.1);
    pm.expect(jsonData.coord.lon).to.be.closeTo(2.35, 0.1);
});

```

---

## 🧾 Sample Test Result

- ✅ Status code is 200
- ✅ List array is present and not empty 
- ✅ AQI is between 1 and 5  
- ✅ PM2.5 and CO are valid numbers
- ✅ Coordinates are close to expected values