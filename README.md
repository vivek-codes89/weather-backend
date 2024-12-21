# Weather Backend

This repository contains the backend code for a weather application. It includes user management, logging, and weather API integration functionalities.

---

## Prerequisites

Before running this project, ensure you have the following installed:

- [Node.js](https://nodejs.org/) (v14 or higher recommended)
- [MySQL](https://www.mysql.com/)

---

## Installation

1. Clone the repository:
   ```bash
   git clone git@github.com:vivek-codes89/weather-backend.git
   cd weather-be
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Create a `.env` file in the root directory with the following content:
   ```env
   PORT=5000
   DB_HOST=127.0.0.1
   DB_USER='root'
   DB_PASSWORD=
   DB_NAME='weather_app'
   DB_PORT=3306
   DB_DIALECT='mysql'
   JWT_SECRET='your_jwt_secret'
   WEATHER_API_KEY='f7a5a96bb558ce041d7474101ffaf9ad'
   ```

4. Set up the database:
   - Open your MySQL client and run the following queries:
     ```sql
     CREATE DATABASE weather_app;

     USE weather_app;

     CREATE TABLE users (
         id INT AUTO_INCREMENT PRIMARY KEY,
         username VARCHAR(255) NOT NULL UNIQUE,
         password VARCHAR(255) NOT NULL,
         email VARCHAR(255) NOT NULL UNIQUE,
         first_name VARCHAR(255),
         last_name VARCHAR(255),
         phone_number VARCHAR(15),
         created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
         latitude DOUBLE,
         longitude DOUBLE
     );

     CREATE TABLE logs (
         id INT AUTO_INCREMENT PRIMARY KEY,
         user_id INT,
         query VARCHAR(255),
         timestamp TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
         FOREIGN KEY (user_id) REFERENCES users(id) ON DELETE CASCADE ON UPDATE CASCADE
     );
     ```

---

## Scripts

### Start the Development Server
```bash
nodemon server.js
```
