# Solar Geeks – Full-Stack E-Commerce Store

An online store for space-themed products, built as my capstone project at
Tech Elevator. It has a Vue 3 front end and a Spring Boot REST API backed by
PostgreSQL.

## Features

- **Accounts:** register and log in, secured with JWT authentication
- **Product catalog:** browse products and view product details
- **Shopping cart:** add and remove items, clear the cart, and see a running
  total
- **Sales tax:** looked up per state from an external tax API and added to the
  cart total
- **Wishlists (API only):** create and delete wishlists, and add or remove
  products

## Tech stack

| Layer | Technologies |
|---|---|
| Front end | Vue 3, Vuex, Vue Router, Axios, Vite |
| Back end | Java 11, Spring Boot, Spring Security (JWT), JDBC |
| Database | PostgreSQL |
| Tooling | Maven, Postman, JUnit |

## Repository layout

```
solar-geeks-frontend/
  client/            Vue 3 store front
  server/            Spring Boot REST API used by the store front (port 9000)
    database/        Schema, seed data and ERD
solar-geeks-backend/ Earlier REST API milestone: cart and state sales tax (port 8080)
```

## API endpoints (`solar-geeks-frontend/server`)

| Method | Path | Description |
|---|---|---|
| POST | `/register` | Create an account |
| POST | `/login` | Log in and receive a JWT |
| GET | `/products` | List products |
| GET | `/products/{id}` | Product details |
| GET | `/cart` | Current user's cart |
| POST | `/cart/items` | Add an item to the cart |
| DELETE | `/cart/items/{itemId}` | Remove an item |
| DELETE | `/cart` | Clear the cart |
| GET / POST | `/wishlists` | List or create wishlists |
| GET / DELETE | `/wishlists/{id}` | View or delete a wishlist |
| POST / DELETE | `/wishlists/{id}/products/{productId}` | Add or remove a product |

## Running locally

**Prerequisites:** Java 11+, Node.js, PostgreSQL

1. **Database:** create a database named `m2_final_project`, then run
   `solar-geeks-frontend/server/database/m2_final_project.sql`. The script
   creates the tables, sample products and two test users (`user` and
   `admin`, both with the password `password`).
2. **API:** set your PostgreSQL username and password in
   `solar-geeks-frontend/server/src/main/resources/application.properties`,
   then start it:
   ```bash
   cd solar-geeks-frontend/server
   ./mvnw spring-boot:run
   ```
   The API runs at `http://localhost:9000`.
3. **Front end:**
   ```bash
   cd solar-geeks-frontend/client
   npm install
   npm run dev
   ```
   Open the URL Vite prints (usually `http://localhost:5173`).
