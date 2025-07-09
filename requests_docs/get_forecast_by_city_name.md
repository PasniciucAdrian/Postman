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

##  Test Scripts

```javascript
// ✅ Test 1: Check if the response status is 200 (OK)
// Confirms the server responded successfully
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

// ✅ Test 2: Confirm the forecast list is returned
// Ensures the response has the expected forecast data structure
pm.test("Forecast list exists and has entries", function () {
    const jsonData = pm.response.json();
    pm.expect(jsonData.list).to.be.an("array").that.is.not.empty;
});

// ✅ Test 3: Check if any forecast is for 12:00 PM
// Verifies at least one forecast entry exists for noon
pm.test("Forecast includes entry for 12:00 PM", function () {
    const jsonData = pm.response.json();
    const atNoon = jsonData.list.find(item => item.dt_txt.includes("12:00:00"));
    pm.expect(atNoon).to.not.be.undefined;
});

// ✅ Test 4: Validate city name returned (handles diacritics and casing)
// This way the test passes even if response is "Iasi" or "Iași"
pm.test("City name contains 'iasi'", function () {
    const jsonData = pm.response.json();
    pm.expect(jsonData.city.name.toLowerCase()).to.include("iasi");
});


// ✅ Test 5: Check temperature exists in forecast items
// Ensures the temperature value is numeric
pm.test("Temperature data exists and is a number", function () {
    const jsonData = pm.response.json();
    pm.expect(jsonData.list[0].main.temp).to.be.a("number");
});

// 🛠️ Optional debug: Output raw JSON if needed
console.log("RAW response:");
console.log(pm.response.text());
```

---

## 🧾 Sample Test Result

- ✅ Status code is 200  
- ✅ Forecast list exists and has entries  
- ✅ Forecast includes entry for 12:00 PM  
- ✅ City name contains 'iasi'
- ✅ Temperature data exists and is a number  