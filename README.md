# Real-Time Chat Application

A full-stack real-time chat application built with React, Node.js, Express, and Socket.io with MongoDB for persistence.

## Features

✅ **User Authentication** - JWT-based registration and login  
✅ **One-to-One Chat** - Direct messaging between users  
✅ **Real-Time Messaging** - Instant message delivery via Socket.io  
✅ **Typing Indicator** - See when users are typing  
✅ **User Status** - Online/Offline/Away status tracking  
✅ **Message History** - Persistent message storage in MongoDB  
✅ **Responsive UI** - Beautiful and intuitive interface  

## Tech Stack

### Backend
- Node.js & Express.js
- Socket.io for real-time communication
- MongoDB with Mongoose
- JWT for authentication
- Bcryptjs for password hashing
- CORS for cross-origin requests

### Frontend
- React 18
- React Router for navigation
- Socket.io Client for real-time updates
- Axios for API calls
- Lucide React for icons
- Tailwind CSS for styling
- Vite for fast development

## Prerequisites

- Node.js (v16 or higher)
- MongoDB (local or cloud instance)
- npm or yarn

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/SujanTheMagician/real-time-chat-app.git
cd real-time-chat-app
```

### 2. Backend Setup

```bash
cd server
npm install
```

Create a `.env` file in the server directory:

```env
PORT=5000
MONGODB_URI=mongodb://localhost:27017/realtime-chat
JWT_SECRET=your-super-secret-key-change-in-production
CLIENT_URL=http://localhost:5173
```

Start the server:

```bash
npm run dev
```

The server will run on `http://localhost:5000`

### 3. Frontend Setup

```bash
cd client
npm install
```

Create a `.env` file in the client directory:

```env
VITE_API_URL=http://localhost:5000/api
VITE_SOCKET_URL=http://localhost:5000
```

Start the development server:

```bash
npm run dev
```

The client will run on `http://localhost:5173`

## Usage

1. **Register**: Create a new account with username, email, and password
2. **Login**: Sign in with your credentials
3. **Select User**: Choose a user from the list to start chatting
4. **Send Message**: Type your message and hit send
5. **Typing Indicator**: You'll see when the other user is typing
6. **Real-Time Updates**: Messages appear instantly for both users

## API Endpoints

### Authentication
- `POST /api/auth/register` - Register a new user
- `POST /api/auth/login` - Login user

### Users
- `GET /api/users` - Get all users (authenticated)
- `GET /api/users/chat-history/:userId` - Get chat history with a user
- `PUT /api/users/mark-read/:senderId` - Mark messages as read

## Socket.io Events

### Client to Server
- `user-online` - User comes online
- `send-message` - Send a message to another user
- `typing` - Emit typing status
- `user-away` - Set user as away

### Server to Client
- `receive-message` - Receive a message
- `user-typing` - User is typing
- `user-status-change` - User status changed
- `message-sent` - Message sent confirmation
- `error` - Error occurred

## Project Structure

```
real-time-chat-app/
├── server/
│   ├── config/
│   │   └── db.js
│   ├── models/
│   │   ├── User.js
│   │   └── Message.js
│   ├── routes/
│   │   ├── auth.js
│   │   └── users.js
│   ├── middleware/
│   │   └── auth.js
│   ├── socket/
│   │   └── socketHandler.js
│   ├── server.js
│   ├── package.json
│   └── .env
├── client/
│   ├── src/
│   │   ├── components/
│   │   │   ├── Auth/
│   │   │   │   ├── Login.jsx
│   │   │   │   └── Register.jsx
│   │   │   └── Chat/
│   │   │       ├── ChatWindow.jsx
│   │   │       └── UserList.jsx
│   │   ├── pages/
│   │   │   └── ChatPage.jsx
│   │   ├── services/
│   │   │   ├── api.js
│   │   │   └── socket.js
│   │   ├── hooks/
│   │   │   └── useAuth.js
│   │   ├── App.jsx
│   │   ├── main.jsx
│   │   └── index.css
│   ├── vite.config.js
│   ├── package.json
│   └── .env
├── .gitignore
└── README.md
```

## Database Models

### User Schema
```javascript
{
  username: String (unique),
  email: String (unique),
  password: String (hashed),
  avatar: String,
  status: String (online/offline/away),
  createdAt: Date
}
```

### Message Schema
```javascript
{
  sender: ObjectId (ref: User),
  receiver: ObjectId (ref: User),
  content: String,
  read: Boolean,
  createdAt: Date
}
```

## Future Enhancements

- [ ] Group chat functionality
- [ ] File sharing and media uploads
- [ ] Message reactions and emojis
- [ ] Read receipts
- [ ] User profile customization
- [ ] Search functionality
- [ ] Message notifications
- [ ] Message editing and deletion
- [ ] User blocking
- [ ] Message encryption

## Troubleshooting

### MongoDB Connection Issues
- Ensure MongoDB is running locally or provide correct cloud URI
- Check MONGODB_URI in .env file

### Socket Connection Issues
- Verify VITE_SOCKET_URL matches backend port
- Check CORS configuration in server.js
- Ensure firewall allows connections

### Authentication Issues
- Clear browser cache and local storage
- Check JWT_SECRET is consistent
- Verify token storage in localStorage

## License

MIT

## Support

For issues and questions, please create an issue in the repository.