# Important points

- System should be highly available for search, view events/hotels/etc
- System should have really low latency for searches < 500 ms ( low latency for driver matches, )
- System should be highly consistent for booking events/hotels/flights/drivers ( No booking twice ) 

# Capacity Estimation
```
Chat APP
--------
1 million DAU
50 messages/day
Each message : 5KB
Retention : 5 years
```
- STORAGE Requirements
```
1 million users X 50 messages/day = 50 million messages/day
5 KB X 50 mi messages/day = 250 X 10 ^ 9 = 250 GB /day
250 GB X 356 days = 90 TB/year
90 TB/year x 5 = 450 TB/5 year
```

- Bandwidth Requirements
```
 50 messages/day x 5KB/message = 250 KB/day/user
 1 mil x 250 KB => 250 GB / day
 Bandwidth/sec : 250 x 10^9 / 100,000 => 2.5 MB/second
```

- Transactions/sec
```
 50 mil messages/day / 100,000 seconds/day => 500 messages/sec
 READ + WRITE TPS => 500 + 500 = 1000 messages/sec
 Peak => 1000 X 2 => 2000 messages/sec
```

# Data Modeling

## Size of various datatypes
```
INT, FLOAT : 4 Bytes
TEXT : 1 KB - 5 KiloBytes
ID# (varchar 36) : 36 Bytes
name (varchar 255) : 256 Bytes
price (decimal(10,2)) : 10 Bytes
created_at (datetime) : 8 Bytes
currency (char(3)) : 3 Bytess
```
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

### Chat app

- `POST /auth/login` : login
- `POST /messages` : Send message API
{
  "sender_id": "user123",
  "recipient_id": "user456",
  "message_type": "text",  // could be 'text', 'image', 'video', etc.
  "content": "Hey, how's it going?",
  "timestamp": "2024-08-18T15:45:00Z"

}

- `GET /chats/{user_ID}/{recipient_ID}`
```
GET /chats/{user_id}/recipient_ID?page=1&page_size=20 HTTP/1.1
HOST : api.chatapp.com
Authorization : Bearer <<TOKEN>>
```

```
{
"messages" : [
{
 "message_id" : "xxxx11",  //36 bytes
 "sender_id" : "123D",     //36 bytes
 "recipient_id" : "342D",  //36 bytes
 "message_type" : "TEXT", //IMAGE,VIDEO,FILE etc //8 Bytes
 "messsage_content" : "", //1KB - 5 KB
 "timestamp" : "2024-08-19T15:01:12" //8 Bytes
}, //5.1KB each messsage
{
 "message_id" : "xxxx11",
 "sender_id" : "123D",
 "recipient_id" : "342D",
 "message_type" : "TEXT", //IMAGE,VIDEO,FILE etc
 "messsage_content" : "",
 "timestamp" : "2024-08-19T15:01:12"
}
],
"pagination": {
"total_messsages" : 50,
"page" : 1,
"page_size" : 20,
"total_pages" : 3
}
}

```

# System Design

# Design Discussion
