# Go Bookstore API

This is a Golang backend API for a simple bookstore application. It includes functionality for managing books and other related tasks.

## Folder Structure

```
.
├── go.mod
├── go.sum
├── cmd
│   └── main
│       ├── main.exe
│       ├── main.go
├── pkg
│   ├── config
│   │   └── app.go
│   ├── controllers
│   │   └── book-controller.go
│   ├── models
│   │   └── book.go
│   ├── routes
│   │   └── bookstore-routes.go
│   ├── utils
│       └── utils.go
```

## Setup

1. **Clone the repository**

   ```sh
   git clone https://github.com/rupeshdev18/go-bookstore.git
   cd go-bookstore
   ```

2. **Install Dependencies**

   Ensure you have [Go](https://golang.org/dl/) installed. Then run:

   ```sh
   go mod tidy
   ```

3. **Configure Database**

   Update the `Connect` function in `pkg/config/app.go` with your MySQL database credentials:

   ```go
   package config

   import (
       "github.com/jinzhu/gorm"
       _ "github.com/jinzhu/gorm/dialects/mysql"
   )

   var (
       db *gorm.DB
   )

   func Connect() {
       d, err := gorm.Open("mysql", "username:password@tcp(127.0.0.1:3306)/simplerest?charset=utf8&parseTime=True&loc=Local")
       if err != nil {
           panic(err)
       }
       db = d
   }

   func GetDB() *gorm.DB {
       return db
   }
   ```

4. **Run the Application**

   ```sh
   go run cmd/main/main.go
   ```

## API Endpoints

### Books

- **GET /books**: Get all books
- **GET /books/{id}**: Get a book by ID
- **POST /books**: Create a new book
- **PUT /books/{id}**: Update a book by ID
- **DELETE /books/{id}**: Delete a book by ID

## Project Structure

- `cmd/main`: Entry point of the application
  - `main.go`: Initializes the application and starts the server
- `pkg/config`: Configuration package
  - `app.go`: Database connection setup
- `pkg/controllers`: Controller package
  - `book-controller.go`: Handlers for book-related endpoints
- `pkg/models`: Model package
  - `book.go`: Book model definition and database interactions
- `pkg/routes`: Routes package
  - `bookstore-routes.go`: Route definitions and setup
- `pkg/utils`: Utility package
  - `utils.go`: Common utility functions

## Contributing

1. Fork the repository.
2. Create a new branch.
3. Make your changes.
4. Submit a pull request.

