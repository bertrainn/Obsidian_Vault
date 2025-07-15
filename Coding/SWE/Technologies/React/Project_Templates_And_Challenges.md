# React Project Templates & Coding Challenges

## Quick Setup Commands

### Create React App Projects
```bash
# Traditional Create React App
npx create-react-app my-app
cd my-app
npm start

# With TypeScript
npx create-react-app my-app --template typescript
```

### Vite Projects (Recommended - Faster)
```bash
# JavaScript
npm create vite@latest my-react-app -- --template react

# TypeScript
npm create vite@latest my-react-app -- --template react-ts
```

---

## Day-by-Day Project Templates

### Day 1 Projects

#### 1. Personal Card Component
**Goal:** Practice props and basic JSX
- Display name, photo, bio, skills
- Make it reusable with different data
- Style with CSS modules or styled-components

#### 2. Simple Calculator
**Goal:** Event handling and basic state
- Add, subtract, multiply, divide
- Clear function
- Display calculation history

### Day 2 Projects

#### 1. Interactive Todo List
**Features to implement:**
- Add new todos
- Mark as complete/incomplete
- Delete todos
- Filter (all, active, completed)
- Local storage persistence

#### 2. Dynamic Form Builder
**Challenge:** Build a form that adds/removes fields dynamically
- Text inputs, checkboxes, radio buttons
- Form validation
- Submit and display data

### Day 3 Projects

#### 1. Weather Dashboard
**API Integration practice:**
- Use OpenWeatherMap API
- Search by city
- Display current weather and 5-day forecast
- Custom hook for API calls
- Loading states and error handling

#### 2. Theme Context App
**Global state practice:**
- Light/dark theme toggle
- Multiple color schemes
- Theme persistence
- Context + useReducer pattern

### Day 4 Projects

#### 1. Multi-Page Portfolio
**Routing practice:**
- Home, About, Projects, Contact pages
- Project detail pages with URL parameters
- 404 page
- Navigation with active states
- SEO-friendly URLs

#### 2. Blog Application
**Advanced routing:**
- Blog post list with pagination
- Individual post pages
- Category filtering
- Search functionality
- Protected admin routes

### Day 5 Projects

#### 1. E-commerce Cart System
**State management focus:**
- Product catalog
- Add/remove from cart
- Quantity management
- Cart persistence
- Checkout flow
- Redux Toolkit implementation

#### 2. Real-time Dashboard
**Performance optimization:**
- Multiple widgets with data
- Auto-refresh capabilities
- Memoization practice
- Lazy loading of components
- Virtual scrolling for large lists

### Day 6 Projects

#### 1. Testing Suite Implementation
**Add comprehensive tests to previous projects:**
- Component unit tests
- Integration tests
- API mocking
- User interaction testing
- Coverage reports

#### 2. Component Library
**Advanced patterns:**
- Reusable UI components
- Storybook documentation
- TypeScript definitions
- Custom hooks library
- NPM package setup

### Day 7 Capstone Project Options

#### Option A: Social Media Platform
**Features:**
- User authentication
- Create/edit/delete posts
- Like and comment system
- User profiles
- Image upload
- Real-time notifications
- Responsive design

#### Option B: Project Management Tool
**Features:**
- Multiple projects
- Task creation and assignment
- Drag-and-drop interface
- Progress tracking
- Team collaboration
- File attachments
- Dashboard analytics

#### Option C: E-learning Platform
**Features:**
- Course catalog
- Video player integration
- Progress tracking
- Quizzes and assessments
- User profiles
- Payment integration
- Admin panel

---

## Coding Challenges by Difficulty

### Beginner Challenges (Days 1-2)
1. **Clock Component** - Digital and analog versions
2. **Color Picker** - HSL/RGB/HEX conversion
3. **Rating System** - Star ratings with hover effects
4. **Image Gallery** - Grid layout with lightbox
5. **Accordion Component** - Collapsible content sections

### Intermediate Challenges (Days 3-4)
1. **Infinite Scroll** - Load more content as user scrolls
2. **Autocomplete Search** - Debounced API calls
3. **Drag and Drop** - Sortable lists
4. **Modal Manager** - Multiple modals with z-index management
5. **Chart Components** - Data visualization with libraries

### Advanced Challenges (Days 5-7)
1. **Virtual Scrolling** - Handle thousands of items efficiently
2. **Real-time Collaboration** - Multiple users editing simultaneously
3. **PWA Implementation** - Service workers and offline functionality
4. **Micro-frontend Architecture** - Module federation
5. **Performance Monitoring** - Custom analytics and error tracking

---

## GitHub Repository Templates

### Starter Templates to Fork/Clone

#### Beginner-Friendly:
1. **React Starter Kit**: https://github.com/facebook/create-react-app
2. **Vite React Template**: https://github.com/vitejs/vite/tree/main/packages/create-vite/template-react
3. **Simple React Boilerplate**: Search for "react-boilerplate-simple"

#### With Additional Tools:
1. **React + TypeScript + Tailwind**: Search for "react-typescript-tailwind-starter"
2. **React + Redux Toolkit**: https://github.com/reduxjs/redux-toolkit-example
3. **React + Router + Context**: Search for "react-context-router-template"

#### Full-Stack Templates:
1. **MERN Stack**: Search for "mern-stack-template"
2. **React + Express + MongoDB**: Multiple options available
3. **React + Firebase**: Search for "react-firebase-starter"

---

## Recommended APIs for Practice

### Free APIs (No Auth Required):
- **JSONPlaceholder**: https://jsonplaceholder.typicode.com/
- **Rick and Morty API**: https://rickandmortyapi.com/
- **Pokemon API**: https://pokeapi.co/
- **Cat Facts**: https://catfact.ninja/
- **Random User Generator**: https://randomuser.me/

### APIs with Free Tiers:
- **OpenWeatherMap**: Weather data
- **The Movie Database (TMDB)**: Movie/TV data
- **NewsAPI**: News articles
- **Unsplash**: Stock photos
- **GitHub API**: Repository data

### Real-time APIs:
- **WebSocket.org Echo Test**: wss://echo.websocket.org/
- **Socket.io Examples**: Various real-time demos
- **Firebase Realtime Database**: Google's real-time solution

---

## Learning Resources by Project Type

### Component Libraries to Study:
1. **Material-UI (MUI)**: https://mui.com/
2. **Ant Design**: https://ant.design/
3. **Chakra UI**: https://chakra-ui.com/
4. **React Bootstrap**: https://react-bootstrap.github.io/

### Animation Libraries:
1. **Framer Motion**: https://www.framer.com/motion/
2. **React Spring**: https://react-spring.io/
3. **React Transition Group**: https://reactcommunity.org/react-transition-group/

### Form Libraries:
1. **React Hook Form**: https://react-hook-form.com/
2. **Formik**: https://formik.org/
3. **React Final Form**: https://final-form.org/react

### Testing Resources:
1. **Testing Library Examples**: https://testing-library.com/docs/example-intro
2. **Jest Documentation**: https://jestjs.io/docs/tutorial-react
3. **React Testing Patterns**: Search for testing best practices

---

## Daily Challenge Suggestions

### Morning Warm-up (30 minutes):
- Implement a simple component from scratch
- Refactor previous day's code
- Code review and optimization

### Afternoon Deep Dive (2-3 hours):
- Main project development
- Feature implementation
- Problem-solving and debugging

### Evening Review (1 hour):
- Document what you learned
- Plan next day's goals
- Quick knowledge reinforcement

---

*Use this as your practical coding companion alongside the main roadmap. Focus on building and experimenting rather than perfection.*
