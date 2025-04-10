# Order Management - Full Stack Application

A demonstration full-stack application for managing simple orders, built with React, Node.js, PostgreSQL, and Docker Compose.

**Project Repositories:**

*   **Frontend (Vite + React):** [https://github.com/Parsleyka/order-management-front.git](https://github.com/Parsleyka/order-management-front.git)
*   **Backend (Node.js + Express.js + PostgreSQL):** [https://github.com/Parsleyka/order-management-back.git](https://github.com/Parsleyka/order-management-back.git)

---

## Overview

This project provides a basic system for creating and viewing orders. It serves as a practical example of integrating a React frontend with a Node.js backend API and a PostgreSQL database, all orchestrated using Docker Compose for easy setup and deployment.

---

## Tech Stack

*   **Frontend:** React, Vite
*   **Backend:** Node.js, Express.js
*   **Database:** PostgreSQL
*   **ORM:** Prisma
*   **Database Admin:** pgAdmin 4
*   **Containerization:** Docker, Docker Compose

---

## Prerequisites

Before you begin, ensure you have the following installed:

*   [Docker](https://docs.docker.com/get-docker/)
*   [Docker Compose](https://docs.docker.com/compose/install/) (Usually included with Docker Desktop)

---

## Getting Started

Follow these steps to get the application running locally using Docker Compose.

1.  **Clone Docker Compose:**
    ```bash
    git clone https://github.com/Parsleyka/order-management-docker-compose.git
    ```

2.  **Configure Environment:**
    *   Navigate to the project folder
    *   Create a `.env` file by copying the example:
        ```bash
        cp .env.example .env
        ```
    *   Review the `.env` file. The default mocked values are suitable for a quick test start-up.

3.  **Build and Run with Docker Compose:**
    *   Make sure Docker Desktop (or Docker daemon) is running.
    *   From the directory run:
        ```bash
        docker-compose up --build
        ```
    *   Wait for the command to complete. It will download the PostgreSQL and pgAdmin images, build your application images, and start all the containers.

4.  **Ready!** The application stack should now be running.

---

## Accessing Services

Once the containers are up and running:

*   **Frontend Application:**
    *   Access the main user interface in your browser:
    *   **[http://localhost:5173](http://localhost:5173)** (or the `VITE_HOST_URL`:`VITE_HOST_PORT` specified in the frontend's `.env` if customized and used by Docker)

*   **Database Admin (pgAdmin):**
    *   Access pgAdmin to view/manage the PostgreSQL database:
    *   **[http://localhost:5050](http://localhost:5050)** (or the port mapped in `docker-compose.yml`)
    *   Login using the credentials defined in your `.env` file (`DATABASE_PASSWORD`).
    *   *Note:* The database is automatically seeded with some mock data during the backend container's startup process (check backend Dockerfile/entrypoint) for testing purposes.

---

## API Documentation

The backend exposes the following REST API endpoints (base path `/api` assumed):

### Orders

*   **`POST /api/orders`**
    *   **Description:** Creates a new order. Requires sufficient user balance and product stock.
    *   **Request Body:**
        ```json
        {
          "userId": "string (UUID)",
          "productId": "string (UUID)",
          "quantity": "number"
        }
        ```

*   **`GET /api/orders/:userId`**
    *   **Description:** Retrieves all orders placed by a specific user.
    *   **URL Parameters:**
        *   `userId` (string, UUID): The ID of the user whose orders are to be retrieved.

---

## Docker Services

The `docker-compose.yml` file defines the following services:

*   `backend`: The Node.js/Express.js application serving the API.
*   `frontend`: The Vite/React application serving the user interface.
*   `db`: The PostgreSQL database instance.
*   `pgadmin`: The pgAdmin 4 web interface for database administration.

---