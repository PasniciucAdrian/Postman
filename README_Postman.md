# PostmanWeather Project

This project demonstrates how to interact with the **OpenWeatherMap API** using Postman, by retrieving weather data for a specific city. It also includes validation scripts and API key protection using Postman environments.

---

## 🔧 API Endpoint

- **GET** request to:  
  `https://api.openweathermap.org/data/2.5/weather?q={{city}}&appid={{apikey}}`

- Example query used:  
  - `q=Iasi`  
  - `appid={{apikey}}`

Environment variables are used to avoid exposing sensitive information like the API key.

---

## 📦 What this project includes

### ✅ 1. Request: Get weather by city name

- A GET request that fetches current weather data for a specified city.
- API key is passed securely using a Postman environment variable `{{apikey}}`.

---

### ✅ 2. Test Scripts

The request includes the following **Postman test scripts**:

#### ✔️ Status Code Check

```javascript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```

#### ✔️ Validate City Name

```javascript
pm.test("City name is present in response", function () {
    let jsonData = pm.response.json();
    pm.expect(jsonData.name).to.eql("Iasi");
});
```

Ensures the city in the response matches the one requested.

#### ✔️ Weather and Temperature Check

```javascript
pm.test("Weather info and temperature are present", function () {
    let jsonData = pm.response.json();
    pm.expect(jsonData.weather).to.be.an("array").that.is.not.empty;
    pm.expect(jsonData.main.temp).to.be.a("number");
});
```

Verifies that key weather data (like description and temperature) is available and correct.

---

### ⚙️ 3. Pre-request Script

Before each request, the following script checks if the API key is set:

```javascript
if (!pm.variables.get("apikey")) {
    throw new Error("API key ({{apikey}}) is not set. Please define it in your environment variables.");
}
```

This prevents the request from being sent if the key is missing.

---

### 🛡️ Environment Variables

Make sure to define the following variables in your Postman Environment:

- `apikey`: Your OpenWeatherMap API key  
- `city`: The name of the city you want to test (e.g., Iasi)

---

### 📌 Purpose

This setup is part of a QA training and demonstrates:

- Using Postman for API testing  
- Writing test automation scripts in Postman  
- Keeping sensitive data secure with variables
