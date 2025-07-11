
# Create New Board - Trello API (Postman Practice)

## 🔧 Request Type
**POST** `https://api.trello.com/1/boards/?name=Postman-Trello&key={{apiKey}}&token={{apiToken}}`

## 📋 Headers
None required for this request.

## 📦 Body
None – the board name is passed via URL parameters.

## ✅ Test Script

```javascript
// Check if the status code is 200
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

// Parse the response body
let jsonData = pm.response.json();

// Check that the board name is correct
pm.test("Board name is correct", function () {
    pm.expect(jsonData.name).to.eql("Postman-Trello");
});

// Log and test board ID presence
pm.test("Board ID is present", function () {
    pm.expect(jsonData.id).to.exist;
});

// Set variables for later use
pm.environment.set("boardId", jsonData.id);
pm.environment.set("boardName", jsonData.name);

// Display the name and ID in Test Results
console.log("Board name:", jsonData.name);
console.log("Board ID:", jsonData.id);

// Add custom message in test result
pm.test("Board created with correct name and ID", function () {
    console.log(`✅ Board "${jsonData.name}" created with ID: ${jsonData.id}`);
});
```

## 📈 Test Results (example)

```
PASS  Status code is 200
PASS  Board name is correct
PASS  Board ID is present
PASS  Board created with correct name and ID

✅ Board "Postman-Trello" created with ID: 64e1bc5f5c77be43b17a9472
```

## 🖼️ Screenshot Reference
Located in:  
`Postman/Postman-Trello/printscreen/Postman-Trello.png`

Preview shows the board with the exact title **Postman-Trello** in Trello workspace.
