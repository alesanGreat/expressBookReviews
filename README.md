# Book Reviews API

A RESTful API for managing books and user reviews built with Express.js, featuring user authentication and JWT-based authorization.

## Features

- **User Management**: Registration and login system
- **Book Catalog**: Browse books by ISBN, author, or title
- **Review System**: Authenticated users can add, update, and delete reviews
- **JWT Authentication**: Secure endpoints with JSON Web Tokens
- **Session Management**: Express sessions for user state

## Technologies Used

- **Node.js** - JavaScript runtime environment
- **Express.js** - Web framework for Node.js
- **JWT (jsonwebtoken)** - For secure authentication
- **Express-session** - Session middleware
- **Axios** - HTTP client for async requests
- **Nodemon** - Development tool for automatic restart

## Project Structure

```
expressBookReviews/
├── final_project/
│   ├── index.js                 # Main entry point
│   ├── package.json             # Dependencies and scripts
│   └── router/
│       ├── auth_users.js        # Routes for authenticated users
│       ├── booksdb.js          # In-memory books database
│       └── general.js          # Public routes
├── LICENSE                     # Apache 2.0 License
└── README.md                   # This file
```

## Installation and Setup

1. **Navigate to the project directory**:
   ```powershell
   cd "final_project"
   ```

2. **Install dependencies**:
   ```powershell
   npm install
   ```

3. **Start the server**:
   ```powershell
   npm start
   ```

The server will run on `http://localhost:5000`

## API Endpoints

### Public Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/` | Get list of all books |
| GET | `/isbn/:isbn` | Get book details by ISBN |
| GET | `/author/:author` | Get books by author |
| GET | `/title/:title` | Get books by title |
| GET | `/review/:isbn` | Get reviews for a book |
| POST | `/register` | Register new user |

### Authenticated Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/customer/login` | User login |
| PUT | `/customer/auth/review/:isbn` | Add/update review |
| DELETE | `/customer/auth/review/:isbn` | Delete review |

## API Usage

### User Registration

```http
POST /register
Content-Type: application/json

{
    "username": "user123",
    "password": "myPassword"
}
```

### User Login

```http
POST /customer/login
Content-Type: application/json

{
    "username": "user123",
    "password": "myPassword"
}
```

### Add Review

```http
PUT /customer/auth/review/1
Content-Type: application/json
Authorization: Bearer <token>

{
    "review": "Excellent book, highly recommended!"
}
```

### Get Books by Author

```http
GET /author/Chinua%20Achebe
```

## Database

The application uses an in-memory database that includes 10 classic books with information such as:
- Author
- Title
- Reviews (initially empty object)

## Technical Features

### Authentication
- User registration with duplicate validation
- Login system with JWT
- Authentication middleware for protected routes
- Express sessions for state management

### Asynchronous Handling
- Implementation with async/await
- Use of Promises for asynchronous operations
- Integration with Axios for HTTP requests

### Validations
- Required field validation
- Book existence verification
- User authentication for protected actions

## Development

### Available Scripts

- `npm start` - Starts the server with nodemon for automatic reload
- `npm test` - Runs tests (currently not implemented)

### Environment Variables

The server uses the following configurations:
- Port: 5000
- JWT Secret: "access"
- Session Secret: "fingerprint_customer"

## License

This project is licensed under the Apache License 2.0. See the `LICENSE` file for more details.

## Developer Notes

This project is part of the IBM Full Stack Developer course on Coursera, specifically from the Node.js and Express module. It implements best practices for RESTful APIs and secure authentication.