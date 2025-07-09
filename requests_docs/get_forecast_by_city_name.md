# 📅 GET - 5-Day Forecast (3-hour intervals)

**Endpoint:**
```
GET https://api.openweathermap.org/data/2.5/forecast?q={{city}}&appid={{apikey}}
```

**Description:**
Returns weather forecast for the next 5 days, updated in 3-hour increments.

---

## ✅ Request

**Method:** GET  
**Query Parameters:**
- `q`: City name
- `appid`: Your API key

---

## 🧪 Test Scripts

```javascript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

pm.test("Forecast list is present and has entries", function () {
    const jsonData = pm.response.json();
    pm.expect(jsonData.list).to.be.an("array").that.is.not.empty;
});

pm.test("There is at least one forecast for 12:00 PM", function () {
    const jsonData = pm.response.json();
    const forecastAtNoon = jsonData.list.find(item => item.dt_txt.includes("12:00:00"));
    pm.expect(forecastAtNoon).to.not.be.undefined;
});

pm.test("City is correct", function () {
    const jsonData = pm.response.json();
    pm.expect(jsonData.city.name).to.eql("Iasi");
});
```

---

## 🧾 Sample Test Result

- ✅ Status 200  
- ✅ Noon forecast found  
- ✅ City = Iasi  
- ✅ Forecast array not empty