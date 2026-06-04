# Todo App - 3 Tier Architecture

A simple todo application with **React** frontend, **Node.js/Express** backend, and **MongoDB** database.

## Project Structure

```
todo-app/
├── backend/          # Node.js/Express server
│   ├── models/       # MongoDB schemas
│   ├── routes/       # API routes
│   ├── server.js     # Express server setup
│   ├── package.json
│   └── .env
├── frontend/         # React application
│   ├── public/       # Static files
│   ├── src/
│   │   ├── components/  # React components
│   │   ├── App.js
│   │   ├── index.js
│   │   └── App.css
│   └── package.json
└── README.md
```

## Prerequisites

- Node.js (v14 or higher)
- MongoDB (local or Atlas)

## Setup Instructions

### 1. MongoDB Setup

**Option A: Local MongoDB**
- Install MongoDB from https://www.mongodb.com/try/download/community
- Start MongoDB service:
  ```bash
  # Windows
  net start MongoDB
  
  # macOS
  brew services start mongodb-community
  
  # Linux
  sudo systemctl start mongodb
  ```

**Option B: MongoDB Atlas (Cloud)**
- Create free account at https://www.mongodb.com/cloud/atlas
- Create a cluster and get connection string
- Update `.env` file in backend with your connection string

### 2. Backend Setup

```bash
cd backend

# Install dependencies
npm install

# Create .env file (already provided)
# Edit .env to set your MongoDB URI if needed

# Start server
npm start
# Server will run on http://localhost:5000
```

The backend will automatically connect to MongoDB and expose REST APIs:
- `GET /api/todos` - Get all todos
- `POST /api/todos` - Create new todo
- `GET /api/todos/:id` - Get single todo
- `PUT /api/todos/:id` - Update todo
- `DELETE /api/todos/:id` - Delete todo

### 3. Frontend Setup

In a new terminal:

```bash
cd frontend

# Install dependencies
npm install

# Start development server
npm start
# App will open at http://localhost:3000
```

## Usage

1. **Add Todo**: Enter title and optional description, click "Add Todo"
2. **Toggle Completion**: Click checkbox to mark as done/undone
3. **Edit Todo**: Click edit (✎) button to modify
4. **Delete Todo**: Click delete (✕) button to remove

## API Endpoints

### Get All Todos
```bash
curl http://localhost:5000/api/todos
```

### Create Todo
```bash
curl -X POST http://localhost:5000/api/todos \
  -H "Content-Type: application/json" \
  -d '{"title":"My Todo","description":"Description here"}'
```

### Update Todo
```bash
curl -X PUT http://localhost:5000/api/todos/{id} \
  -H "Content-Type: application/json" \
  -d '{"title":"Updated","description":"New desc","completed":true}'
```

### Delete Todo
```bash
curl -X DELETE http://localhost:5000/api/todos/{id}
```

## Environment Variables

**Backend (.env)**
```
PORT=5000
MONGODB_URI=mongodb://localhost:27017/todo-app
NODE_ENV=development
```

## Features

✅ Create, Read, Update, Delete (CRUD) operations  
✅ Mark todos as completed  
✅ Edit todo titles and descriptions  
✅ Responsive UI design  
✅ Error handling  
✅ Loading states  

## Tech Stack

- **Frontend**: React 18, Axios, CSS3
- **Backend**: Node.js, Express, Mongoose
- **Database**: MongoDB
- **Port**: Frontend on 3000, Backend on 5000

## Troubleshooting

**Cannot connect to MongoDB:**
- Ensure MongoDB is running
- Check connection string in `.env`
- For Atlas, whitelist your IP in security settings

**Backend/Frontend not communicating:**
- Ensure both servers are running
- Check CORS is enabled in backend
- Check proxy setting in frontend `package.json`

## Next Steps (Future Enhancements)

- User authentication (JWT)
- Task categories/tags
- Due dates and reminders
- Task priority levels
- Dark mode
- Docker containerization
- AWS deployment (ECS, RDS, CloudFront)
