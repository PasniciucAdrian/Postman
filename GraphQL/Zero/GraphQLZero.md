
# 🧪 Postman – GraphQL User CRUD Example (Create, Update, Delete)

This Postman collection demonstrates how to perform **Create**, **Update**, and **Delete** operations using **GraphQL** at the endpoint [https://graphqlzero.almansi.me/](https://graphqlzero.almansi.me/). The screenshots for each step are also included for reference.

---

## 1. ✅ Create a User

This mutation allows you to create a new user with a name, username, and email address.

📷 Screenshot: [Create User Body](./CreateUserBody.png)

###  Request Body (JSON)
```json
{
  "query": "mutation CreateUser($input: CreateUserInput!) { createUser(input: $input) { id name username email } }",
  "variables": {
    "input": {
      "name": "Adrian",
      "username": "Adrian.graphql",
      "email": "adrianTest@gmail.com@gmail.com"
    }
  }
}
```

###  Test Script
```javascript
let jsonData = pm.response.json();
let user = jsonData.data.createUser;

//  Save to environment for future requests
pm.environment.set("new_user_id", user.id);
pm.environment.set("new_user_name", user.name);

// Show only ID and name in Test Results
pm.test("Created User Info", function () {
    console.log(`User ID: ${user.id}`);
    console.log(`User Name: ${user.name}`);

    // Display in Test Results tab
    pm.expect(user).to.have.property("id");
    pm.expect(user).to.have.property("name");

    pm.test(`✅ ID: ${user.id}`, function () {
        pm.expect(user.id).to.be.a("string");
    });

    pm.test(`✅ Name: ${user.name}`, function () {
        pm.expect(user.name).to.be.a("string");
    });
});
```

---

## 2.  Update User

This mutation updates the name of the user created earlier, using variables stored in the environment.

📷 Screenshot: [Update User Body](./UpdateUserBody.png)

###  Pre-request Script
```javascript
let id = pm.environment.get("new_user_id");
let name = pm.environment.get("new_user_name");
let query = `
mutation {
  updateUser(id: "${id}", input: { name: "Updated ${name}" }) {
    id
    name
  }
}
`;

pm.variables.set("update_query", query);
```

###  Request Body (JSON)
```json
{
  "query": "mutation { updateUser(id: \"{{new_user_id}}\", input: { name: \"Updated {{new_user_name}}\" }) { id name } }"
}
```

###  Test Script
```javascript
let jsonData = pm.response.json();
let updatedUser = jsonData.data.updateUser;

// ✅ Save updated name to env
pm.environment.set("updated_user_name", updatedUser.name);

// 🟡 Old name from Create step
let oldName = pm.environment.get("new_user_name");

// ✅ Test results
pm.test(`🟡 Old Name: ${oldName}`, function () {
    pm.expect(oldName).to.be.a("string");
});

pm.test(`🟢 New Name: ${updatedUser.name}`, function () {
    pm.expect(updatedUser.name).to.be.a("string");
    pm.expect(updatedUser.name).to.include("Updated");
});

// 🆔 Check ID from previous step (create)
pm.test(`🆔 ID still exists (from create): ${pm.environment.get("new_user_id")}`, function () {
    pm.expect(pm.environment.get("new_user_id")).to.be.a("string");
});
```

---

## 3.  Delete User

This mutation deletes the user using the `id` stored in the environment.

📷 Screenshot: [Delete User Body](./DeleteUserBody.png)

###  Request Body (JSON)
```json
{
  "query": "mutation DeleteUser($id: ID!) { deleteUser(id: $id) }",
  "variables": {
    "id": "{{updated_user_id}}"
  }
}
```

###  Test Script
```javascript
let jsonData = pm.response.json();

// 🟡 ID from environment
let deletedUserId = pm.environment.get("new_user_id");

// ✅ Confirm deleted ID
pm.test(`🆔 Deleted User ID (from env): ${deletedUserId}`, function () {
    pm.expect(deletedUserId).to.be.a("string");
});

// ✅ Success message
pm.test("✅ User deleted successfully", function () {
    pm.expect(jsonData.data).to.have.property("deleteUser");
});

// ✅ Clear environment
pm.environment.unset("new_user_id");
pm.environment.unset("new_user_name");
pm.environment.unset("updated_user_id");
pm.environment.unset("updated_user_name");
```

---

✅ **You're ready to test** all user operations via GraphQL in Postman. Make sure your environment is active and your variables are correctly set before moving to the next step.
