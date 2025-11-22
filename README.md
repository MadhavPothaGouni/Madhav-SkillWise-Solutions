# Inventory Management System

Full-stack inventory management web application with:

- User authentication (JWT)
- Product CRUD
- Sorting and filtering
- CSV import/export
- Inventory history tracking
- Responsive UI (Bootstrap)

This repo contains both frontend (React) and backend (Node.js + Express + SQLite) code.

---

## Live Demo Links

- **Backend (Render)**  
  https://backendinventory-3.onrender.com  
  Health check response: `Backend is running...`
  
- **Frontend (Vercel)**  
  https://frontend-inventory-lpxo.vercel.app


The frontend is configured to talk to the backend via:

- `REACT_APP_API_URL = https://backendinventory-3.onrender.com/api`

---

## Demo Account (Optional)

You can log in quickly using this demo user, or create your own:

- Email: `demo@test.com`  
- Password: `Demo@123`

The interviewer can also register their own account and test everything end-to-end.

---

## Features

### Authentication

- Register new user
- Login
- Protected routes on the backend using JWT
- Password hashing with bcrypt
- Token stored in `localStorage` on the frontend
- Axios interceptor attaches `Authorization: Bearer <token>` to every API request

### Products and Inventory

- Add product
- Edit product (inline editing in table rows)
- Delete product
- Stock status badges:
  - `In Stock` when stock > 0
  - `Out of Stock` when stock = 0
- Inventory history:
  - Tracks old stock and new stock whenever quantity changes
  - Stores `changed_by` and timestamp
  - History displayed in a sidebar

### Table and UI

- Pagination (server side)
- Sorting (server side)
  - Sort by: id, name, category, brand, stock
  - Ascending / descending
- Search by product name
- Category filter dropdown
- CSV import (bulk products)
- CSV export
- Responsive layout using Bootstrap
- “Add Product” modal form

---

## Project Structure

At the root of this repo:

```text
inventory-management/
├── backend/      # Node.js + Express + SQLite API
└── frontend/     # React app (Vercel deployment)
Backend (Node.js + Express + SQLite)
Tech Stack

Node.js

Express

SQLite3

JWT (jsonwebtoken)

bcryptjs

multer (CSV upload)

csv-parser

express-validator

dotenv

Important Files

backend/server.js
Express server setup, routes registration.

backend/db.js
SQLite connection and table creation:

products

inventory_logs

users (for authentication)

backend/routes/products.js
Product CRUD, CSV import/export, inventory history.

backend/routes/auth.js
Register, login, GET /auth/me, JWT middleware.

API Overview

Base URL in production: https://backendinventory-3.onrender.com/api

Main endpoints:

POST /auth/register

POST /auth/login

GET /auth/me

GET /products

GET /products/search

POST /products

PUT /products/:id

DELETE /products/:id

GET /products/:id/history

POST /products/import

GET /products/export

Frontend (React)
Tech Stack

React

React Router

Axios

Bootstrap

React Toastify

Important Files

frontend/src/services/api.js

Configures Axios instance with baseURL

Reads REACT_APP_API_URL from environment

Adds JWT token to Authorization header

frontend/src/pages/LoginPage.js

frontend/src/pages/RegisterPage.js

frontend/src/pages/ProductsPage.js

Search, filter, sort, pagination

Add Product modal

Inventory history sidebar

frontend/src/components/

SearchBar

CategoryFilter

ImportExportBar

ProductTable

ProductRow

InventoryHistorySidebar

Environment Variables
Backend (.env)

Create a .env file inside the backend folder:

PORT=5000
JWT_SECRET=supersecretjwtkey


You can change JWT_SECRET to any strong secret string.

On Render, set Environment Variables:

PORT = 5000 (or leave default if using Render’s port)

JWT_SECRET = supersecretjwtkey (or your own secret)

Frontend (.env)

Create a .env file inside the frontend folder for local development:

REACT_APP_API_URL=http://localhost:5000/api


On Vercel (production):

Key: REACT_APP_API_URL

Value: https://backendinventory-3.onrender.com/api

Re-deploy after changing environment variables so the build picks them up.

Running Locally
1. Clone the repo
git clone https://github.com/MadhavPothaGouni/Madhav-SkillWise-Solutions.git
cd Madhav-SkillWise-Solutions

2. Backend setup
cd backend
npm install


Create backend/.env:

PORT=5000
JWT_SECRET=supersecretjwtkey


Start backend:

npm run dev   # uses nodemon
# or
npm start


Backend will run at: http://localhost:5000

Health check: http://localhost:5000/ → Backend is running...

3. Frontend setup

Open a new terminal:

cd frontend
npm install


Create frontend/.env:

REACT_APP_API_URL=http://localhost:5000/api


Start frontend:

npm start


Frontend will run at: http://localhost:3000

How the Deployed Version Works

Frontend (Vercel) is built with REACT_APP_API_URL pointing to the Render backend:

https://backendinventory-3.onrender.com/api

Axios in frontend/src/services/api.js uses this URL as baseURL.

Opens this:

https://frontend-inventory-lpxo.vercel.app

they can:

Click “Register” and create a new account (their own email and password)

Log in

Manage products

Import/Export CSV

View inventory history