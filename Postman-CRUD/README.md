\# Postman-CRUD



This project demonstrates how to perform CRUD operations (Create, Read, Update, Delete) using Postman and a REST API endpoint available at:  

Test PHP API endpoint: [https://qachallenge.ro/api/test_api.php](https://qachallenge.ro/api/test_api.php)



Each operation is configured as a request in the `Postman-CRUD` collection.



\## Requests Overview



\### 1. Read All Users

Sends a `GET` request to retrieve all users from the database.



\*\*URL:\*\*

```

https://qachallenge.ro/api/test\_api.php?action=fetch\_all

```



\*\*Screenshot:\*\*

!\[Read All Users](../printscreen/ReadAllUsers.png)



---



\### 2. Read a Single User

Sends a `GET` request using a specific `id` to fetch a single user's details.



\*\*URL:\*\*

```

https://qachallenge.ro/api/test\_api.php?action=fetch\_single\&id=USER\_ID

```



\*\*Screenshot (Postman):\*\*

!\[ReadAnUserTR](../printscreen/ReadAnUserTR.png)



\*\*Screenshot (PHP logic):\*\*

!\[ReadAnUserPHP](../printscreen/UpdateUserPHP.png)



---



\### 3. Insert User

Sends a `POST` request to insert a new user into the database.



\*\*Body:\*\*

\- `action`: insert  

\- `first\_name`: user's first name  

\- `last\_name`: user's last name  



\*\*Screenshot (Postman):\*\*

!\[InsertUserTR](../printscreen/InserUserTR.png)



\*\*Screenshot (PHP logic):\*\*

!\[InsertUserPHP](../printscreen/InserUserPHP.png)



---



\### 4. Update User

Sends a `POST` request to update an existing user's information.



\*\*Body:\*\*

\- `action`: update  

\- `id`: user's ID  

\- `first\_name`: new first name  

\- `last\_name`: new last name  



\*\*Screenshot (Postman):\*\*

!\[UpdateUserTR](../printscreen/UpdateUserTR.png)



\*\*Screenshot (PHP logic):\*\*

!\[UpdateUserPHP](../printscreen/UpdateUserPHP.png)



---



\### 5. Delete User

Sends a `POST` request to delete a user by ID.



\*\*Body:\*\*

\- `action`: delete  

\- `id`: user's ID  



\*\*Screenshot (Postman):\*\*

!\[DeleteUserTR](../printscreen/DeleteUserTR.png)



\*\*Screenshot (PHP logic):\*\*

!\[DeleteUserPHP](../printscreen/DeleteUserPHP.png)



---



\## Tools Used



\- \*\*Postman\*\* for testing API requests  

\- \*\*PHP \& MySQL\*\* for back-end REST API functionality



\*\*Overview Diagram:\*\*

!\[Overview](printscreen/PHP Mysl REST API CRUD.png)



