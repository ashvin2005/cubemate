# 🧊 CubeMate — Your Intelligent 3D Rubik's Cube Solving Companion

## 📋 Project Title & Overview

**CubeMate** is an advanced web-based 3D Rubik's Cube solver and learning platform that combines interactive visualization, intelligent solving algorithms, and educational features. The platform helps users visualize, input, solve, and learn Rubik's cube techniques through immersive 3D animations and step-by-step guidance.

**Purpose**: To create an educational and interactive tool that makes Rubik's cube solving accessible to beginners while providing advanced features for enthusiasts, including pattern recognition, solving tutorials, and performance tracking.

---

## 🧩 Enhanced Key Features / Modules

### 🎯 Core Features
1. **3D Interactive Cube Visualization**
   - Realistic 3D Rubik's Cube using Three.js/react-three-fiber
   - Smooth rotation animations and zoom controls
   - Manual color assignment with intuitive click-to-color interface
   - Real-time cube state validation

2. **Multiple Input Methods**
   - **Manual Mode**: Click-based color assignment with 6-color palette
   - **Camera Mode**: Upload 6 face photos with OpenCV color detection
   - **Notation Input**: Direct cube state input using standard notation
   - **Random Scramble**: Generate valid random cube configurations

3. **Intelligent Solving Engine**
   - Kociemba two-phase algorithm implementation
   - Multiple solving methods (Beginner, CFOP, Roux)
   - Optimal solution generation (20 moves or less)
   - Alternative solution paths

4. **Interactive Learning System**
   - Step-by-step animated solutions
   - Pause/resume/replay controls
   - Speed adjustment (0.5x to 3x)
   - Educational explanations for each move
   - Method-specific tutorials (Layer-by-layer, CFOP basics)

### 🚀 Enhanced Features
5. **User Management & Progress Tracking**
   - User registration and authentication
   - Personal solve history and statistics
   - Performance metrics (average solve time, success rate)
   - Achievement system and badges

6. **Learning Hub**
   - Interactive tutorials for different solving methods
   - Common patterns and algorithms library
   - Practice mode with guided hints
   - Quiz system for notation and pattern recognition

7. **Community Features**
   - Solve challenges and competitions
   - Leaderboards (daily/weekly/all-time)
   - Share cube configurations and solutions
   - User-generated content (custom scrambles)

8. **Advanced Tools**
   - Cube timer with inspection period
   - Move counter and efficiency analysis
   - Pattern recognition for common cases
   - Export solutions as notation

### 🔧 Optional/Future Features
9. **AI-Powered Enhancements**
   - Smart hints based on current cube state
   - Personalized learning recommendations
   - Difficulty adaptation based on user performance

10. **Mobile & Accessibility**
    - Progressive Web App (PWA) support
    - Touch gestures for mobile cube manipulation
    - Keyboard navigation and screen reader support

---

## 👥 User Roles

### 1. **Guest User**
- View demo cube and basic features
- Try manual color input and basic solving
- Access limited tutorials
- No progress tracking or history

### 2. **Registered User**
- Full access to all solving features
- Personal progress tracking and statistics
- Save favorite cube configurations
- Participate in challenges and competitions
- Access complete tutorial library

### 3. **Premium User** (Optional)
- Advanced analytics and detailed statistics
- Priority customer support
- Early access to new features
- Custom themes and cube designs
- Advanced algorithm tutorials

### 4. **Administrator**
- User management and moderation
- Content management (tutorials, challenges)
- System analytics and monitoring
- Community moderation tools

---

## 🖥️ Page / Screen List (Frontend)

### Public Pages
1. **Landing Page** - Hero section, features overview, demo
2. **About Page** - Project information, team details
3. **Tutorial Hub** - Learning resources and guides

### Authentication
4. **Login Page** - User authentication
5. **Register Page** - User registration
6. **Forgot Password** - Password recovery

### Main Application
7. **Dashboard** - User overview, quick stats, recent activity
8. **Cube Solver** - Main 3D cube interface and solving tools
9. **Learning Center** - Interactive tutorials and lessons
10. **Practice Mode** - Guided practice with hints
11. **Timer & Statistics** - Solve timing and performance tracking
12. **Pattern Library** - Algorithm reference and practice
13. **Challenges** - Daily/weekly solving challenges
14. **Leaderboards** - Community rankings and competitions
15. **Profile Settings** - User preferences and account management
16. **History** - Solve history and detailed analytics

### Admin Panel (if applicable)
17. **Admin Dashboard** - System overview and user management
18. **Content Management** - Tutorial and challenge creation
19. **Analytics** - User engagement and system metrics

---

## 🗄️ Database Schema (Prisma ORM)

### Users Model
```prisma
model User {
  id        String   @id @default(cuid())
  username  String   @unique @db.VarChar(50)
  email     String   @unique @db.VarChar(100)
  fullName  String?  @db.VarChar(100)
  avatarUrl String?
  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt
  isActive  Boolean  @default(true)
  role      Role     @default(USER)
  
  // Relations
  cubeStates     CubeState[]
  solveSessions  SolveSession[]
  userProgress   UserProgress[]
  submissions    ChallengeSubmission[]
  
  @@map("users")
}

enum Role {
  GUEST
  USER
  PREMIUM
  ADMIN
}
```

### Cube Configurations
```prisma
model CubeState {
  id        String   @id @default(cuid())
  userId    String
  stateData Json     // Cube color configuration
  name      String   @db.VarChar(100)
  isPublic  Boolean  @default(false)
  createdAt DateTime @default(now())
  
  // Relations
  user          User           @relation(fields: [userId], references: [id], onDelete: Cascade)
  solveSessions SolveSession[]
  
  @@map("cube_states")
}
```

### Solve Sessions
```prisma
model SolveSession {
  id            String   @id @default(cuid())
  userId        String
  cubeStateId   String
  solutionSteps Json     // Array of solving moves
  solveTime     Int?     // in milliseconds
  moveCount     Int
  methodUsed    String   @db.VarChar(50)
  completedAt   DateTime @default(now())
  wasSuccessful Boolean  @default(false)
  
  // Relations
  user      User      @relation(fields: [userId], references: [id], onDelete: Cascade)
  cubeState CubeState @relation(fields: [cubeStateId], references: [id], onDelete: Cascade)
  
  @@map("solve_sessions")
}
```

### Learning Progress
```prisma
model UserProgress {
  id                 String   @id @default(cuid())
  userId             String
  tutorialId         String
  completed          Boolean  @default(false)
  progressPercentage Int      @default(0)
  lastAccessed       DateTime @default(now())
  
  // Relations
  user     User     @relation(fields: [userId], references: [id], onDelete: Cascade)
  tutorial Tutorial @relation(fields: [tutorialId], references: [id], onDelete: Cascade)
  
  @@unique([userId, tutorialId])
  @@map("user_progress")
}
```

### Tutorials & Content
```prisma
model Tutorial {
  id              String      @id @default(cuid())
  title           String      @db.VarChar(200)
  description     String      @db.Text
  content         Json        // Tutorial steps and content
  difficultyLevel Difficulty
  category        String      @db.VarChar(50)
  createdById     String
  isPublished     Boolean     @default(false)
  createdAt       DateTime    @default(now())
  
  // Relations
  createdBy    User           @relation(fields: [createdById], references: [id])
  userProgress UserProgress[]
  
  @@map("tutorials")
}

enum Difficulty {
  BEGINNER
  INTERMEDIATE
  ADVANCED
}
```

### Challenges & Competitions
```prisma
model Challenge {
  id                String   @id @default(cuid())
  title             String   @db.VarChar(200)
  description       String   @db.Text
  cubeConfiguration Json     // Starting cube state
  startDate         DateTime
  endDate           DateTime
  isActive          Boolean  @default(true)
  prizeDescription  String?  @db.Text
  
  // Relations
  submissions ChallengeSubmission[]
  
  @@map("challenges")
}

model ChallengeSubmission {
  id            String   @id @default(cuid())
  challengeId   String
  userId        String
  solutionSteps Json     // User's solution
  solveTime     Int      // in milliseconds
  submittedAt   DateTime @default(now())
  
  // Relations
  challenge Challenge @relation(fields: [challengeId], references: [id], onDelete: Cascade)
  user      User      @relation(fields: [userId], references: [id], onDelete: Cascade)
  
  @@unique([challengeId, userId])
  @@map("challenge_submissions")
}
```

---

## ⚙️ Tech Stack (Based on Team Skills)

### Frontend
- **Framework**: React.js with JavaScript (team expertise)
- **3D Graphics**: Three.js with react-three-fiber (learnable - good docs)
- **Styling**: Tailwind CSS (team knows)
- **Routing**: React Router v6 (easy to learn)
- **State Management**: React Context API + useState/useEffect (built-in)
- **Build Tool**: Vite

### Backend
- **Runtime**: Node.js with Express.js (team expertise)
- **Authentication**: JWT tokens with Supabase Auth (team knows Supabase)
- **API Structure**: RESTful APIs with Express.js
- **File Upload**: Multer (easy to learn for image uploads)
- **Cube Solving Engine**: Python script with kociemba library (separate service)

### Database & ORM
- **Database**: Supabase (PostgreSQL) - team knows
- **ORM**: Prisma ORM (team knows)
- **Real-time**: Supabase real-time subscriptions
- **File Storage**: Supabase Storage for cube images

### Python Services
- **Cube Solver**: Python with kociemba library
- **Computer Vision**: OpenCV for color detection (moderate learning curve)
- **API Communication**: Flask/FastAPI for Python endpoints (easy to learn)

### Development & Deployment
- **Version Control**: Git with GitHub (team expertise)
- **Frontend Hosting**: Vercel (team knows)
- **Backend Hosting**: Vercel Serverless Functions or Railway (easy to learn)
- **Database**: Supabase (team expertise)
- **Environment Management**: dotenv for configuration

### Easy-to-Learn Additions
- **API Documentation**: Basic Swagger/Postman collections
- **Error Handling**: Simple try-catch with user-friendly messages
- **Loading States**: React loading spinners and skeleton screens
- **Form Validation**: Simple client-side validation with regex

---


## 🔄 User Workflow

### New User Journey
1. **Discovery** → Landing page → View demo
2. **Registration** → Create account → Email verification
3. **Onboarding** → Tutorial introduction → Basic cube manipulation
4. **First Solve** → Manual color input → Guided solving
5. **Learning** → Tutorial progression → Practice mode
6. **Engagement** → Challenges → Community features

### Solving Workflow
1. **Cube Setup** → Choose input method (manual/camera/notation)
2. **Validation** → System checks cube validity
3. **Method Selection** → Choose solving approach
4. **Solution Generation** → Backend computes optimal solution
5. **Interactive Learning** → Step-by-step animated guidance
6. **Completion** → Statistics tracking → Share/save results

### Learning Workflow
1. **Assessment** → Skill level evaluation
2. **Path Selection** → Choose learning method (CFOP, Layer-by-layer)
3. **Progressive Tutorials** → Interactive lessons with practice
4. **Pattern Recognition** → Algorithm memorization tools
5. **Applied Practice** → Timed solves with hints
6. **Mastery Validation** → Challenges and assessments

---

## 🎯 Expected Outcomes (Realistic Scope)

### Core Deliverables (Must-Have)
- **Responsive web application** built with React + Tailwind CSS
- **3D interactive Rubik's cube** using Three.js with basic rotations
- **Manual color input system** with 6-color palette
- **Working cube solver** using Python kociemba algorithm
- **Step-by-step solution display** with move-by-move animations
- **User authentication** with Supabase Auth
- **Basic user dashboard** showing solve history

### Enhanced Features (Should-Have)
- **Cube state validation** to ensure valid configurations
- **Multiple solving methods** (beginner vs advanced)
- **Save/load cube configurations** with Prisma + Supabase
- **Simple tutorial system** for basic cube operations
- **Mobile-responsive design** with touch controls
- **Solution export** as text notation

### Stretch Goals (Could-Have)
- **Camera-based color detection** using OpenCV (if time permits)
- **Basic competition/challenge system**
- **Simple performance statistics** and solve tracking
- **Admin panel** for content management

### Learning Achievements
- **Three.js proficiency** for 3D web development
- **Full-stack integration** between React, Node.js, and Python
- **Database design** with Prisma ORM
- **Authentication implementation** with modern tools
- **Algorithm integration** (understanding cube-solving logic)
- **Deployment experience** with Vercel and Supabase

### Success Metrics (Realistic)
- Users can input cube colors and get a working solution
- 3D cube renders smoothly on desktop and mobile
- Solution animations are clear and educational
- Basic user system works (register, login, save progress)
- Application deploys successfully and is publicly accessible
- Code is well-documented and maintainable for future development

### Technical Demonstration
- **Live demo** of cube solving with real-time 3D visualization
- **Mobile compatibility** showing responsive design
- **User flow demonstration** from registration to first solve
- **Code walkthrough** explaining key architectural decisions
- **Performance analysis** of 3D rendering and algorithm efficiency

---


## 🔮 Future Expansion Possibilities

- **AR/VR Integration**: Mixed reality cube solving
- **Advanced Algorithms**: Roux, ZZ, and Petrus methods
- **Different Cube Sizes**: 2x2, 4x4, 5x5 support
- **AI Tutoring**: Personalized learning with machine learning
- **Mobile App**: Native iOS/Android applications
- **Hardware Integration**: Smart cube connectivity
- **Multiplayer**: Real-time solving competitions
- **Certification System**: Official skill level certifications

---

*This project combines cutting-edge web technologies with educational value, making it an ideal end-semester project that demonstrates full-stack development skills while creating a meaningful learning tool for the Rubik's cube community.*
