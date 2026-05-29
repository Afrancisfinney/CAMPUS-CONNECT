# Campus Connect - API Documentation

## Base URL
```
http://localhost:5000/api
```

## Authentication
Include JWT token in Authorization header:
```
Authorization: Bearer <token>
```

---

## Auth Endpoints

### Register User
**POST** `/auth/signup`

Request:
```json
{
  "fullName": "John Doe",
  "email": "john@iitm.ac.in",
  "password": "password123",
  "department": "Computer Science",
  "year": 2
}
```

Response:
```json
{
  "message": "User registered. Please verify your email.",
  "user": {
    "id": "user_id",
    "email": "john@iitm.ac.in",
    "fullName": "John Doe"
  }
}
```

### Login
**POST** `/auth/login`

Request:
```json
{
  "email": "john@iitm.ac.in",
  "password": "password123"
}
```

Response:
```json
{
  "message": "Login successful",
  "token": "jwt_token",
  "user": {
    "id": "user_id",
    "email": "john@iitm.ac.in",
    "fullName": "John Doe",
    "role": "student"
  }
}
```

### Verify Email
**POST** `/auth/verify-email`

Request:
```json
{
  "token": "verification_token"
}
```

### Forgot Password
**POST** `/auth/forgot-password`

Request:
```json
{
  "email": "john@iitm.ac.in"
}
```

### Reset Password
**POST** `/auth/reset-password`

Request:
```json
{
  "token": "reset_token",
  "newPassword": "newpassword123"
}
```

---

## User Endpoints

### Get Profile
**GET** `/users/profile`

Authorization Required: Yes

Response:
```json
{
  "user": {
    "id": "user_id",
    "fullName": "John Doe",
    "email": "john@iitm.ac.in",
    "bio": "CS Student",
    "skills": ["JavaScript", "React"],
    "followers": [],
    "following": []
  }
}
```

### Update Profile
**PUT** `/users/profile`

Authorization Required: Yes

Request:
```json
{
  "fullName": "John Doe",
  "bio": "Full Stack Developer",
  "skills": ["JavaScript", "React", "Node.js"],
  "profilePhoto": "image_url"
}
```

### Search Users
**GET** `/users/search?q=john`

Response:
```json
{
  "users": [
    {
      "id": "user_id",
      "fullName": "John Doe",
      "profilePhoto": "url"
    }
  ]
}
```

### Follow User
**POST** `/users/:userId/follow`

Authorization Required: Yes

### Unfollow User
**DELETE** `/users/:userId/follow`

Authorization Required: Yes

---

## Notes Endpoints

### Get All Notes
**GET** `/notes?subject=DSA&semester=2&sortBy=trending`

Query Parameters:
- `subject` - Filter by subject
- `semester` - Filter by semester
- `department` - Filter by department
- `tags` - Filter by tags (comma-separated)
- `sortBy` - trending or recent

Response:
```json
{
  "notes": [
    {
      "id": "note_id",
      "title": "Data Structures",
      "subject": "DSA",
      "semester": 2,
      "fileUrl": "url",
      "uploadedBy": {
        "fullName": "John Doe",
        "profilePhoto": "url"
      },
      "likes": 10,
      "downloads": 5
    }
  ]
}
```

### Create Note
**POST** `/notes`

Authorization Required: Yes

Request:
```json
{
  "title": "Data Structures",
  "subject": "DSA",
  "semester": 2,
  "description": "Notes on arrays and linked lists",
  "fileUrl": "cloudinary_url",
  "fileType": "pdf",
  "tags": ["arrays", "structures"],
  "department": "CSE"
}
```

### Like Note
**POST** `/notes/:noteId/like`

Authorization Required: Yes

### Bookmark Note
**POST** `/notes/:noteId/bookmark`

Authorization Required: Yes

---

## Events Endpoints

### Get All Events
**GET** `/events?eventType=hackathon&upcoming=true`

Query Parameters:
- `eventType` - hackathon, workshop, webinar, etc.
- `upcoming` - true for upcoming events
- `tags` - Filter by tags

Response:
```json
{
  "events": [
    {
      "id": "event_id",
      "title": "Hackathon 2024",
      "description": "24-hour coding competition",
      "eventType": "hackathon",
      "startDate": "2024-06-01T10:00:00Z",
      "venue": "Campus A",
      "registrations": 50,
      "maxParticipants": 100
    }
  ]
}
```

### Create Event
**POST** `/events`

Authorization Required: Yes

Request:
```json
{
  "title": "Hackathon 2024",
  "description": "24-hour coding competition",
  "eventType": "hackathon",
  "startDate": "2024-06-01T10:00:00Z",
  "endDate": "2024-06-02T10:00:00Z",
  "venue": "Campus A",
  "posterUrl": "url",
  "tags": ["coding", "competition"],
  "maxParticipants": 100
}
```

### Register Event
**POST** `/events/:eventId/register`

Authorization Required: Yes

---

## Chat Endpoints

### Get All Chats
**GET** `/chats`

Authorization Required: Yes

### Create Chat
**POST** `/chats`

Authorization Required: Yes

Request:
```json
{
  "participantId": "user_id",
  "isGroupChat": false,
  "chatName": "Optional for group"
}
```

### Send Message
**POST** `/chats/:chatId/messages`

Authorization Required: Yes

Request:
```json
{
  "text": "Hello there!",
  "fileUrl": "optional_file_url"
}
```

---

## Error Responses

### 400 Bad Request
```json
{
  "message": "Only college emails are allowed"
}
```

### 401 Unauthorized
```json
{
  "message": "No token provided"
}
```

### 403 Forbidden
```json
{
  "message": "Unauthorized access"
}
```

### 404 Not Found
```json
{
  "message": "Resource not found"
}
```

### 500 Server Error
```json
{
  "message": "Internal server error",
  "error": "error details"
}
```

---

## Status Codes

- `200` - OK
- `201` - Created
- `400` - Bad Request
- `401` - Unauthorized
- `403` - Forbidden
- `404` - Not Found
- `500` - Server Error

---

## Rate Limiting

API is rate limited to 100 requests per 15 minutes per IP.

Response header:
```
X-RateLimit-Limit: 100
X-RateLimit-Remaining: 99
X-RateLimit-Reset: 1234567890
```
