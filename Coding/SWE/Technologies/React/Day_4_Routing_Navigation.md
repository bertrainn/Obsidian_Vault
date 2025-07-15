# Day 4: Routing & Navigation

## 🎯 Daily Goal
Build single-page applications with navigation and routing

## 📚 Topics to Cover
- [ ] React Router basics
- [ ] Route configuration
- [ ] Dynamic routing
- [ ] Nested routes
- [ ] Protected routes
- [ ] Navigation (Link, NavLink, useNavigate)
- [ ] URL parameters and query strings
- [ ] Route guards and authentication flow

---

## 🤔 Pre-Learning Questions
*Answer these before you start learning today:*

1. **How do you think single-page applications (SPAs) handle different "pages" without full page reloads?**
   
   *Your answer:*

2. **What challenges might arise when building a multi-page React application?**
   
   *Your answer:*

3. **How would you handle user authentication in a web application with multiple pages?**
   
   *Your answer:*

---

## 📖 Learning Questions
*Answer these as you go through the material:*

### React Router Fundamentals
1. **What is React Router and why is it necessary for SPAs?**
   
   *Your answer:*

2. **Explain the difference between `BrowserRouter`, `HashRouter`, and `MemoryRouter`.**
   
   *Your answer:*

3. **What are the core components of React Router? (Router, Routes, Route, Link, etc.)**
   
   *Your answer:*

### Navigation and Links
4. **What's the difference between `Link`, `NavLink`, and regular anchor tags?**
   
   *Your answer:*

5. **When would you use `useNavigate` instead of `Link` components?**
   
   *Your answer:*

6. **How do you handle programmatic navigation (e.g., after form submission)?**
   
   *Your answer:*

### Dynamic and Nested Routes
7. **How do URL parameters work in React Router? Give examples.**
   
   *Your answer:*

8. **What are nested routes and when would you use them?**
   
   *Your answer:*

9. **How do you access and use query parameters in your components?**
   
   *Your answer:*

### Advanced Routing Concepts
10. **What are protected routes and how do you implement them?**
    
    *Your answer:*

11. **How would you implement route guards for different user roles?**
    
    *Your answer:*

12. **What strategies exist for handling 404 pages and error boundaries with routing?**
    
    *Your answer:*

---

## 🛠️ Practice Projects
Complete these projects today:

### Project 1: Multi-Page Portfolio Website ✅
**Requirements:**
- [ ] Home page with introduction
- [ ] About page with personal info
- [ ] Projects page with project list
- [ ] Contact page with form
- [ ] Navigation menu with active states
- [ ] 404 page for invalid routes

**Advanced features:**
- [ ] Breadcrumb navigation
- [ ] Smooth page transitions
- [ ] SEO-friendly URLs
- [ ] Social media integration

**Routing Challenges:**
- [ ] Implement nested routes for project categories
- [ ] Add URL-based filtering
- [ ] Handle deep linking properly

**Reflection:** How did routing change the structure of your application?

*Your answer:*

### Project 2: Blog with Post Details ✅
**Requirements:**
- [ ] Blog post list page
- [ ] Individual post detail pages
- [ ] Category filtering
- [ ] Tag-based navigation
- [ ] Search functionality
- [ ] Pagination

**Advanced features:**
- [ ] Related posts section
- [ ] Comment system with routing
- [ ] Author profile pages
- [ ] Archive pages by date

**Dynamic Routing Challenges:**
- [ ] Handle dynamic slugs for posts
- [ ] Implement category and tag routes
- [ ] Create flexible URL structures

**Reflection:** How did you handle the relationship between data and URL structure?

*Your answer:*

### Project 3: E-commerce Product Catalog ✅
**Requirements:**
- [ ] Product listing page
- [ ] Product detail pages
- [ ] Category browsing
- [ ] Shopping cart page
- [ ] Checkout flow with steps
- [ ] User account pages

**Advanced features:**
- [ ] Product comparison page
- [ ] Wishlist functionality
- [ ] Order history
- [ ] Product reviews with routing

**Complex Routing Challenges:**
- [ ] Multi-step checkout process
- [ ] Product filtering with URL state
- [ ] Cart persistence across routes

**Reflection:** How did you manage complex state across different routes?

*Your answer:*

### Project 4: Dashboard with Protected Routes ✅
**Requirements:**
- [ ] Login/register pages
- [ ] Protected dashboard area
- [ ] User profile management
- [ ] Settings pages
- [ ] Logout functionality
- [ ] Role-based access control

**Advanced features:**
- [ ] Route guards for different user types
- [ ] Automatic logout on token expiration
- [ ] Remember login state
- [ ] Redirect after login

**Authentication Challenges:**
- [ ] Implement proper route protection
- [ ] Handle authentication state globally
- [ ] Manage redirect flows

**Reflection:** How did you balance security with user experience in your routing?

*Your answer:*

---

## 🔗 Resources for Today
- [React Router Documentation](https://reactrouter.com/)
- [React Router 6 Complete Guide](https://blog.webdevsimplified.com/2022-07/react-router/)

---

## 🧪 Advanced Challenges

### Challenge 1: Route Configuration Patterns
Implement these routing patterns:
- [ ] Route-based code splitting
- [ ] Lazy loading of route components
- [ ] Route configuration object
- [ ] Nested route layouts
- [ ] Conditional routes

**Which routing pattern felt most scalable for larger applications?**

*Your answer:*

### Challenge 2: URL State Management
Build examples of:
- [ ] Search filters in URL
- [ ] Pagination state in URL
- [ ] Form state in URL
- [ ] Modal state in URL
- [ ] Tab state in URL

**How does URL state management compare to component state?**

*Your answer:*

### Challenge 3: Advanced Navigation Patterns
Implement:
- [ ] Breadcrumb component
- [ ] Sidebar navigation with nested items
- [ ] Tab-based navigation
- [ ] Wizard/stepper navigation
- [ ] Mobile-responsive navigation

**What navigation pattern was most challenging to implement?**

*Your answer:*

---

## 🔒 Security Considerations

### Authentication Flow Questions
1. **How do you prevent unauthorized access to protected routes?**
   
   *Your answer:*

2. **What information should you store in the URL vs. local/session storage?**
   
   *Your answer:*

3. **How do you handle expired authentication tokens with routing?**
   
   *Your answer:*

---

## 🎯 End-of-Day Assessment

### Knowledge Check
1. **Can you set up basic routing with React Router?**
   - [ ] Yes, confidently
   - [ ] Yes, with some reference
   - [ ] Not yet, need more practice

2. **Do you understand dynamic routing and URL parameters?**
   - [ ] Yes, confidently
   - [ ] Yes, with some reference
   - [ ] Not yet, need more practice

3. **Can you implement protected routes and authentication flows?**
   - [ ] Yes, confidently
   - [ ] Yes, with some reference
   - [ ] Not yet, need more practice

4. **Do you understand nested routes and complex navigation patterns?**
   - [ ] Yes, confidently
   - [ ] Yes, with some reference
   - [ ] Not yet, need more practice

### Today's Wins
*Write about your biggest accomplishment today:*

*Your answer:*

### Routing Insights
*What was the most surprising thing you learned about routing in React?*

*Your answer:*

### Application Architecture
*How has learning routing changed your perspective on application structure?*

*Your answer:*

---

## 📝 Code Snippets & Notes

```javascript
// Example: Basic routing setup
import { BrowserRouter, Routes, Route } from 'react-router-dom';

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="/products/:id" element={<ProductDetail />} />
        <Route path="*" element={<NotFound />} />
      </Routes>
    </BrowserRouter>
  );
}

// Example: Protected route component
function ProtectedRoute({ children }) {
  const isAuthenticated = useAuth();
  return isAuthenticated ? children : <Navigate to="/login" />;
}
```

*Your notes:*

---

## 🔄 Integration with Previous Concepts
*How did you combine routing with state management, hooks, and components from previous days?*

*Your answer:*

---

## 🚀 Looking Ahead
*Based on today's learning, what aspects of state management do you think will be important for tomorrow (Day 5)?*

*Your answer:*

---

## ✅ Daily Checklist
- [ ] Completed all reading/video materials
- [ ] Answered all learning questions
- [ ] Built all four practice projects
- [ ] Completed advanced challenges
- [ ] Addressed security considerations
- [ ] Completed end-of-day assessment
- [ ] Integrated with previous concepts

**Time spent today:** _____ hours

**Most complex routing challenge overcome:**

*Your answer:*

**Confidence level for Day 5 (Global State Management):** [ ] Ready [ ] Need review [ ] Need more practice

**Areas to review before Day 5:**
