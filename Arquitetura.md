# Node.js API Starter Kit for Campus Map Project

## 🛠️ Core Stack
| Category       | Tool/Library          | Purpose                          | Install Command              |
|----------------|-----------------------|----------------------------------|-----------------------------|
| **Runtime**    | Node.js (LTS)         | JavaScript backend runtime       | [Download](https://nodejs.org/) |
| **Framework**  | Express.js            | Minimalist web framework         | `npm install express`       |
| **Database**   | PostgreSQL            | Relational database (SQL)        | [Download](https://www.postgresql.org/download/) |
|                | MongoDB               | NoSQL database (flexible JSON)   | `npm install mongodb`       |
| **ORM**        | Prisma                | Type-safe database client        | `npm install prisma @prisma/client` |
|                | Mongoose (for MongoDB)| ODM for MongoDB                  | `npm install mongoose`      |

## 📦 Essential Libraries
| Library                | Use Case                          | Install Command              |
|------------------------|----------------------------------|-----------------------------|
| `cors`                 | Enable Cross-Origin Requests     | `npm install cors`          |
| `dotenv`               | Load environment variables       | `npm install dotenv`        |
| `jsonwebtoken` (JWT)   | User authentication              | `npm install jsonwebtoken`  |
| `bcryptjs`             | Password hashing                 | `npm install bcryptjs`      |
| `axios`                | HTTP requests (to external APIs) | `npm install axios`         |

## 🚀 Project Structure
campus-map-api/
├── .env # Environment variables (DB_URL, JWT_SECRET)
├── src/
│ ├── config/ # Database connection setup
│ ├── controllers/ # Route handlers (e.g., buildingController.js)
│ ├── models/ # Database models (Prisma/Mongoose)
│ ├── routes/ # API endpoints (e.g., buildingRoutes.js)
│ ├── middlewares/ # Auth/validation middleware
│ ├── utils/ # Helper functions
│ └── server.js # Entry point
├── prisma/ # Prisma schema (if using Prisma)
└── package.json

## 🔌 Sample Code Snippets

### 1. **Express Server Setup (`server.js`)**
```javascript
const express = require('express');
const cors = require('cors');
require('dotenv').config();

const app = express();
app.use(cors());
app.use(express.json());

// Routes
app.use('/api/buildings', require('./routes/buildingRoutes'));

const PORT = process.env.PORT || 5000;
app.listen(PORT, () => console.log(`API running on port ${PORT}`));
```

