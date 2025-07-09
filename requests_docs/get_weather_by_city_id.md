# 🌍 GET - Weather by City ID

**Endpoint:**
```
GET https://api.openweathermap.org/data/2.5/weather?id={{cityid}}&appid={{apikey}}
```

**Description:**
Fetches weather information for a specific city using its city ID.

---

## ✅ Request

**Method:** GET  
**Query Parameters:**
- `id`: City ID (e.g., 2988507 for Paris)
- `appid`: Your API key

---

##  Test Scripts

```javascript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

pm.test("City name is Paris", function () {
    pm.response.to.be.withBody;
    pm.response.to.be.json;
    const jsonData = pm.response.json();
    pm.expect(jsonData.name).to.eql("Paris");
});

pm.test("Weather data and coordinates are valid", function () {
    const jsonData = pm.response.json();
    pm.expect(jsonData.weather).to.be.an("array").that.is.not.empty;
    pm.expect(jsonData.main.temp).to.be.a("number");
    pm.expect(jsonData.coord.lat).to.be.closeTo(48.85, 0.5);
    pm.expect(jsonData.coord.lon).to.be.closeTo(2.35, 0.5);
});
```

---

## 🧾 Sample Test Result

- ✅ Status 200  
- ✅ Paris recognized  
- ✅ Coordinates within acceptable range