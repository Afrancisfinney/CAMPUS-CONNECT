# Campus Connect - Full-Stack College Ecosystem Platform

A modern, secure, scalable, and responsive full-stack web application for college students to collaborate, share resources, and build networks.

## 🌟 Features

### Core Features
- **📝 Secure Authentication** - College email verification, JWT tokens, password reset, OTP verification
- **🎓 Notes Sharing** - Upload and share study materials (PDF, DOCX, PPT, Images)
- **🤝 Networking** - Connect with seniors, juniors, and peers
- **👨‍🏫 Tutoring System** - Find and book tutors, track sessions, ratings and reviews
- **🎉 Event Management** - Create, register for, and manage hackathons, workshops, webinars
- **💬 Real-Time Chat** - Socket.io powered messaging with real-time notifications
- **🔍 Advanced Search** - Global search with smart recommendations
- **👨‍💼 Role-Based Dashboards** - Student, Senior Mentor, Tutor, Event Coordinator, Admin
- **📊 Admin Panel** - Moderation, user management, analytics
- **🌓 Dark/Light Mode** - Modern UI with theme toggle
- **📱 Fully Responsive** - Mobile-first design using Tailwind CSS

## 🛠️ Tech Stack

### Frontend
- **React 18** - UI library
- **Vite** - Build tool
- **Tailwind CSS** - Styling
- **Framer Motion** - Animations
- **Redux Toolkit** - State management
- **Axios** - HTTP client
- **React Router** - Routing
- **Socket.io Client** - Real-time communication

### Backend
- **Node.js** - Runtime
- **Express.js** - Web framework
- **MongoDB** - Database
- **Mongoose** - ODM
- **JWT** - Authentication
- **Bcryptjs** - Password hashing
- **Zod** - Validation
- **Socket.io** - Real-time events
- **Nodemailer** - Email service
- **Multer** - File uploads
- **Helmet** - Security
- **CORS** - Cross-origin requests
- **Express Rate Limit** - Rate limiting

## 📋 Prerequisites

- Node.js (v16 or higher)
- npm or yarn
- MongoDB (local or Atlas)
- Git

## 🚀 Installation

### 1. Clone the Repository
```bash
git clone <repository-url>
cd CONNECTIT
```

### 2. Frontend Setup

```bash
cd frontend

# Install dependencies
npm install

# Create .env file
cp .env.example .env

# Update environment variables in .env
# VITE_API_BASE_URL=http://localhost:5000/api
# VITE_SOCKET_URL=http://localhost:5000

# Start development server
npm run dev
```

### 3. Backend Setup

```bash
cd ../backend

# Install dependencies
npm install

# Create .env file
cp .env.example .env

# Update environment variables in .env
# NODE_ENV=development
# PORT=5000
# MONGODB_URI=mongodb://localhost:27017/campusconnect
# JWT_SECRET=your_secret_key
# COLLEGE_EMAIL_DOMAIN=@iitm.ac.in,@college.edu
# SMTP settings for email
# Cloudinary credentials

# Start development server
npm run dev
```

## 📁 Project Structure

```
CONNECTIT/
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   │   ├── auth/
│   │   │   ├── common/
│   │   │   └── dashboard/
│   │   ├── pages/
│   │   ├── layouts/
│   │   ├── hooks/
│   │   ├── services/
│   │   ├── redux/
│   │   │   └── slices/
│   │   ├── utils/
│   │   ├── assets/
│   │   ├── App.jsx
│   │   └── main.jsx
│   ├── package.json
│   ├── vite.config.js
│   ├── tailwind.config.js
│   └── .env.example
│
├── backend/
│   ├── controllers/
│   ├── models/
│   ├── routes/
│   ├── middleware/
│   ├── services/
│   ├── utils/
│   ├── validations/
│   ├── config/
│   ├── uploads/
│   ├── server.js
│   ├── package.json
│   └── .env.example
│
└── README.md
```

## 📚 Database Schema

### Users Collection
- fullName, email, password (hashed)
- role (student, senior_mentor, tutor, event_coordinator, admin)
- department, year, bio, skills
- profilePhoto, isVerified, isBanned
- followers, following

### Notes Collection
- title, description, subject, semester
- department, tags, fileUrl, fileType
- uploadedBy, likes, bookmarks, downloads
- comments, isApproved, reports

### Events Collection
- title, description, eventType
- startDate, endDate, venue
- organizer, registrations, teams
- posterUrl, tags, discussionForum

### Chat Collection
- participants, isGroupChat, chatName
- messages (with sender, text, fileUrl, timestamp)

### Tutors Collection
- userId, subjects, expertise
- availability, hourlyRate
- ratings, reviews, isVerified

### Mentors Collection
- userId, specialties, availability
- mentees, reviews

## 🔐 Security Features

- ✅ College email validation
- ✅ Password hashing with bcrypt
- ✅ JWT token authentication
- ✅ Email verification
- ✅ OTP verification
- ✅ Rate limiting
- ✅ CORS protection
- ✅ Input validation with Zod
- ✅ Helmet for HTTP headers
- ✅ Secure file upload validation
- ✅ XSS prevention
- ✅ CSRF protection

## 🔄 Development Workflow

### Phase 1: Setup ✅
- Initialize projects
- Configure databases
- Setup routing

### Phase 2: Authentication
- Implement signup/login
- Email verification
- Password reset
- JWT tokens
- Role-based access

### Phase 3: Core Features
- Notes sharing module
- User profiles
- Event management
- Messaging system

### Phase 4: Advanced Features
- Real-time chat
- Recommendations
- Tutor system
- Notifications

### Phase 5: Admin & Security
- Admin dashboard
- Moderation tools
- Analytics
- Security hardening

### Phase 6: Deployment
- Frontend deployment (Vercel/Netlify)
- Backend deployment (Render/Railway)
- Database setup (MongoDB Atlas)
- Testing and optimization

## 🚢 Deployment

### Frontend (Vercel)
```bash
npm run build
vercel deploy
```

### Backend (Render/Railway)
Push to GitHub and connect with Render/Railway

### Database (MongoDB Atlas)
- Create account at mongodb.com/cloud
- Create cluster
- Update MongoDB URI in backend .env

## 📝 API Endpoints

### Authentication
- `POST /api/auth/signup` - Register user
- `POST /api/auth/login` - Login user
- `POST /api/auth/verify-email` - Verify email
- `POST /api/auth/forgot-password` - Forgot password
- `POST /api/auth/reset-password` - Reset password

### Users
- `GET /api/users/profile` - Get user profile
- `PUT /api/users/profile` - Update profile
- `GET /api/users/search?q=query` - Search users

### Notes
- `GET /api/notes` - Get all notes
- `POST /api/notes` - Create note
- `GET /api/notes/:id` - Get note
- `PUT /api/notes/:id` - Update note
- `DELETE /api/notes/:id` - Delete note

### Events
- `GET /api/events` - Get all events
- `POST /api/events` - Create event
- `GET /api/events/:id` - Get event
- `POST /api/events/:id/register` - Register for event

## 🎨 UI/UX Design

The application features:
- Modern glassmorphism design
- Smooth animations with Framer Motion
- Responsive grid layouts
- Professional color palette (Sky & Purple gradients)
- Dark/Light mode support
- Clean typography
- Interactive components
- Intuitive navigation

## 🤝 Contributing

1. Fork the repository
2. Create feature branch (`git checkout -b feature/feature-name`)
3. Commit changes (`git commit -m 'Add feature'`)
4. Push to branch (`git push origin feature/feature-name`)
5. Open Pull Request

## 📄 License

This project is licensed under the MIT License - see LICENSE file for details.

## 📧 Contact & Support

For questions, feedback, or support, please reach out to the development team.

## 🙏 Acknowledgments

Inspired by platforms like LinkedIn, Discord, GitHub, Notion, and Microsoft Teams.

---

**Happy Coding! Build something amazing with Campus Connect!** 🚀
