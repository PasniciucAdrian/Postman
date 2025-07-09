# 🌤️ GET - Weather by City Name

**Endpoint:**
```
GET https://api.openweathermap.org/data/2.5/weather?q={{city}}&appid={{apikey}}
```

**Description:**
Fetches current weather information for a specific city using the city name.

---

## ✅ Request

**Method:** GET  
**Query Parameters:**
- `q`: City name (e.g., Iasi)
- `appid`: Your API key stored as environment variable `{{apikey}}`

---

##  Test Scripts

```javascript
// ✅ Test 1: Check status code
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

// ✅ Test 2: Validate city name
pm.test("City name is present in response", function () {
    const jsonData = pm.response.json();
    pm.expect(jsonData.name).to.eql("Iasi");
});

// ✅ Test 3: Weather and temp validation
pm.test("Weather info and temperature are present", function () {
    const jsonData = pm.response.json();
    pm.expect(jsonData.weather).to.be.an("array").that.is.not.empty;
    pm.expect(jsonData.main.temp).to.be.a("number");
});
```

---

## 🧾 Sample Test Result

- ✅ Status code is 200  
- ✅ City name is "Iasi"  
- ✅ Temperature and weather description are present