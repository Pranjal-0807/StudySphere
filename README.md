# StudySphere 🌐📚

A comprehensive ed-tech platform built with the MERN stack, enabling seamless creation, consumption, and rating of educational content.

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [System Architecture](#system-architecture)
- [Tech Stack](#tech-stack)
- [Installation](#installation)
- [API Documentation](#api-documentation)
- [Database Schema](#database-schema)
- [Deployment](#deployment)
- [Testing](#testing)
- [Future Enhancements](#future-enhancements)
- [Contributing](#contributing)
- [License](#license)

## 🎯 Overview

StudySphere is a fully functional ed-tech platform that bridges the gap between instructors and learners worldwide. Built using the MERN stack (MongoDB, Express.js, React.js, Node.js), StudySphere provides:

- **For Students**: An interactive and engaging learning experience with easy access to quality educational content
- **For Instructors**: A platform to showcase expertise, create courses, and connect with a global audience of learners
- **For Administrators**: Comprehensive management tools for overseeing platform operations

## ✨ Features

### 🎓 Student Features
- **User Authentication**: Secure signup/login with OTP verification
- **Course Discovery**: Browse and search through available courses
- **Wishlist Management**: Save courses for later purchase
- **Secure Checkout**: Complete course purchases with integrated payment processing
- **Interactive Learning**: Access course content including videos and materials
- **Profile Management**: Update personal information and track learning progress
- **Course Rating**: Rate and review completed courses

### 👩‍🏫 Instructor Features
- **Instructor Dashboard**: Overview of courses, ratings, and performance metrics
- **Course Management**: Create, update, and delete courses with rich content
- **Analytics & Insights**: Detailed metrics on course performance and student engagement
- **Profile Management**: Manage instructor profile and credentials
- **Content Upload**: Support for various media types with cloud storage

### 🔧 Admin Features (Future Scope)
- **Platform Overview**: Dashboard with comprehensive platform statistics
- **User Management**: Manage students and instructors
- **Course Moderation**: Review and approve course content
- **Analytics**: Platform-wide insights and reporting

## 🏗️ System Architecture

StudySphere follows a client-server architecture with three main components:

```
┌─────────────────┐    HTTP/REST API    ┌─────────────────┐
│                 │◄──────────────────►│                 │
│   Frontend      │                    │   Backend       │
│   (React.js)    │                    │   (Node.js)     │
│                 │                    │                 │
└─────────────────┘                    └─────────────────┘
                                                │
                                                │
                                                ▼
                                       ┌─────────────────┐
                                       │                 │
                                       │   Database      │
                                       │   (MongoDB)     │
                                       │                 │
                                       └─────────────────┘
```

### Frontend
- Built with **React.js** for dynamic and responsive user interfaces
- **Redux** for state management
- **Tailwind CSS** for modern, responsive styling
- RESTful API integration for backend communication

### Backend
- **Node.js** with **Express.js** framework
- RESTful API architecture
- JWT-based authentication
- Cloudinary integration for media management
- Razorpay integration for payment processing

### Database
- **MongoDB** for flexible, scalable data storage
- **Mongoose** ODM for data modeling
- Support for unstructured and semi-structured data

## 🛠️ Tech Stack

### Frontend
- **React.js** - UI library
- **Redux** - State management
- **React Router** - Navigation
- **Tailwind CSS** - Styling
- **Axios** - HTTP client

### Backend
- **Node.js** - Runtime environment
- **Express.js** - Web framework
- **MongoDB** - Database
- **Mongoose** - ODM
- **JWT** - Authentication
- **Bcrypt** - Password hashing
- **Cloudinary** - Media management
- **Razorpay** - Payment processing

## 🚀 Installation

### Prerequisites
- Node.js (v14 or higher)
- MongoDB
- npm or yarn

### Backend Setup

1. Clone the repository
```bash
git clone https://github.com/yourusername/studysphere.git
cd studysphere
```

2. Install backend dependencies
```bash
cd server
npm install
```

3. Create environment variables
```bash
cp .env.example .env
```

Configure the following variables in `.env`:
```env
MONGODB_URI=mongodb://localhost:27017/studysphere
JWT_SECRET=your_jwt_secret
CLOUDINARY_CLOUD_NAME=your_cloudinary_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret
RAZORPAY_KEY_ID=your_razorpay_key
RAZORPAY_SECRET=your_razorpay_secret
MAIL_HOST=smtp.gmail.com
MAIL_USER=your_email
MAIL_PASS=your_password
```

4. Start the backend server
```bash
npm run dev
```

### Frontend Setup

1. Install frontend dependencies
```bash
cd client
npm install
```

2. Start the frontend development server
```bash
npm start
```

The application will be available at `http://localhost:3000`

## 📡 API Documentation

### Authentication Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/auth/signup` | Create a new user account |
| POST | `/api/auth/login` | User login |
| POST | `/api/auth/verify-otp` | Verify OTP |
| POST | `/api/auth/forgot-password` | Send password reset email |

### Course Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/courses` | Get all courses |
| GET | `/api/courses/:id` | Get specific course |
| POST | `/api/courses` | Create new course |
| PUT | `/api/courses/:id` | Update course |
| DELETE | `/api/courses/:id` | Delete course |
| POST | `/api/courses/:id/rate` | Rate a course |

### Sample API Response

```json
{
  "success": true,
  "data": {
    "courses": [
      {
        "_id": "64a7b8c9d1234567890abcde",
        "title": "Introduction to React.js",
        "description": "Learn the fundamentals of React.js",
        "instructor": "John Doe",
        "price": 99.99,
        "rating": 4.5,
        "studentsEnrolled": 1250
      }
    ]
  },
  "message": "Courses fetched successfully"
}
```

## 🗄️ Database Schema

### User Schema
```javascript
{
  firstName: String,
  lastName: String,
  email: String (unique),
  password: String (hashed),
  accountType: String (Student/Instructor/Admin),
  courses: [ObjectId],
  image: String,
  courseProgress: [ObjectId]
}
```

### Course Schema
```javascript
{
  courseName: String,
  courseDescription: String,
  instructor: ObjectId,
  whatYouWillLearn: String,
  courseContent: [ObjectId],
  ratingAndReviews: [ObjectId],
  price: Number,
  thumbnail: String,
  studentsEnrolled: [ObjectId]
}
```

## 🚀 Deployment

### Production Environment Setup

1. **Backend Deployment** (Node.js/Express)
   - Deploy to platforms like Heroku, Railway, or DigitalOcean
   - Configure environment variables
   - Set up MongoDB Atlas for database

2. **Frontend Deployment** (React.js)
   - Build the production version: `npm run build`
   - Deploy to Netlify, Vercel, or similar platforms
   - Configure environment variables for API endpoints

3. **Database Setup**
   - MongoDB Atlas for cloud database
   - Configure connection strings and security settings

## 🧪 Testing

### Testing Strategy
- **Unit Testing**: Jest for component and function testing
- **Integration Testing**: API endpoint testing with Supertest
- **End-to-End Testing**: Cypress for user flow testing

### Running Tests
```bash
# Backend tests
cd server
npm test

# Frontend tests
cd client
npm test
```

## 🔮 Future Enhancements

### Phase 1 (Short-term)
- [ ] Mobile application development
- [ ] Advanced search and filtering
- [ ] Course completion certificates
- [ ] Discussion forums for courses

### Phase 2 (Medium-term)
- [ ] Live streaming capabilities
- [ ] AI-powered course recommendations
- [ ] Multi-language support
- [ ] Advanced analytics dashboard

### Phase 3 (Long-term)
- [ ] AR/VR integration for immersive learning
- [ ] Blockchain-based certification
- [ ] Marketplace for educational resources
- [ ] Advanced proctoring system

## 🤝 Contributing

We welcome contributions to StudySphere! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Development Guidelines
- Follow existing code style and conventions
- Write comprehensive tests for new features
- Update documentation as needed
- Ensure all tests pass before submitting PR

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 📞 Support

For support and queries:
- 📧 Email: support@studysphere.com
- 💬 Discord: [StudySphere Community](https://discord.gg/studysphere)
- 📚 Documentation: [docs.studysphere.com](https://docs.studysphere.com)

---

**Built with ❤️ by the StudySphere Team**

⭐ If you found this project helpful, please give it a star on GitHub!
