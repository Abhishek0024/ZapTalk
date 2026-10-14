# ZapTalk

ZapTalk is a real-time, one-to-one chat application built with the MERN stack.
Users can register, choose an avatar, find other registered users, and exchange
messages. Socket.IO delivers messages to recipients who are online.

![ZapTalk login screen](./images/snappy_login.png)

![ZapTalk chat screen](./images/snappy.png)

## Features

- User registration and login.
- Avatar selection.
- Contact list of other registered users.
- One-to-one conversations with message history.
- Real-time delivery for online users.
- Logout from the chat sidebar.

## Technology

- **Frontend:** React, React Router, Styled Components, Axios, Socket.IO Client
- **Backend:** Node.js, Express, Socket.IO
- **Database:** MongoDB with Mongoose

## Requirements

- [Node.js and npm](https://nodejs.org/)
- [MongoDB](https://www.mongodb.com/docs/manual/administration/install-community/) running locally or a reachable MongoDB instance
- A MongoDB database user with read/write access if authentication is enabled

## Configure the environment

From the project root in PowerShell, create environment files from the examples:

```powershell
Copy-Item .\backend\.env.example .\backend\.env
Copy-Item .\frontend\.env.example .\frontend\.env
```

Edit `backend/.env` and set the backend port and MongoDB connection URI:

```env
PORT=5000
MONGO_URL="mongodb://localhost:27017/chat"
```

If MongoDB requires authentication, use the credentials for a database user
that can read and write to `chat`. For example:

```env
MONGO_URL="mongodb://USERNAME:PASSWORD@localhost:27017/chat?authSource=chat"
```

Replace `USERNAME` and `PASSWORD` with your MongoDB user's credentials. URL
encode special characters in credentials. Keep this URI private and do not
commit it.

The `frontend/.env` file should contain the browser's local storage key:

```env
REACT_APP_LOCALHOST_KEY="chat-app-current-user"
```

MongoDB creates the `chat` database and its collections automatically when the
application first writes data.

## Install and run

Open two PowerShell terminals in the project root. Keep MongoDB running.

In the first terminal, install and start the backend:

```powershell
cd .\backend
npm install
npm start
```

In the second terminal, install and start the frontend:

```powershell
cd .\frontend
npm install
npm start
```

Open [http://localhost:3000](http://localhost:3000). The backend API listens
on port `5000`. Leave both terminal processes running while using ZapTalk;
press `Ctrl+C` in each terminal to stop its server.

## Start chatting

1. Register an account and choose an avatar.
2. Register a second account in another browser profile or session.
3. Sign in and select the other user from the contacts list.
4. Send a message using the chat input.

The contact list includes all other registered users; there is no friend-request
or invitation workflow.

## Useful commands

Run these from the relevant project directory:

```powershell
# Frontend production build (from frontend/)
npm run build

# Frontend tests (from frontend/)
npm test

# Check backend availability
curl.exe http://localhost:5000/ping
```

## Project structure

```text
frontend/
  src/pages/        Login, registration, and chat pages
  src/components/   Chat, contacts, avatar, and shared UI components
  src/utils/        Frontend API route configuration
backend/
  controllers/      Authentication and message request handlers
  models/           Mongoose user and message models
  routes/           Authentication and message API routes
  index.js          Express, MongoDB, and Socket.IO server setup
images/             Screenshots used above
```
