# Development Guide

## Getting Started

This guide will help you set up and develop Campus Connect locally.

## Prerequisites

- Node.js 16+
- npm or yarn
- MongoDB
- Git

## Local Setup

### 1. Clone Repository
```bash
git clone <repo-url>
cd CONNECTIT
```

### 2. Install Dependencies

**Frontend:**
```bash
cd frontend
npm install
```

**Backend:**
```bash
cd ../backend
npm install
```

### 3. Environment Setup

**Frontend (.env):**
```
VITE_API_BASE_URL=http://localhost:5000/api
VITE_SOCKET_URL=http://localhost:5000
VITE_CLOUDINARY_CLOUD_NAME=your_cloudinary_name
```

**Backend (.env):**
```
NODE_ENV=development
PORT=5000
MONGODB_URI=mongodb://localhost:27017/campusconnect
JWT_SECRET=dev_secret_key_change_in_production
JWT_EXPIRE=7d
COLLEGE_EMAIL_DOMAIN=@iitm.ac.in,@college.edu,@student.edu
SMTP_SERVICE=gmail
SMTP_USER=your_email@gmail.com
SMTP_PASSWORD=your_app_password
CLOUDINARY_CLOUD_NAME=your_name
CLOUDINARY_API_KEY=your_key
CLOUDINARY_API_SECRET=your_secret
FRONTEND_URL=http://localhost:5173
```

### 4. Start Development

**Terminal 1 - Backend:**
```bash
cd backend
npm run dev
```
Server runs on http://localhost:5000

**Terminal 2 - Frontend:**
```bash
cd frontend
npm run dev
```
App runs on http://localhost:5173

## Project Structure

```
CONNECTIT/
├── frontend/              # React + Vite frontend
│   ├── src/
│   │   ├── components/   # Reusable components
│   │   ├── pages/        # Page components
│   │   ├── layouts/      # Layout components
│   │   ├── hooks/        # Custom hooks
│   │   ├── services/     # API services
│   │   ├── redux/        # State management
│   │   ├── utils/        # Utility functions
│   │   └── App.jsx       # Root component
│   └── package.json
│
├── backend/              # Express + MongoDB backend
│   ├── controllers/      # Request handlers
│   ├── models/          # Mongoose schemas
│   ├── routes/          # API routes
│   ├── middleware/      # Custom middleware
│   ├── services/        # Business logic
│   ├── utils/           # Utility functions
│   ├── validations/     # Input validation
│   ├── server.js        # Entry point
│   └── package.json
│
└── README.md
```

## Development Workflow

### Adding a Feature

1. **Create Backend Endpoint**
   - Add route in `backend/routes/`
   - Create controller in `backend/controllers/`
   - Add validation in `backend/validations/`

2. **Create Frontend UI**
   - Add component in `backend/src/components/`
   - Create page if needed in `backend/src/pages/`

3. **Connect to API**
   - Add service in `frontend/src/services/services.js`
   - Use Redux or hooks for state management
   - Handle errors with try-catch

4. **Test**
   - Test backend with Postman/Thunder Client
   - Test frontend in browser
   - Check console for errors

### Coding Standards

- Use ES6+ syntax
- Keep functions small and focused
- Add comments for complex logic
- Use meaningful variable names
- Follow existing code patterns

### Database

#### MongoDB Connection
```javascript
// Automatic via server.js
mongoose.connect(process.env.MONGODB_URI)
```

#### Creating a Model
```javascript
// backend/models/YourModel.js
import mongoose from 'mongoose';

const schema = new mongoose.Schema({
  name: String,
  // ... fields
}, { timestamps: true });

export default mongoose.model('YourModel', schema);
```

### Authentication

#### Login Flow
1. User submits email + password
2. Backend validates college email domain
3. Password verified with bcrypt
4. JWT token generated
5. Token stored in localStorage
6. Token sent with each request

#### Protected Routes
```javascript
// Frontend
<Route path="/dashboard" element={
  <ProtectedRoute isAuthenticated={isAuthenticated}>
    <Dashboard />
  </ProtectedRoute>
} />

// Backend
router.post('/api/notes', authenticate, notesController.createNote);
```

## API Development

### Creating an API Endpoint

1. **Backend Route**
```javascript
// routes/notesRoutes.js
router.post('/', authenticate, notesController.createNote);
```

2. **Controller**
```javascript
// controllers/notesController.js
export const createNote = async (req, res) => {
  try {
    // Logic here
    res.status(201).json({ message: 'Success', data });
  } catch (error) {
    res.status(500).json({ message: 'Error', error });
  }
};
```

3. **Frontend Service**
```javascript
// services/services.js
export const notesService = {
  createNote: (noteData) => api.post('/notes', noteData),
};
```

4. **Frontend Component**
```javascript
// pages/NotesPage.jsx
import { notesService } from '../services/services.js';

const handleCreate = async (noteData) => {
  try {
    const response = await notesService.createNote(noteData);
    // Handle success
  } catch (error) {
    // Handle error
  }
};
```

## Debugging

### Frontend Debug
- Use React Developer Tools
- Check browser console
- Use `console.log()` strategically
- Check Redux DevTools

### Backend Debug
- Check terminal logs
- Use `console.log()` in controllers
- Use Postman to test APIs
- Check MongoDB collections

## Testing

### Manual Testing
1. Test user signup flow
2. Verify email functionality
3. Test login/logout
4. Test CRUD operations
5. Test real-time features

### Browser Testing
- Chrome DevTools
- Test responsive design
- Check dark mode
- Verify animations

## Common Issues

### Port Already in Use
```bash
# Find process using port 5000
lsof -i :5000
kill -9 <PID>
```

### MongoDB Connection Error
- Ensure MongoDB is running
- Check connection string
- Verify network access

### CORS Error
- Check backend CORS configuration
- Verify frontend URL in .env
- Clear browser cache

## Deployment Checklist

- [ ] Update environment variables
- [ ] Run build commands
- [ ] Test in production mode
- [ ] Set up CI/CD pipeline
- [ ] Configure database backups
- [ ] Set up monitoring
- [ ] Document API endpoints
- [ ] Write deployment guide

## Resources

- [React Documentation](https://react.dev)
- [Express.js Documentation](https://expressjs.com)
- [MongoDB Documentation](https://docs.mongodb.com)
- [Tailwind CSS](https://tailwindcss.com)
- [Redux Toolkit](https://redux-toolkit.js.org)

## Support

For issues or questions, create an issue in the repository or reach out to the development team.
