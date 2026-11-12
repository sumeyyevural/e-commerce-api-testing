# E-Commerce API Testing Project

## Project Overview
This project focuses on testing RESTful APIs in a simulated e-commerce environment using Postman.

The main objective is to verify API endpoints, HTTP methods, response status codes, and JSON response structures through automated test scripts.

## Tools & Technologies
- Postman
- REST API
- HTTP Methods (GET, POST, PUT, DELETE)
- JavaScript (Postman Tests)
- JSON

## API Base URL
https://dummyjson.com

## Test Scenarios
- Retrieve all products
- Retrieve product details
- Create a new product
- Update an existing product
- Delete a product
- Handle non-existing product requests

## Note
This project uses DummyJSON, a simulated API service. Create, update, and delete operations demonstrate API responses and do not represent persistent changes in a real database.

## 1. Get All Products

**Method:** GET

**Endpoint:** `/products`

**Full URL:** https://dummyjson.com/products

### Purpose
Retrieve the list of all available products.

### Request
- HTTP Method: GET
- Request Body: None
- Parameters: None

### Expected Response
- Status Code: 200 OK
- Content-Type: application/json
- Response Body: A JSON object containing a list of products.

### Test Cases
- Verify that the status code is 200.
- Verify that the response format is JSON.
- Verify that the products list is not empty.
- Verify that every product has a title.

### Response Structure

The API returns a JSON object containing the following fields:

| Field | Data Type | Description |
|---|---|---|
| products | Array | List of products |
| total | Number | Total number of products |
| skip | Number | Number of skipped products |
| limit | Number | Maximum number of products returned |

Each product object includes:
- id: Product identifier
- title: Product name
- price: Product price
- category: Product category
- description: Product description

## 2. Get Product Details

**Method:** GET

**Endpoint:** `/products/1`

**Full URL:** https://dummyjson.com/products/1

### Purpose
Retrieve detailed information about a specific product using its ID.

### Request
- HTTP Method: GET
- Request Body: None
- Path Parameter: `id = 1`

### Expected Response
- Status Code: 200 OK
- Content-Type: application/json
- Response Body: A JSON object containing the details of the requested product.

### Test Cases
- Verify that the status code is 200.
- Verify that the product ID is 1.
- Verify that the product has a title.
- Verify that the product price is greater than 0.
- Verify that the product has a category.

### Response Structure

The API returns a JSON object containing the following fields:

| Field | Data Type | Description |
|---|---|---|
| id | Number | Unique product identifier |
| title | String | Product name |
| price | Number | Product price |
| description | String | Product description |
| category | String | Product category |
| brand | String | Product brand |
| rating | Number | Product rating |
| stock | Number | Available stock quantity |
| thumbnail | String | Product image URL |

## 3. Create New Product

**Method:** POST

**Endpoint:** `/products/add`

**Full URL:** https://dummyjson.com/products/add

### Purpose
Simulate creating a new product by sending product information to the API.

### Request
- HTTP Method: POST
- Content-Type: application/json

**Request Body:**

```json
{
  "title": "Wireless Bluetooth Headphones",
  "price": 49.99,
  "description": "High quality wireless headphones",
  "category": "electronics"
}
```

### Expected Response
- Status Code: 201 Created
- Response Body: A JSON object containing the submitted product information and a generated product ID.

### Test Cases
- Verify that the status code is 201.
- Verify that the response contains a product ID.
- Verify that the product title is correct.
- Verify that the product price is correct.

### Note
DummyJSON simulates the product creation process. The new product is not permanently stored in a database.

## 4. Update Product

**Method:** PUT

**Endpoint:** `/products/1`

**Full URL:** https://dummyjson.com/products/1

### Purpose
Simulate updating an existing product by sending new product information to the API.

### Request
- HTTP Method: PUT
- Content-Type: application/json
- Path Parameter: `id = 1`

**Request Body:**

```json
{
  "title": "Updated Wireless Headphones",
  "price": 59.99
}
```

### Expected Response
- Status Code: 200 OK
- Response Body: A JSON object containing the updated product information.

### Test Cases
- Verify that the status code is 200.
- Verify that the product title is updated correctly.
- Verify that the product price is updated correctly.
- Verify that the product ID is 1.

### Note
DummyJSON simulates the update operation. Changes are not permanently stored in a database.

## 5. Delete Product

**Method:** DELETE

**Endpoint:** `/products/1`

**Full URL:** https://dummyjson.com/products/1

### Purpose
Simulate deleting an existing product using its ID.

### Request
- HTTP Method: DELETE
- Request Body: None
- Path Parameter: `id = 1`

### Expected Response
- Status Code: 200 OK
- Response Body: A JSON object containing deletion confirmation and a deletion timestamp.

### Test Cases
- Verify that the status code is 200.
- Verify that the `isDeleted` field is true.
- Verify that the `deletedOn` field exists.

### Note
DummyJSON simulates the deletion operation. The product is not permanently deleted from a real database.

## 6. Get Non-Existing Product

**Method:** GET

**Endpoint:** `/products/999999`

**Full URL:** https://dummyjson.com/products/999999

### Purpose
Test how the API handles requests for a product that does not exist.

### Request
- HTTP Method: GET
- Request Body: None
- Path Parameter: `id = 999999`

### Expected Response
- Status Code: 404 Not Found
- Response Body: A JSON object containing an error message.

### Test Cases
- Verify that the status code is 404.
- Verify that the error response contains a message.

### Note
This scenario tests the API's error-handling behavior when a requested product cannot be found.