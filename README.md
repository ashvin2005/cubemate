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
- React.js 18+ with TypeScript
- Three.js with react-three-fiber
- Material-UI / Chakra UI
- Redux Toolkit / Zustand

### Backend
- Node.js with Express.js / Python with FastAPI
- PostgreSQL + Redis
- JWT Authentication
- OpenCV for computer vision

### Deployment
- Frontend: Vercel / Netlify
- Backend: Railway / Render
- Database: Supabase / AWS RDS

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
- PostgreSQL
- Redis

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-team/cubemate.git
   cd cubemate
   ```

2. **Frontend Setup**
   ```bash
   cd frontend
   npm install
   npm start
   ```

3. **Backend Setup**
   ```bash
   cd backend
   npm install
   # or for Python backend
   pip install -r requirements.txt
   npm run dev
   ```

4. **Database Setup**
   ```bash
   # Create PostgreSQL database
   createdb cubemate_dev
   # Run migrations
   npm run migrate
   ```

## 👥 Team Members

| Name | Role | Responsibilities |
|------|------|-----------------|
| [Member 1] | Frontend Lead | React.js, Three.js, UI/UX |
| [Member 2] | Backend Lead | API, Database, Authentication |
| [Member 3] | Algorithm Engineer | Kociemba, OpenCV, Performance |
| [Member 4] | Product Designer | UX/UI, Educational Features |

## 📋 Development Progress

### ✅ Completed
- [ ] Project planning and architecture
- [ ] Repository setup
- [ ] Technology stack selection

### 🔄 In Progress
- [ ] Basic 3D cube rendering
- [ ] User authentication system
- [ ] Database schema design

### 📅 Upcoming
- [ ] Cube state management
- [ ] Solving algorithm integration
- [ ] Tutorial system development
- [ ] Mobile optimization

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

*Last Updated: October 2025*
