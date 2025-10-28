# 🧊 CubeMate - 3D Rubik's Cube Solving Companion

> An intelligent web-based 3D Rubik's Cube solver and learning platform

![Project Status](https://img.shields.io/badge/Status-In%20Development-yellow)
![Team Size](https://img.shields.io/badge/Team-4%20Members-blue)
![Semester](https://img.shields.io/badge/Semester-3%20End%20Project-green)

## 📖 Overview

CubeMate is an advanced web application that combines 3D visualization, intelligent solving algorithms, and educational features to make Rubik's cube solving accessible and engaging for everyone. Whether you're a beginner learning your first solve or an enthusiast exploring advanced methods, CubeMate provides the tools and guidance you need.

## ✨ Key Features

- 🎨 **Interactive 3D Cube**: Realistic cube visualization with smooth animations
- 🧠 **Intelligent Solver**: Kociemba algorithm for optimal solutions
- 📚 **Learning Hub**: Step-by-step tutorials and pattern library
- 📊 **Progress Tracking**: Personal statistics and achievement system
- 🏆 **Community Features**: Challenges, leaderboards, and competitions
- 📱 **Mobile Friendly**: Responsive design with PWA support

## 🛠️ Tech Stack

### Frontend
- React.js with JavaScript (team expertise)
- Three.js with react-three-fiber (learnable)
- Tailwind CSS (team knows)
- React Router v6

### Backend
- Node.js with Express.js (team expertise)
- Supabase (PostgreSQL) + Prisma ORM (team knows)
- JWT Authentication with Supabase Auth
- Python with kociemba library for cube solving

### Deployment
- Frontend: Vercel (team knows)
- Backend: Vercel Serverless Functions
- Database: Supabase (team expertise)

## 📁 Project Structure

```
cubemate/
├── frontend/                 # React.js application
│   ├── src/
│   │   ├── components/      # Reusable UI components
│   │   ├── pages/          # Application pages
│   │   ├── hooks/          # Custom React hooks
│   │   ├── utils/          # Utility functions
│   │   └── store/          # State management
│   └── public/             # Static assets
├── backend/                 # Server application
│   ├── src/
│   │   ├── routes/         # API endpoints
│   │   ├── models/         # Database models
│   │   ├── middleware/     # Custom middleware
│   │   └── utils/          # Server utilities
│   └── tests/              # Backend tests
├── solver/                  # Cube solving algorithms
│   ├── kociemba/           # Kociemba implementation
│   └── computer_vision/    # OpenCV color detection
├── docs/                   # Documentation
└── deployment/             # Deployment configurations
```

## 🚀 Getting Started

### Prerequisites
- Node.js (v16+)
- Python (v3.8+)
- Git and GitHub account

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/ashvin2005/cubemate.git
   cd cubemate
   ```

2. **Install all dependencies**
   ```bash
   npm run install:all
   ```

3. **Environment Setup**
   ```bash
   # Copy environment template
   cp .env.example .env
   # Add your Supabase credentials
   ```

4. **Start development**
   ```bash
   npm run dev
   ```

## 👥 Team Members

| Name |
|------|
| Ashvin Tiwari |
| Kanishk Kumar Ranjan |
| Aayush chaturvedi |
| Bharat Singh |

## 📋 Development Progress

### ✅ Completed
- [x] Project planning and architecture
- [x] Repository setup and Git initialization
- [x] Technology stack selection
- [x] Database schema design (Prisma)

### 🔄 In Progress
- [ ] Basic React app setup with Vite
- [ ] Supabase project configuration
- [ ] Basic 3D cube rendering with Three.js

### 📅 Upcoming
- [ ] User authentication with Supabase Auth
- [ ] Cube state management system
- [ ] Python solving algorithm integration
- [ ] Mobile-responsive UI design

## 🤝 Contributing

This is an academic project for semester 3. Team members should:

1. Create feature branches for new development
2. Follow the established coding conventions
3. Write tests for new functionality
4. Update documentation as needed

### Branch Naming Convention
```
feature/cube-visualization
bugfix/rotation-animation
hotfix/authentication-error
```

### Commit Message Format
```
type(scope): description

feat(cube): add 3D rotation animations
fix(auth): resolve JWT token expiration issue
docs(readme): update installation instructions
```

## 📚 Documentation

- [Project Idea & Requirements](./idea.md)
- [API Documentation](./docs/api.md) *(Coming Soon)*
- [Frontend Guide](./docs/frontend.md) *(Coming Soon)*
- [Backend Guide](./docs/backend.md) *(Coming Soon)*
- [Deployment Guide](./docs/deployment.md) *(Coming Soon)*

## 🔗 Links

- **Live Demo**: *(Coming Soon)*
- **Project Presentation**: *(Coming Soon)*
- **Design Mockups**: *(Coming Soon)*

## 📄 License

This project is created for educational purposes as part of a semester project. All rights reserved to the team members.

## 🙏 Acknowledgments

- Kociemba algorithm for optimal cube solving
- Three.js community for 3D visualization resources
- OpenCV team for computer vision capabilities
- Our course instructors for guidance and support

---

**Note**: This project is actively under development. Features and documentation will be updated regularly as we progress through the semester.
