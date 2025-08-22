# Go CRUD API with MySQL

This is a simple CRUD (Create, Read, Update, Delete) API built with Go and MySQL, designed to work with Laragon's MySQL server.

## Prerequisites

- Go installed on your machine
- Laragon with MySQL running locally
- Git (for cloning the repository)

## Setup Instructions

### 1. Database Setup

1. Open Laragon and ensure MySQL is running
2. Execute the `setup_database.sql` script using Laragon's database management tool (phpMyAdmin or HeidiSQL)
   - Alternatively, you can run it from the command line:
   ```
   mysql -u root < setup_database.sql
   ```

### 2. Install Dependencies

1. Open a terminal/command prompt
2. Navigate to the project directory
3. Install the required Go packages:
   ```
   go mod init go-crud-api
   go get github.com/go-sql-driver/mysql
   go get github.com/gorilla/mux
   ```

### 3. Run the Application

1. Start the server:
   ```
   go run main.go
   ```
2. The server will start on port 8000, and you should see the message:
   ```
   Successfully connected to Laragon MySQL database!
   Server starting on port 8000...
   ```

## API Endpoints

The API provides the following endpoints:

- `GET /users` - Get all users
- `GET /user/{id}` - Get a specific user by ID
- `POST /user` - Create a new user
- `PUT /user/{id}` - Update an existing user
- `DELETE /user/{id}` - Delete a user

### Example Usage

#### Get all users
```
GET http://localhost:8000/users
```

#### Get a specific user
```
GET http://localhost:8000/user/1
```

#### Create a new user
```
POST http://localhost:8000/user
Content-Type: application/json

{
    "name": "Bob Smith",
    "email": "bob@example.com"
}
```

#### Update a user
```
PUT http://localhost:8000/user/1
Content-Type: application/json

{
    "name": "John Doe Updated",
    "email": "john.updated@example.com"
}
```

#### Delete a user
```
DELETE http://localhost:8000/user/1
```

## Troubleshooting

If you encounter any issues:

1. Make sure Laragon's MySQL server is running
2. Verify the database connection parameters in `main.go`
3. Ensure the `go_crud_api` database exists and the `users` table is created
4. Check that the port 8000 is not being used by another application
