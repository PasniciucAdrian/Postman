# GET All Boards - Trello API

## 🧾 Summary
This request is used to retrieve all boards associated with a Trello account using valid `apiKey` and `apiToken`.

---

## ✅ Test Scripts

```javascript
//  Status code should be 200 (OK)
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

//  Response must be an array
pm.test("Response is an array", function () {
    pm.expect(pm.response.json()).to.be.an('array');
});

//  At least one board must be returned
pm.test("At least one board exists", function () {
    pm.expect(pm.response.json().length).to.be.above(0);
});

//  Check exact name of a known board
pm.test("Board name is correct", function () {
    let board = pm.response.json().find(b => b.name === "Postman 3 - Practica - Tema");
    pm.expect(board).to.not.be.undefined;
});

//  Save the ID and name of the board to environment
let targetBoard = pm.response.json().find(b => b.name === "Postman 3 - Practica - Tema");
if (targetBoard) {
    pm.environment.set("targetBoardId", targetBoard.id);
    pm.environment.set("targetBoardName", targetBoard.name);
    console.log("✅ Board name: " + targetBoard.name);
    console.log("✅ Board ID: " + targetBoard.id);
}
```

---

## 🧪 Test Results

When the board `"Postman 3 - Practica - Tema"` exists and is public/accessible:

```
✅ Board name: Postman 3 - Practica - Tema
✅ Board ID: 6666f0d734ad6daa1fd873f
```

These values were retrieved from the `GET` response and confirmed against the screenshot proof.

---

## 📷 Screenshot Proof

Located in:

```
/Postman-Trello/printscreen/Postman-3-Practica-Tema-Trello.png
```

The image shows the board `"Postman 3 - Practica - Tema"` with lists `"To Do"`, `"Doing"` and `"Done"` as displayed on Trello Web.

---

## 🔐 Auth Notes

- Requires a valid Trello `apiKey` and `apiToken`
- Request uses query parameters: `key={{apiKey}}` and `token={{apiToken}}`