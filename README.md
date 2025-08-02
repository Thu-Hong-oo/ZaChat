# Zalo Clone - Full Stack Messaging Application

A cross-platform messaging application with monolithic architecture, featuring real-time chat, video calling, and group management capabilities.

## ?? Key Features

### ?? Messaging System
- **1-1 Chat:** Text messages, emojis, multi-format file sharing
- **Group Chat:** Create groups, manage members, admin permissions
- **Real-time communication** with Socket.io
- **Message Features:**
  - File sharing (PDF, Word, Excel, PPT, ZIP, images, videos)
  - Forward messages between chats and groups
  - Recall messages (24-hour limit)
  - Delete messages with metadata tracking
  - Read receipts and notifications

### ?? Video Call System
- **1-1 Video Call** integrated with Twilio Video API
- **Group Video Call** supporting up to 50 participants
- **Call History** and detailed statistics
- **Real-time call notifications** and call quality monitoring

### ?? Social Features
- **Friend System:** Add friends, send/accept friend requests
- **User Profiles:** Manage avatars, personal information
- **Online/Offline Status** real-time updates
- **Group Management:** Create groups, add/remove members, role management

### ?? Authentication & Security
- Registration/login system with OTP verification
- JWT token authentication with refresh mechanism
- API security with middleware authentication
- Password encryption with bcryptjs

## ??? Technology Stack

### Frontend
- **Mobile App:** React Native with Expo SDK 52
- **Web App:** React.js 18 with Bootstrap 5
- **State Management:** Redux Toolkit
- **Real-time:** Socket.io Client
- **UI Components:** React Native Paper, Lucide React Icons

### Backend
- **Runtime:** Node.js with Express.js
- **Database:** AWS DynamoDB (NoSQL)
- **Real-time:** Socket.io Server
- **Authentication:** JWT, bcryptjs
- **File Upload:** Multer, Sharp (image processing)
- **Video Call:** Twilio API
- **Cloud Services:** AWS S3, AWS SNS
- **Caching:** Redis

### DevOps & Deployment
- **Containerization:** Docker
- **Web Deployment:** Netlify
- **Mobile Build:** Expo
- **Cloud Services:** AWS (DynamoDB, S3, SNS)

## ?? Project Structure

```
Zalo-Official/
+-- App/                    # React Native Mobile App
¦   +-- screens/           # 20+ screens
¦   +-- components/        # Reusable components
¦   +-- modules/          # API controllers
¦   +-- services/         # Socket, storage services
¦   +-- config/           # API configuration
+-- zalo-backend/         # Node.js Backend API
¦   +-- src/
¦   ¦   +-- modules/      # Feature modules
¦   ¦   +-- middleware/   # Auth, upload middleware
¦   ¦   +-- config/       # AWS, Redis config
¦   ¦   +-- services/     # Twilio service
¦   +-- scripts/          # Database setup
+-- zalo-web/             # React Web App
    +-- src/
    ¦   +-- components/   # 20+ components
    ¦   +-- redux/        # State management
    ¦   +-- services/     # API services
    +-- public/           # Static assets
```

## ?? Installation & Setup

### Prerequisites
- Node.js (v16+)
- npm or yarn
- Expo CLI
- Docker (optional)
- AWS Account (DynamoDB, S3, SNS)
- Twilio Account (Video API)

### Backend Setup
```bash
cd zalo-backend
npm install
cp .env.example .env
# Configure environment variables
npm run dev
```

### Mobile App Setup
```bash
cd App
npm install
expo start
```

### Web App Setup
```bash
cd zalo-web
npm install
npm start
```

## ?? Environment Configuration

### Backend (.env)
```env
PORT=3000
JWT_SECRET=your_jwt_secret
AWS_ACCESS_KEY_ID=your_aws_key
AWS_SECRET_ACCESS_KEY=your_aws_secret
AWS_REGION=us-east-1
DYNAMODB_TABLE_PREFIX=zalolite
REDIS_URL=redis://localhost:6379
TWILIO_ACCOUNT_SID=your_twilio_sid
TWILIO_AUTH_TOKEN=your_twilio_token
TWILIO_API_KEY=your_twilio_api_key
TWILIO_API_SECRET=your_twilio_api_secret
```

### Mobile App (.env)
```env
API_URL=http://localhost:3000
SOCKET_URL=http://localhost:3000
```

## ?? API Endpoints

### Authentication
- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User login
- `POST /api/auth/verify-otp` - OTP verification
- `POST /api/auth/refresh-token` - Refresh token

### Users
- `GET /api/users/profile` - Get user profile
- `PUT /api/users/profile` - Update profile
- `POST /api/users/avatar` - Upload avatar

### Friends
- `GET /api/friends` - Get friends list
- `POST /api/friends/request` - Send friend request
- `PUT /api/friends/accept` - Accept friend request
- `DELETE /api/friends/reject` - Reject friend request

### Groups
- `POST /api/groups` - Create group
- `GET /api/groups/:id` - Get group info
- `PUT /api/groups/:id` - Update group
- `POST /api/groups/:id/members` - Add member
- `DELETE /api/groups/:id/members/:memberId` - Remove member

### Chat
- `GET /api/chat/:conversationId/messages` - Get messages
- `POST /api/chat/:conversationId/messages` - Send message
- `DELETE /api/chat/:conversationId/messages/:messageId` - Delete message
- `PUT /api/chat/:conversationId/messages/:messageId/recall` - Recall message

### Video Call
- `POST /api/video-call/token` - Generate access token
- `POST /api/video-call/room` - Create video call room
- `GET /api/video-call/history` - Get call history

## ?? Real-time Events

### Socket.io Events
- `message:new` - New message
- `message:recall` - Message recall
- `message:delete` - Message deletion
- `typing:start` - Start typing
- `typing:stop` - Stop typing
- `user:online` - User online
- `user:offline` - User offline
- `call:offer` - Incoming call
- `call:answer` - Call answer
- `call:end` - Call end

## ?? Database Schema

### DynamoDB Tables
- **Users Table:** User information
- **Messages Table:** 1-1 messages
- **Group Messages Table:** Group messages
- **Groups Table:** Group information
- **Friends Table:** Friend relationships
- **Video Calls Table:** Call history

## ?? Deployment

### Backend (Docker)
```bash
cd zalo-backend
docker build -t zalo-backend .
docker run -p 3000:3000 zalo-backend
```

### Web App (Netlify)
```bash
cd zalo-web
npm run build
# Deploy build folder to Netlify
```

### Mobile App (Expo)
```bash
cd App
expo build:android
expo build:ios
```

## ?? Contributing

1. Fork the project
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## ?? License

This project is licensed under the MIT License - see the `LICENSE` file for details.

## ????? Author

**Your Name** - [GitHub](https://github.com/yourusername)

## ?? Acknowledgments

- [Expo](https://expo.dev/) - React Native development platform
- [Twilio](https://www.twilio.com/) - Video calling API
- [AWS](https://aws.amazon.com/) - Cloud services
- [Socket.io](https://socket.io/) - Real-time communication 