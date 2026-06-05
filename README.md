# 🛍️ Product CRUD API

A RESTful API for managing products with **filtering** and **pagination**, built with **Node.js**, **Express**, and **MongoDB (Mongoose)**.

> **Internship Project** — Week 2, Project 2 | Syntecxhub Back-End Development Internship

---

## 🚀 Features

- Full **CRUD** operations for a Product resource
- **Filter** products by category or price range
- **Pagination** support for listing products
- Input **validation** with meaningful error messages
- Proper **HTTP status codes** for every response
- Clean **MVC** folder structure
- Global **error handling** middleware

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Runtime | Node.js |
| Framework | Express.js |
| Database | MongoDB Atlas |
| ODM | Mongoose |
| Environment | dotenv |
| Dev Tool | Nodemon |

---

## 📁 Folder Structure

```
Syntecxhub_Product_CRUD_API/
├── config/
│   └── db.js               # MongoDB connection
├── controllers/
│   └── productController.js # CRUD + filter + pagination logic
├── middleware/
│   └── errorHandler.js      # Global error handler
├── models/
│   └── Product.js           # Mongoose schema
├── routes/
│   └── productRoutes.js     # API routes
├── .env                     # Environment variables
├── .gitignore
├── package.json
└── server.js                # Entry point
```

---

## ⚙️ Setup & Installation

### 1. Clone the repository
```bash
git clone https://github.com/Shubhanjali801/backend_syntaxhub/Syntecxhub_Product_CRUD_API.git
cd Syntecxhub_Product_CRUD_API
```

### 2. Install dependencies
```bash
npm install
```

### 3. Configure environment variables

Create a `.env` file in the root directory:
```env
PORT=5000
MONGO_URI=your_mongodb_atlas_connection_string
```

### 4. Run the server
```bash
# Development (with auto-reload)
npm run dev

# Production
npm start
```

Server will start at `http://localhost:5000`

---

## 📡 API Endpoints

Base URL: `http://localhost:5000/api/products`

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/products` | Create a new product |
| GET | `/api/products` | Get all products (supports filters & pagination) |
| GET | `/api/products/:id` | Get a single product by ID |
| PUT | `/api/products/:id` | Update a product by ID |
| DELETE | `/api/products/:id` | Delete a product by ID |

---

## 🔍 Filtering & Pagination

Append query parameters to `GET /api/products`:

| Query Param | Type | Description | Example |
|-------------|------|-------------|---------|
| `category` | String | Filter by category | `?category=electronics` |
| `minPrice` | Number | Minimum price filter | `?minPrice=500` |
| `maxPrice` | Number | Maximum price filter | `?maxPrice=2000` |
| `page` | Number | Page number (default: 1) | `?page=2` |
| `limit` | Number | Results per page (default: 5) | `?limit=3` |

### Example Queries
```
GET /api/products?category=fitness
GET /api/products?minPrice=500&maxPrice=2000
GET /api/products?page=1&limit=3
GET /api/products?category=electronics&minPrice=1000&page=1&limit=2
```

---

## 📋 Request & Response Examples

### ➕ Create Product — `POST /api/products`

**Request Body:**
```json
{
  "name": "Wireless Headphones",
  "price": 1999,
  "description": "Noise cancelling over-ear headphones",
  "category": "electronics",
  "stock": 50
}
```

**Response `201 Created`:**
```json
{
  "success": true,
  "data": {
    "_id": "664abc123...",
    "name": "Wireless Headphones",
    "price": 1999,
    "description": "Noise cancelling over-ear headphones",
    "category": "electronics",
    "stock": 50,
    "createdAt": "2026-06-03T10:00:00.000Z",
    "updatedAt": "2026-06-03T10:00:00.000Z"
  }
}
```

---

### 📋 Get All Products (Paginated) — `GET /api/products?page=1&limit=3`

**Response `200 OK`:**
```json
{
  "success": true,
  "total": 8,
  "page": 1,
  "totalPages": 3,
  "count": 3,
  "data": [ ... ]
}
```

---

### 🔍 Get Product by ID — `GET /api/products/:id`

**Response `404 Not Found`:**
```json
{
  "success": false,
  "message": "Product not found"
}
```

---

### ✏️ Update Product — `PUT /api/products/:id`

**Request Body (partial update supported):**
```json
{
  "price": 1799,
  "stock": 40
}
```

---

### 🗑️ Delete Product — `DELETE /api/products/:id`

**Response `200 OK`:**
```json
{
  "success": true,
  "message": "Product deleted successfully"
}
```

---

## ✅ HTTP Status Codes Used

| Code | Meaning |
|------|---------|
| 200 | OK |
| 201 | Created |
| 400 | Bad Request / Validation Error |
| 404 | Not Found |
| 500 | Internal Server Error |

---

## 🧪 Testing

All endpoints tested using [Postman](https://www.postman.com/).

**Sample test data categories:** `electronics`, `footwear`, `fitness`, `home`, `accessories`

---

## 👩‍💻 Author

**Shubhanjali**
B.Tech Information Technology — IIIT Allahabad
Syntecxhub Back-End Development Intern

---

## 📄 License

This project is built for internship/learning purposes.