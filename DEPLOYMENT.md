# 🏆 Leaderboard System - Deployment Documentation

## 📋 Project Overview
A full-stack real-time leaderboard system built with React.js, Node.js, and MongoDB. Users can claim random points (1-10) and see dynamic rankings with real-time updates.

## 🔗 Essential Links

### 1. **Frontend Application**
- **Live Demo**: [https://quiet-alfajores-edafc7.netlify.app/](https://quiet-alfajores-edafc7.netlify.app/)
- **Local Development**: http://localhost:3003
- **Frontend Repository**: [https://github.com/yourusername/leaderboard-frontend](https://github.com/yourusername/leaderboard-frontend)

### 2. **Backend API**
- **Production API**: [https://leaderboard-backend-zmq3.onrender.com/](https://leaderboard-backend-zmq3.onrender.com/)
- **Local Development**: http://localhost:5000
- **Backend Repository**: [https://github.com/yourusername/leaderboard-backend](https://github.com/yourusername/leaderboard-backend)

### 3. **MongoDB Database**
- **MongoDB Atlas Cluster**: [https://cloud.mongodb.com/v2/your-cluster-id](https://cloud.mongodb.com/v2/your-cluster-id)
- **Database Name**: `leaderboard`
- **Collections**: `users`, `claims`

## 🚀 Deployment Instructions

### **Frontend Deployment (Netlify)**

1. **Build the Frontend:**
   ```bash
   cd frontend
   pnpm install
   pnpm run build
   ```

2. **Deploy to Netlify:**
   - Connect your GitHub repository to Netlify
   - Set build command: `cd frontend && pnpm install && pnpm run build`
   - Set publish directory: `frontend/build`
   - Set environment variables:
     ```
     REACT_APP_API_URL=https://leaderboard-backend-zmq3.onrender.com/api
     REACT_APP_SOCKET_URL=https://leaderboard-backend-zmq3.onrender.com
     ```

### **Backend Deployment (Render)**

1. **Prepare Backend:**
   ```bash
   cd backend
   pnpm install
   ```

2. **Deploy to Render:**
   - Connect your GitHub repository to Render
   - Set build command: `cd backend && pnpm install --no-frozen-lockfile`
   - Set start command: `cd backend && pnpm start`
   - Set environment variables:
     ```
     MONGO_URI=mongodb+srv://username:password@cluster.mongodb.net/leaderboard
     PORT=5000
     NODE_ENV=production
     ```

### **MongoDB Atlas Setup**

1. **Create MongoDB Atlas Account:**
   - Visit: https://www.mongodb.com/atlas
   - Sign up for free account
   - Create new cluster (M0 Free tier)

2. **Configure Database:**
   - Create database: `leaderboard`
   - Create collections: `users`, `claims`
   - Set up network access (allow all IPs: 0.0.0.0/0)
   - Create database user with read/write permissions

3. **Get Connection String:**
   ```
   mongodb+srv://username:password@cluster.mongodb.net/leaderboard?retryWrites=true&w=majority
   ```

## 🛠️ Local Development Setup

### **Prerequisites**
- Node.js v18+
- pnpm package manager
- MongoDB Atlas account

### **Frontend Setup**
```bash
cd frontend
pnpm install
pnpm start
```

### **Backend Setup**
```bash
cd backend
pnpm install
# Create .env file with MongoDB connection string
echo "MONGO_URI=mongodb+srv://username:password@cluster.mongodb.net/leaderboard" > .env
pnpm start
```

## 📁 Project Structure

```
task-1/
├── frontend/                 # React.js Frontend
│   ├── src/
│   │   ├── App.tsx          # Main application component
│   │   ├── index.css        # TailwindCSS styles
│   │   └── index.tsx        # Entry point
│   ├── package.json         # Frontend dependencies
│   └── tailwind.config.js   # TailwindCSS configuration
├── backend/                  # Node.js Backend
│   ├── src/
│   │   ├── models/          # MongoDB schemas
│   │   ├── routes/          # API endpoints
│   │   └── server.js        # Express server
│   ├── package.json         # Backend dependencies
│   └── .env                 # Environment variables
└── README.md                # Project documentation
```

## 🔧 API Endpoints

### **Users**
- `GET /api/users` - Get all users with rankings
- `POST /api/users` - Add new user
- `GET /api/users/leaderboard` - Get top 10 users

### **Claims**
- `POST /api/claims/claim` - Claim random points (1-10)
- `GET /api/claims/history` - Get claim history

## 🎨 Features

### **Frontend Features**
- ✅ Real-time leaderboard updates via Socket.IO
- ✅ User selection and point claiming
- ✅ Add new users functionality
- ✅ Responsive design with TailwindCSS
- ✅ Grand animations for top 3 users
- ✅ Confetti and particle effects
- ✅ Claim history display

### **Backend Features**
- ✅ RESTful API with Express.js
- ✅ MongoDB integration with Mongoose
- ✅ Real-time updates with Socket.IO
- ✅ User and claim data persistence
- ✅ Automatic ranking calculation
- ✅ Error handling and validation

## 🔒 Environment Variables

### **Frontend (.env)**
```
REACT_APP_API_URL=http://localhost:5000/api
REACT_APP_SOCKET_URL=http://localhost:5000
```

### **Backend (.env)**
```
MONGO_URI=mongodb+srv://username:password@cluster.mongodb.net/leaderboard
PORT=5000
NODE_ENV=development
```

## 📊 Database Schema

### **Users Collection**
```javascript
{
  _id: ObjectId,
  name: String,
  totalPoints: Number,
  createdAt: Date
}
```

### **Claims Collection**
```javascript
{
  _id: ObjectId,
  userId: ObjectId,
  userName: String,
  points: Number,
  claimedAt: Date
}
```

## 🚀 Performance Optimizations

- **Frontend**: React.memo, useCallback, lazy loading
- **Backend**: Connection pooling, indexing, caching
- **Database**: Proper indexing on totalPoints field
- **Real-time**: Efficient Socket.IO event handling

## 🔧 Troubleshooting

### **Common Issues**
1. **MongoDB Connection Error**: Check connection string and network access
2. **CORS Error**: Ensure backend CORS is configured for frontend domain
3. **Socket.IO Connection**: Verify Socket.IO URLs match between frontend and backend
4. **Build Errors**: Clear node_modules and reinstall dependencies

### **Debug Commands**
```bash
# Check MongoDB connection
mongo "mongodb+srv://cluster.mongodb.net/leaderboard"

# Test API endpoints
curl http://localhost:5000/api/users

# Check frontend build
cd frontend && pnpm run build
```

## 📞 Support

For technical support or questions:
- **GitHub Issues**: [https://github.com/yourusername/leaderboard-app/issues](https://github.com/yourusername/leaderboard-app/issues)
- **Email**: your.email@example.com

---

**Last Updated**: December 2024  
**Version**: 1.0.0  
**Status**: Production Ready ✅ 