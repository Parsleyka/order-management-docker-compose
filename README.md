# order-management-docker-compose

# FullStack Test Application

This project contains of
- front-end(Vite+React) (https://github.com/Parsleyka/order-management-front.git)
- back-end(Node.js(Express.js)) and database(PostgreSQL) (https://github.com/Parsleyka/order-management-back.git)

# API

POST /orders – Create an Order
`body: {
    userId: 'uuid'
    productId: 'uuid'
    quantity: 'number'
}`
GET /orders/:userId – Retrieve a User’s Orders


## Configuration
### How to start

1. Download project
2. Be sure you have configured Docker
3. Add `.env` file based on `.env.example`
 - Note: There are default mocked values, and they are ready for test start up

Docker images list:
- Database (PostgreSQL)
- Database Admin Panel (pgAdmin)
- Backend (Node.js(Express.js))
- Frontend (Vite+React)

4. Run command `docker-compose up --build` and wait for start
5. It is ready for use

### How to use
1. Navigate to pgAdmin to ensure database is set and ready for use
- Note: By default pgAdmin hosted on `http://localhost:5050`
- Note: I mocked some data for testing purpose during image configuration.
2. Navigate to frontend and use application
- Note: By default it hosted on `http://localhost:5173/`