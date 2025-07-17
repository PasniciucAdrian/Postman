
# 📌 PHP & MySQL REST API CRUD

This project demonstrates how to perform basic CRUD operations using a RESTful API created in PHP with a MySQL database. The API is tested using Postman.

---

## 🔗 API Endpoint

Base URL:
```
https://qachallenge.ro/api/test_api.php
```

Each request uses a query parameter `action` to determine the operation to perform.

---

## 📥 GET: Read All Users

**Request:**
```
https://qachallenge.ro/api/test_api.php?action=fetch_all
```

**Result:**
Returns a list of all users in JSON format.

- 🔹 **[ReadAllUsers.png](../printscreen/ReadAllUsers.png)**

---

## 📥 GET: Read an User

**Request:**
```
https://qachallenge.ro/api/test_api.php?action=fetch_single&id=USER_ID
```

**Result:**
Returns the user with the given ID.

- 🔹 **[ReadAnUserTR.png](../printscreen/ReadAnUserTR.png)**

---

## 📤 POST: Insert User

**Request:**
```
https://qachallenge.ro/api/test_api.php?action=insert
```

**Body (form-data):**
- first_name
- last_name

**Result:**
Returns a success indicator.

- 🔹 **[InserUserTR.png](../printscreen/InserUserTR.png)**
- 🔹 **[InserUserPHP.png](../printscreen/InserUserPHP.png)**

---

## 🛠 POST: Update User

**Request:**
```
https://qachallenge.ro/api/test_api.php?action=update
```

**Body (form-data):**
- id
- first_name
- last_name

**Result:**
Returns a success indicator.

- 🔹 **[UpdateUserTR.png](../printscreen/UpdateUserTR.png)**
- 🔹 **[UpdateUserPHP.png](../printscreen/UpdateUserPHP.png)**

---

## ❌ GET: Delete User

**Request:**
```
https://qachallenge.ro/api/test_api.php?action=delete&id=USER_ID
```

**Result:**
Returns a success indicator.

- 🔹 **[DeleteUserTR.png](../printscreen/DeleteUserTR.png)**
- 🔹 **[DeleteUserPHP.png](../printscreen/DeleteUserPHP.png)**

---

## 🧩 Overview Diagram

- 🔹 **[PHPMyslRESTAPICRUD.png](../printscreen/PHPMyslRESTAPICRUD.png)**

---

## 🛠 Tools Used

- **Postman** for testing API requests  
- **PHP & MySQL** for back-end REST API functionality
