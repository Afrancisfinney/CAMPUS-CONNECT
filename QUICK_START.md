# Campus Connect - Quick Start Guide

## 🎯 Project Overview

Campus Connect is a full-stack college ecosystem platform built with modern technologies:

- **Frontend**: React + Vite + Tailwind CSS + Redux
- **Backend**: Node.js + Express + MongoDB
- **Real-time**: Socket.io
- **Auth**: JWT + Email Verification
- **Deployment Ready**: Configured for Vercel/Netlify (Frontend) and Render/Railway (Backend)

## ⚡ Quick Start (5 minutes)

### Prerequisites
- Node.js 16+
- npm/yarn
- MongoDB (local or MongoDB Atlas)
- Git

### Step 1: Clone & Navigate
```bash
cd CONNECTIT
```

### Step 2: Backend Setup

```bash
cd backend

# Install dependencies
npm install

# Create .env file
cp .env.example .env

# Edit .env with your credentials
# Required keys:
# - MONGODB_URI (local: mongodb://localhost:27017/campusconnect)
# - JWT_SECRET (any random string for dev)
# - COLLEGE_EMAIL_DOMAIN (@iitm.ac.in,@college.edu)
# - SMTP details for email (gmail with app password)

# Start backend
npm run dev
```

Backend will run on: `http://localhost:5000`

### Step 3: Frontend Setup (New Terminal)

```bash
cd ../frontend

# Install dependencies
npm install

# Create .env file
cp .env.example .env

# .env should have:
# VITE_API_BASE_URL=http://localhost:5000/api
# VITE_SOCKET_URL=http://localhost:5000

# Start frontend
npm run dev
```

Frontend will run on: `http://localhost:5173`

### Step 4: Test the App

1. Open http://localhost:5173 in browser
2. Click "Get Started" → Sign Up
3. Use college email (e.g., `student@iitm.ac.in`)
4. Create account and verify email (check logs for verification link)
5. Login and explore features

## 📁 Project Structure at a Glance

```
CONNECTIT/
├── frontend/                    # React App (Vite)
│   ├── src/
│   │   ├── components/         # Reusable UI components
│   │   ├── pages/              # Full-page components
│   │   ├── layouts/            # Page layouts
│   │   ├── services/           # API calls
│   │   ├── redux/              # State management
│   │   ├── hooks/              # Custom React hooks
│   │   ├── utils/              # Helper functions
│   │   ├── App.jsx             # Main app
│   │   └── main.jsx            # Entry point
│   ├── package.json
│   └── vite.config.js
│
├── backend/                     # Express Server
│   ├── controllers/            # Business logic
│   ├── models/                 # MongoDB schemas
│   ├── routes/                 # API endpoints
│   ├── middleware/             # Auth, error handling
│   ├── utils/                  # Helper functions
│   ├── config/                 # Configuration
│   ├── server.js               # Entry point
│   └── package.json
│
├── README.md                   # Full documentation
├── DEVELOPMENT_GUIDE.md        # Development setup
├── API_DOCUMENTATION.md        # API reference
└── QUICK_START.md             # This file
```

## 🔐 Key Features Setup

### Authentication Flow
1. User signs up with college email (e.g., @iitm.ac.in)
2. Verification email sent automatically
3. User clicks verification link
4. Can now login with JWT token
5. Token stored in localStorage
6. All API requests include token in header

### Database Collections
- **Users**: Authentication, profiles, followers
- **Notes**: Study materials
- **Events**: Hackathons, workshops, webinars
- **Chats**: Real-time messaging
- **Others**: Tutors, Mentors, Comments, Reports, Notifications

### Security Features
- ✅ Password hashing (bcrypt)
- ✅ JWT authentication
- ✅ College email validation
- ✅ Rate limiting (100 requests/15 min)
- ✅ CORS protection
- ✅ Input validation with Zod
- ✅ Helmet for HTTP headers

## 🛠️ Common Tasks

### Add a New Feature

**Example: Adding "Like Note" feature**

1. **Backend**
   ```javascript
   // controllers/notesController.js
   export const likeNote = async (req, res) => {
     // Implementation
   };
   
   // routes/notesRoutes.js
   router.post('/:noteId/like', authenticate, likeNote);
   ```

2. **Frontend**
   ```javascript
   // services/services.js
   export const notesService = {
     likeNote: (noteId) => api.post(`/notes/${noteId}/like`),
   };
   
   // Component
   const handleLike = async () => {
     await notesService.likeNote(noteId);
   };
   ```

### Test an API Endpoint

**Using Thunder Client or Postman:**

```
POST http://localhost:5000/api/auth/login
Headers: Content-Type: application/json
Body: {
  "email": "student@iitm.ac.in",
  "password": "password123"
}
```

### Debug Issues

1. **Backend not starting?**
   - Ensure MongoDB is running
   - Check .env file
   - Look at terminal logs

2. **Frontend build errors?**
   - Clear node_modules: `rm -rf node_modules && npm install`
   - Check Node version: `node --version` (should be 16+)

3. **CORS errors?**
   - Check FRONTEND_URL in backend .env
   - Clear browser cache

## 🚀 Deployment Checklist

### Before Deployment
- [ ] Update environment variables
- [ ] Run `npm run build` (frontend)
- [ ] Test in production mode
- [ ] Update API base URL
- [ ] Setup MongoDB Atlas
- [ ] Configure email service
- [ ] Setup file upload (Cloudinary/Firebase)

### Deploy Frontend (Vercel)
```bash
cd frontend
npm run build
vercel deploy
```

### Deploy Backend (Render)
1. Push code to GitHub
2. Connect repo to Render
3. Set environment variables
4. Deploy

### Deploy Database (MongoDB Atlas)
1. Create cluster
2. Update MONGODB_URI
3. Whitelist IP addresses

## 📚 Key Files to Know

| File | Purpose |
|------|---------|
| `backend/server.js` | Express server entry point |
| `frontend/src/App.jsx` | React app root |
| `frontend/src/redux/store.js` | Redux configuration |
| `backend/models/*` | Database schemas |
| `backend/controllers/*` | Business logic |
| `.env.example` | Environment template |

## 🔑 Environment Variables

### Backend (.env)
```
NODE_ENV=development
PORT=5000
MONGODB_URI=mongodb://localhost:27017/campusconnect
JWT_SECRET=your_secret_key
COLLEGE_EMAIL_DOMAIN=@iitm.ac.in,@college.edu
FRONTEND_URL=http://localhost:5173
```

### Frontend (.env)
```
VITE_API_BASE_URL=http://localhost:5000/api
VITE_SOCKET_URL=http://localhost:5000
```

## 📖 Learn More

- [Full README](./README.md) - Complete documentation
- [Development Guide](./DEVELOPMENT_GUIDE.md) - Dev workflow
- [API Docs](./API_DOCUMENTATION.md) - All endpoints
- [React Docs](https://react.dev)
- [Express Docs](https://expressjs.com)

## 🎨 UI Components

Pre-built components available:
- `Button` - Styled button
- `Input` - Form input
- `Card` - Content card
- `Modal` - Modal dialog
- `Loading` - Loading spinner
- `Navbar` - Navigation bar
- `Footer` - Footer component

## 🤝 Project Phases

| Phase | Status | Features |
|-------|--------|----------|
| Phase 1 | ✅ Done | Setup & Configuration |
| Phase 2 | 📝 Todo | Full Authentication |
| Phase 3 | 📝 Todo | Core Features |
| Phase 4 | 📝 Todo | Advanced Features |
| Phase 5 | 📝 Todo | Admin & Security |
| Phase 6 | 📝 Todo | Deployment |

## 🆘 Need Help?

1. Check [DEVELOPMENT_GUIDE.md](./DEVELOPMENT_GUIDE.md)
2. Review [API_DOCUMENTATION.md](./API_DOCUMENTATION.md)
3. Check terminal logs for errors
4. Look at existing components for patterns

## 🎓 Learning Path

1. **Setup**: Get project running locally
2. **Explore**: Browse code structure
3. **Frontend**: Understand React components
4. **Backend**: Understand Express routes
5. **Database**: Learn MongoDB schemas
6. **Build**: Add your own features
7. **Deploy**: Push to production

---

**Ready to build?** Start with `npm run dev` in both terminals! 🚀

Happy coding! 💻
