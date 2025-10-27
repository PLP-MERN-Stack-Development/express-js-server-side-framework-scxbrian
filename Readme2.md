📁 Project Structure
express-js-server-side-framework-scxbrian/
├── server.js
├── package.json
├── .env.example
└── README.md

⚙️ Setup Instructions
1️⃣ Install Dependencies

Make sure you have Node.js (v18 or later) installed.
Then run:

npm install

2️⃣ Set Environment Variables

Create a .env file in your root folder and add:

PORT=3000
API_KEY=12345


(A .env.example file is already provided to guide you.)

3️⃣ Run the Server

Start the API using:

node server.js


or, if you have nodemon installed:

npx nodemon server.js

4️⃣ Test the Endpoints

The server runs at:
👉 http://localhost:3000

🧠 API Endpoints
1. Root Endpoint

GET /
Returns a welcome message.
Example Response:

{
  "message": "Welcome to the Product API! Go to /api/products to see all products."
}

2. Get All Products

GET /api/products
Returns all products with optional filtering, pagination, and search.
Query Parameters:

Parameter	Type	Description
category	string	Filter by category
page	number	Page number for pagination
limit	number	Items per page
search	string	Search by product name

Example:
GET /api/products?category=electronics&page=1&limit=2&search=laptop

Response:

{
  "total": 2,
  "page": 1,
  "limit": 2,
  "data": [
    {
      "id": "1",
      "name": "Laptop",
      "description": "High-performance laptop with 16GB RAM",
      "price": 1200,
      "category": "electronics",
      "inStock": true
    }
  ]
}

3. Get Product by ID

GET /api/products/:id
Returns a single product.

Example:
GET /api/products/2

Response:

{
  "id": "2",
  "name": "Smartphone",
  "description": "Latest model with 128GB storage",
  "price": 800,
  "category": "electronics",
  "inStock": true
}

4. Create a New Product

POST /api/products
Creates a new product.
🛡️ Requires header:
x-api-key: 12345

Request Body:

{
  "name": "Wireless Mouse",
  "description": "Ergonomic design",
  "price": 25,
  "category": "electronics",
  "inStock": true
}


Response:

{
  "id": "generated-uuid",
  "name": "Wireless Mouse",
  "description": "Ergonomic design",
  "price": 25,
  "category": "electronics",
  "inStock": true
}

5. Update Product

PUT /api/products/:id
Updates an existing product.
🛡️ Requires header:
x-api-key: 12345

Request Body (same structure as POST):

{
  "price": 900,
  "inStock": false
}


Response:

{
  "id": "2",
  "name": "Smartphone",
  "description": "Latest model with 128GB storage",
  "price": 900,
  "category": "electronics",
  "inStock": false
}

6. Delete Product

DELETE /api/products/:id
Deletes a product by ID.
🛡️ Requires header:
x-api-key: 12345

Example:
DELETE /api/products/3

Response:

{
  "message": "Product deleted successfully"
}

7. Product Statistics

GET /api/products/stats
Returns product count by category.

Example Response:

{
  "electronics": 2,
  "kitchen": 1
}

⚙️ Middleware Overview
Middleware	Purpose
bodyParser.json()	Parses incoming JSON requests
Logger	Logs method, URL, and timestamp
Auth	Checks for valid x-api-key header
Validation	Ensures required fields exist and are valid
Error Handler	Catches and returns all application errors
🧪 Error Handling Examples

Missing API Key:

{
  "message": "Unauthorized: Invalid or missing API key"
}


Invalid Product Data:

{
  "message": "Validation Error: Missing or invalid fields"
}


Product Not Found:

{
  "message": "Product not found"
}

💡 Testing Tools

You can test your API with:

Postman

Insomnia

or curl in your terminal.

Example:

curl -X GET http://localhost:3000/api/products

✅ Submission Checklist

✔️ server.js implemented
✔️ README.md (this file) added
✔️ .env.example added
✔️ Dependencies installed (express, body-parser, uuid)
✔️ Pushed to your GitHub Classroom repo