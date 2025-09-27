# Node.js E-Commerce API (Dockerized)

This is a full-featured **E-Commerce API** built with **Node.js, Express,** and **MongoDB**, now fully **Dockerized** for easy deployment. It includes all essential e-commerce functionalities such as user authentication, product and category management, orders, and more.

## Features

- User Registration & Login

- Product CRUD (Create, Read, Update, Delete)

- Category CRUD

- Order Management

- Product Gallery Upload

- Featured Products

- Sales & Order Reports

- Dockerized setup for quick deployment

## Technologies

- Node.js & Express

- MongoDB

- Docker & Docker Compose

- RESTful API design

## Docker Compose Setup 

Clone the repository:
```
git clone https://github.com/NahidCSERU/NODEJS-ECOMMERCE-API.git
cd nodejs-ecommerce-api
```

## Environment Variables

Create a `.env` file in the root folder with the following variables:
```
PORT=3000
MONGO_URI=your_mongo_uri_here
SECRET=your_jwt_secret_here
API_URL=/api/v1
```

**Run the full stack with Docker Compose:**
```
docker-compose up -d
```

**This will start:**
```
API server on http://localhost:3000

MongoDB database on default port 27017
```
**To stop the services:**
```
docker-compose down
```
## Testing API Endpoints with Postman
###  Pre-requisites
- Postman installed
## Import Postman Collection
- Open Postman.

- Import the collection file: Ecommerce-API.postman-collection.json

## 1. Register User

- **Method:** POST

- **URL**: `{{baseUrl}}/users/register`

- **Body (JSON):**
```
{
  "name": "Test User",
  "email": "test123@example.com",
  "password": "password",
  "phone": "+947187521",
  "isAdmin": false,
  "street": "New Street",
  "apartment": "Block D",
  "zip": "10871",
  "city": "Colombo",
  "country": "SriLanka"
}
````

Description: Registers a new user in the database. Use unique email to avoid duplicate errors.
## 2. Login

- **Method:** POST

- **URL:** {{baseUrl}}/users/login

- **Body (JSON):**
```
{
  "email": "admin@admin.com",
  "password": "password"
}
```

**Description:** Logs in the user and returns a JWT token for authentication.

**Postman Test Script:** Save token and userId to environment variables:
```
let res = pm.response.json();
pm.environment.set("token", res.token);
pm.environment.set("userId", res.user._id);
```
## 3. Get All Users

- **Method:** GET

- **URL:** {{baseUrl}}/users

- **Headers:** Authorization: Bearer {{token}}

- **Description:** Fetches all registered users.

## 4. Get Single User

- **Method:** GET

- **URL:** {{baseUrl}}/users/{{userId}}

- **Headers:** Authorization: Bearer {{token}}

- **Description:** Fetches a specific user by ID.

## 5. Other API Endpoints

- Use similar format for Products, Orders, etc.

- Ensure Authorization header is set using {{token}}.

- Replace path variables with environment variables where required.
## Testing Endpoints

### User Routes
| Method | Endpoint                | Description     |
| ------ | ----------------------- | --------------- |
| POST   | /api/v1/users/register  | Create User     |
| POST   | /api/v1/users/login     | Login User      |
| GET    | /api/v1/users           | Get All Users   |
| GET    | /api/v1/users/{id}      | Get Single User |
| DELETE | /api/v1/users/{id}      | Delete User     |
| GET    | /api/v1/users/get/count | Get Users Count |
### Category Routes
| Method | Endpoint                | Description         |
| ------ | ----------------------- | ------------------- |
| POST   | /api/v1/categories      | Create Category     |
| GET    | /api/v1/categories      | Get All Categories  |
| GET    | /api/v1/categories/{id} | Get Single Category |
| PUT    | /api/v1/categories/{id} | Update Category     |
| DELETE | /api/v1/categories/{id} | Delete Category     |

### Product Routes
| Method | Endpoint                              | Description           |
| ------ | ------------------------------------- | --------------------- |
| POST   | /api/v1/products                      | Create Product        |
| GET    | /api/v1/products                      | Get All Products      |
| GET    | /api/v1/products/{id}                 | Get Single Product    |
| PUT    | /api/v1/products                      | Update Product        |
| DELETE | /api/v1/products/{id}                 | Delete Product        |
| POST   | /api/v1/products/gallery-images/{id}  | Upload Product Images |
| GET    | /api/v1/products/get/count            | Get Product Count     |
| GET    | /api/v1/products/get/featured/{count} | Get Featured Products |

### Order Routes
| Method | Endpoint                                | Description      |
| ------ | --------------------------------------- | ---------------- |
| POST   | /api/v1/orders                          | Create Order     |
| GET    | /api/v1/orders                          | Get All Orders   |
| GET    | /api/v1/orders/{id}                     | Get Single Order |
| PUT    | /api/v1/orders/{id}                     | Update Order     |
| DELETE | /api/v1/orders/{id}                     | Delete Order     |
| GET    | /api/v1/orders/get/count                | Get Total Orders |
| GET    | /api/v1/orders/get/totalsales           | Get Total Sales  |
| GET    | /api/v1/orders/get/usersorders/{userid} | Get User Orders  |

## Notes

- Always login first to get a valid token.

- Use unique data for endpoints like registration to avoid duplicate key errors.

- Environment variables like `{{token}}` and `{{userId}}` ensure secure and automated testing.

- Never commit real secrets to GitHub; use placeholders in README.


### Author
[**Dinush Chathurya**](https://github.com/dinushchathurya/nodejs-ecommerce-api.git)  
Dockerized by [**Nahid Hasan**](https://github.com/NahidCSERU)
