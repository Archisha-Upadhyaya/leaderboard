# leaderboard# 🏆 Real-Time Leaderboard System

A full-stack real-time leaderboard application built with React.js, Node.js, and MongoDB. Users can claim random points and see dynamic rankings with live updates.

![Leaderboard Demo](https://img.shields.io/badge/Status-Production%20Ready-brightgreen)
![React](https://img.shields.io/badge/React-18.2.0-blue)
![Node.js](https://img.shields.io/badge/Node.js-18+-green)
![MongoDB](https://img.shields.io/badge/MongoDB-Atlas-orange)

## 🌐 Live Demo

- **Frontend**: [https://quiet-alfajores-edafc7.netlify.app/](https://quiet-alfajores-edafc7.netlify.app/)
- **Backend API**: [https://leaderboard-backend-zmq3.onrender.com/](https://leaderboard-backend-zmq3.onrender.com/)
- **MongoDB Atlas**: [https://cloud.mongodb.com/v2/your-cluster-id](https://cloud.mongodb.com/v2/your-cluster-id)

## ✨ Features

### 🎯 Core Functionality
- **Real-time leaderboard** with live updates via Socket.IO
- **User point claiming** - Random points (1-10) per claim
- **Dynamic rankings** - Automatic position updates
- **User management** - Add new users from frontend
- **Claim history** - Track all point claims with timestamps

### 🎨 UI/UX Features
- **Responsive design** - Works on all devices
- **Grand animations** - Special effects for top 3 users
- **Confetti effects** - Celebrations for ranking changes
- **Modern UI** - Clean, professional design with TailwindCSS
- **Real-time indicators** - Live status and connection status

### 🔧 Technical Features
- **TypeScript** - Type-safe development
- **MongoDB integration** - Persistent data storage
- **RESTful API** - Clean, documented endpoints
- **Error handling** - Comprehensive error management
- **Performance optimized** - Efficient data handling

## 🚀 Quick Start

### Prerequisites
- Node.js 18+
- pnpm package manager
- MongoDB Atlas account

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/leaderboard-app.git
   cd leaderboard-app
   ```

2. **Setup Backend**
   ```bash
   cd backend
   pnpm install
   
   # Create .env file
   echo "MONGO_URI=mongodb+srv://username:password@cluster.mongodb.net/leaderboard" > .env
   
   # Start backend
   pnpm start
   ```

3. **Setup Frontend**
   ```bash
   cd frontend
   pnpm install
   
   # Start frontend
   pnpm start
   ```

4. **Access the application**
   - Frontend: http://localhost:3003
   - Backend API: http://localhost:5000

## 📁 Project Structure

```
leaderboard-app/
├── frontend/                 # React.js Frontend
│   ├── src/
│   │   ├── App.tsx          # Main application component
│   │   ├── index.css        # TailwindCSS styles
│   │   └── index.tsx        # Entry point
│   ├── public/
│   │   └── _redirects       # Netlify redirects
│   ├── package.json         # Frontend dependencies
│   └── tailwind.config.js   # TailwindCSS configuration
├── backend/                  # Node.js Backend
│   ├── src/
│   │   ├── models/          # MongoDB schemas
│   │   │   ├── User.js      # User model
│   │   │   └── Claim.js     # Claim model
│   │   ├── routes/          # API endpoints
│   │   │   ├── users.js     # User routes
│   │   │   └── claims.js    # Claim routes
│   │   └── server.js        # Express server
│   ├── package.json         # Backend dependencies
│   └── .env                 # Environment variables
├── DEPLOYMENT.md            # Deployment documentation
└── README.md               # This file
```

## 🔧 API Documentation

### Users Endpoints
- `GET /api/users` - Get all users with rankings
- `POST /api/users` - Add new user
- `GET /api/users/leaderboard` - Get top 10 users

### Claims Endpoints
- `POST /api/claims/claim` - Claim random points (1-10)
- `GET /api/claims/history` - Get claim history

### Example API Usage
```javascript
// Get all users
const response = await fetch('https://leaderboard-backend-zmq3.onrender.com/api/users');
const users = await response.json();

// Claim points for user
const claimResponse = await fetch('https://leaderboard-backend-zmq3.onrender.com/api/claims/claim', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({ userId: 'user_id_here' })
});
const claim = await claimResponse.json();
```

## 🗄️ Database Schema

### Users Collection
```javascript
{
  _id: ObjectId,
  name: String,
  totalPoints: Number,
  createdAt: Date
}
```

### Claims Collection
```javascript
{
  _id: ObjectId,
  userId: ObjectId,
  userName: String,
  points: Number,
  claimedAt: Date
}
```

## 🚀 Deployment

### Frontend (Netlify)
1. Connect GitHub repository to Netlify
2. Set build command: `cd frontend && pnpm install && pnpm run build`
3. Set publish directory: `frontend/build`
4. Add environment variables:
   ```
   REACT_APP_API_URL=https://leaderboard-backend-zmq3.onrender.com/api
   REACT_APP_SOCKET_URL=https://leaderboard-backend-zmq3.onrender.com
   ```

### Backend (Render)
1. Connect GitHub repository to Render
2. Set build command: `cd backend && pnpm install --no-frozen-lockfile`
3. Set start command: `cd backend && pnpm start`
4. Add environment variables:
   ```
   MONGO_URI=mongodb+srv://username:password@cluster.mongodb.net/leaderboard
   PORT=5000
   NODE_ENV=production
   ```

### MongoDB Atlas
1. Create free account at [MongoDB Atlas](https://www.mongodb.com/atlas)
2. Create new cluster (M0 Free tier)
3. Set up network access (allow all IPs: 0.0.0.0/0)
4. Create database user with read/write permissions
5. Get connection string and add to backend environment variables

## 🛠️ Technologies Used

### Frontend
- **React.js 18** - UI framework
- **TypeScript** - Type safety
- **TailwindCSS** - Styling
- **Socket.IO Client** - Real-time communication
- **Axios** - HTTP client

### Backend
- **Node.js** - Runtime environment
- **Express.js** - Web framework
- **MongoDB** - Database
- **Mongoose** - ODM for MongoDB
- **Socket.IO** - Real-time communication
- **CORS** - Cross-origin resource sharing

### Deployment
- **Netlify** - Frontend hosting
- **Render** - Backend hosting
- **MongoDB Atlas** - Cloud database

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 📞 Support

- **GitHub Issues**: [https://github.com/yourusername/leaderboard-app/issues](https://github.com/yourusername/leaderboard-app/issues)
- **Email**: your.email@example.com

## 🙏 Acknowledgments

- React.js team for the amazing framework
- MongoDB team for the excellent database
- TailwindCSS for the utility-first CSS framework
- Socket.IO for real-time communication capabilities

---

**Made with ❤️ by [Your Name]**

**Last Updated**: December 2024  
**Version**: 1.0.0
