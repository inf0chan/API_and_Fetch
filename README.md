# API_and_Fetch

# Topics Covered

* What is an API?
* Client & Server
* HTTP Request & Response
* JSON
* HTTP Methods
* Status Codes
* REST APIs
* Fetch API
* Sending Data
* Error Handling
* Authentication
* Express.js Basics

---

# What is an API?

An **API (Application Programming Interface)** helps two applications communicate and share data.

For example:

* A weather app gets weather data from a weather server.
* A shopping app gets product details from its server.

---

# Restaurant Example

Think of an API like a waiter in a restaurant.

 * **Client** → Customer placing an order.
 * **Server** → Kitchen preparing the food.
 * **API** → Waiter carrying the order between them.

Flow:

> **Client → API → Server → API → Client**

---

# Client & Server

### Client

The application that requests data.

Examples:

* Web browser
* Mobile app

### Server

The application that stores and sends data.

> The **client always starts the request**, and the **server sends back a response**.

---

# HTTP Request

A request is sent from the client to the server.

It contains:

* **Method** → What action to perform.
* **URL** → Where to send the request.
* **Headers** → Extra information.
* **Body** → Data being sent (for POST, PUT, PATCH).

Example:

```javascript id="9ztcxq"
POST /users

Body:
{
  "name": "Deepesh"
}
```

---

# HTTP Response

The server replies with a response.

It contains:

* Status Code
* Headers
* Data (Body)

Always check the **status code** to know if the request was successful.

---

# What is JSON?

**JSON (JavaScript Object Notation)** is the most common format for sending data between a client and a server.

Example:

```json id="30fmbx"
{
  "name": "Rahul",
  "age": 20
}
```

---

# Convert JSON

Convert JSON into a JavaScript object:

```javascript id="ggz8l7"
const data = await response.json();
```

Convert a JavaScript object into JSON:

```javascript id="tz4rkw"
JSON.stringify(user);
```

---

# HTTP Methods

| Method     | Purpose                 |
| ---------- | ----------------------- |
| **GET**    | Get data                |
| **POST**   | Create new data         |
| **PUT**    | Replace existing data   |
| **PATCH**  | Update part of the data |
| **DELETE** | Delete data             |

---

# GET vs POST

### GET

* Reads data
* Sends information through the URL

Example:

```text
/users?id=10
```

---

### POST

* Sends data to the server
* Data is stored inside the request body

---

# Common HTTP Status Codes

## Success (2xx)

* **200** → OK
* **201** → Created
* **204** → No Content

---

## Client Errors (4xx)

* **400** → Bad Request
* **401** → Unauthorized
* **403** → Forbidden
* **404** → Not Found
* **429** → Too Many Requests

---

## Server Errors (5xx)

* **500** → Internal Server Error

---

# REST API URLs

REST APIs use simple URLs.

Examples:

```text
GET    /users
POST   /users
PATCH  /users/1
DELETE /users/1
```

---

# Fetch API

The **Fetch API** is used to request data from a server.

Using `.then()`:

```javascript id="56pj80"
fetch(url)
  .then(res => res.json())
  .then(data => console.log(data));
```

Using `async/await`:

```javascript id="3xpg4m"
async function getData() {
  const res = await fetch(url);
  const data = await res.json();

  console.log(data);
}
```

---

# Why Use `await` Twice?

```javascript id="52xv7t"
const res = await fetch(url);
const data = await res.json();
```

* First `await` waits for the server response.
* Second `await` waits while JSON is converted into a JavaScript object.

---

# Sending Data with Fetch

```javascript id="wnx4gw"
fetch(url, {
  method: "POST",

  headers: {
    "Content-Type": "application/json"
  },

  body: JSON.stringify(data)
});
```

Remember:

* Set the request method.
* Add the `Content-Type`.
* Convert objects using `JSON.stringify()`.

---

# Error Handling

`fetch()` doesn't automatically throw an error for **404** or **500**.

Always check:

```javascript id="uv1k5v"
if (!response.ok) {
  throw new Error("Request Failed");
}
```

---

# Authentication

Authentication helps identify who is making the request.

### API Key

A unique key used to identify an application.

### Bearer Token

A secure token sent after a user logs in.

Example:

```text
Authorization: Bearer your_token_here
```

### Security Tips

* Store secret keys in a `.env` file.
* Never upload API keys to GitHub.
* Don't expose secret keys in frontend code.

---

# Express.js Basics

**Express.js** is a Node.js framework used to build APIs.

### GET Route

```javascript id="vj0sq2"
app.get("/users", (req, res) => {
  res.json(users);
});
```

### POST Route

```javascript id="p98ttm"
app.post("/users", (req, res) => {
  res.status(201).json(newUser);
});
```

Send a response:

```javascript id="o4ykzu"
res.status(200).json(data);
```

---

# 🐭 PokeAPI Example

**PokeAPI** is a free API for learning.

```javascript id="q8qv7j"
fetch("https://pokeapi.co/api/v2/pokemon/pikachu")
  .then(res => res.json())
  .then(data => console.log(data));
```

It returns information like:

* Pokémon name
* Height
* Weight
* Abilities
* Types

---

# Quick Revision

* APIs allow applications to communicate.
* The **client** sends requests, and the **server** sends responses.
* Every request has a **method**, **URL**, **headers**, and sometimes a **body**.
* Responses include a **status code** and **data**.
* JSON is the standard format for sharing data.
* **GET** reads data.
* **POST** creates data.
* **PUT** replaces data.
* **PATCH** updates data.
* **DELETE** removes data.
* `fetch()` is used to communicate with APIs.
* `response.json()` converts JSON into a JavaScript object.
* Always check `response.ok` for errors.
* Keep API keys safe in a `.env` file.
* Express.js makes it easier to build APIs.
