# Requirements Engineering

# Capacity Estimation

# Data Modeling

# API Design

## e-Commerce

### Product Catalog
- `GET /products`
- `GET /products/{id}`
- `POST /products`
- `PUT /products/{id}`
- `DELETE /products/{id}`
 
### User Account Management API
- `POST /users/register` : create a new user
- `POST /users/login` : Authenticate user
- `GET /users/{id}` : Retrieve profile information
- `PUT /users/{id}` : Update profile information for a user
- `DELETE /users/{id}` : Delete a user account

### Order Management API
- `POST /orders/submitOrder` : Creates an order
- `GET /orders/{id}` : Retrieve an order
- `POST /orders/{id}/pay` : Initiate payment for an order

### Payment API
- `POST /payments` : Process a payment transaction
- `GET /payments/{id}` : Retrieve payment details
- `POST /payments/{id}/refund` : Refund a payment
- `GET /payments/{id}/status` : Get the status of a payment

### Shopping cart API
- `GET /cart` : Retrive current users shopping cart
- `POST /cart/items` : Add items to the cart
- `PUT /cart/items/{id}` : Update item count of an item in cart
- `DELETE /cart/items/{id}` : Delete the item from cart
- `POST /cart/checkout` : Checkout the cart
# System Design

# Design Discussion
