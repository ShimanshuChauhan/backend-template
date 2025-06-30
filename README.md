# Backend Template

A robust Node.js backend template built with Express.js, featuring comprehensive error handling, middleware setup, and MongoDB integration.

## 📋 Table of Contents

- [Features](#features)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Error Handling](#error-handling)
- [Available Scripts](#available-scripts)
- [Dependencies](#dependencies)
- [Contributing](#contributing)

## ✨ Features

- **Express.js** framework for building RESTful APIs
- **MongoDB** integration with Mongoose ODM
- **Comprehensive error handling** with custom error classes
- **Environment-based configuration** using dotenv
- **Development logging** with Morgan
- **Async error handling** utilities
- **Production-ready** error responses

## 🚀 Prerequisites

Before you begin, ensure you have the following installed on your machine:

- **Node.js** (version 14 or higher)
- **npm** (Node Package Manager)
- **MongoDB** (local installation or MongoDB Atlas account)

## 📦 Installation

1. **Clone the repository** (or download the template):
   ```bash
   git clone <your-repository-url>
   cd backend-template
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

3. **Create environment configuration file**:
   ```bash
   # Create config.env file in the root directory
   touch config.env
   ```

## ⚙️ Configuration

Create a `config.env` file in the root directory and add the following environment variables:

```env
NODE_ENV=development
PORT=3000
DATABASE= mongodb+srv://shivanshuchauhan699:<PASSWORD>@cluster0.fsm1x.mongodb.net/?retryWrites=true&w=majority&appName=Cluster0
DATABASE_PASSWORD = password
# Add other environment variables as needed
```

### Environment Variables

- `NODE_ENV`: Set to `development` for detailed error messages, `production` for generic error responses
- `PORT`: Port number for the server (default: 3000)
- `DATABASE_URI`: MongoDB connection string
- Replace database password with `<PASSWORD>`

## 🏃‍♂️ Usage

### Starting the Development Server

```bash
# Start the server
node server.js
```

The server will start and you should see:
- Server running on the specified port
- Console message confirming the server is running
- Access the basic endpoint at `http://localhost:3000/`

### Basic API Endpoint

The template includes a basic GET endpoint:
- **GET** `/` - Returns "Server is running" message

## 📁 Project Structure

```
backend-template/
├── server.js                 # Main server file with database connection
├── app.js                    # Express application setup
├── package.json              # Project dependencies and scripts
├── config.env               # Environment variables (create this)
├── controller/
│   └── errorController.js   # Global error handling middleware
└── utils/
    ├── appError.js          # Custom error class
    └── catchAsync.js        # Async error handling utility
```

### File Descriptions

- **`server.js`**: Main server file that handles database connection and starts the Express application
- **`app.js`**: Express application setup with middleware configuration
- **`controller/errorController.js`**: Global error handling middleware with environment-specific responses
- **`utils/appError.js`**: Custom error class for operational errors
- **`utils/catchAsync.js`**: Utility function to catch async errors in route handlers

## 🔧 Error Handling

This template includes a comprehensive error handling system:

### Custom Error Class (`AppError`)
```javascript
import AppError from './utils/appError.js';

// Example usage
const error = new AppError('Resource not found', 404);
```

### Async Error Handling (`catchAsync`)
```javascript
import catchAsync from './utils/catchAsync.js';

// Example usage in route handlers
app.get('/api/data', catchAsync(async (req, res, next) => {
  // Your async code here
  const data = await someAsyncOperation();
  res.json(data);
}));
```

### Environment-Based Error Responses

- **Development**: Detailed error information including stack traces
- **Production**: Generic error messages for security

## 📜 Available Scripts

Currently available scripts in `package.json`:

```bash
npm test    # Placeholder test script
```

### Recommended Additional Scripts

Add these to your `package.json` scripts section:

```json
{
  "scripts": {
    "start": "nodemon server.js",
    "test": "echo \"Error: no test specified\" && exit 1"
  }
}
```

## 📚 Dependencies

### Production Dependencies
- **express**: Web framework for Node.js
- **mongoose**: MongoDB object modeling for Node.js
- **dotenv**: Environment variable loader

### Development Dependencies
- **morgan**: HTTP request logger middleware
- **nodemon**: Automatically restarts the server when file changes are detected during development 

## 🚀 Next Steps

After setting up the template, you can:

1. **Add routes**: Create route files in a `routes/` directory
2. **Add models**: Create Mongoose models in a `models/` directory
3. **Add controllers**: Expand the `controller/` directory with business logic
4. **Add middleware**: Create custom middleware in a `middleware/` directory
5. **Add validation**: Implement request validation (consider using Joi or express-validator)
6. **Add authentication**: Implement JWT-based authentication
7. **Add testing**: Set up Jest or Mocha for testing

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

---

**Happy coding! 🎉**