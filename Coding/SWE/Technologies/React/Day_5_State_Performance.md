# Day 5: State Management & Performance

## 🎯 Daily Goal
Learn global state management and optimization techniques

## 📚 Topics to Cover
- [ ] Context API for global state
- [ ] Redux Toolkit basics
- [ ] When to use global vs local state
- [ ] Performance optimization (React.memo, useMemo, useCallback)
- [ ] Code splitting and lazy loading
- [ ] Error boundaries
- [ ] React Profiler

---

## 🤔 Pre-Learning Questions
*Answer these before you start learning today:*

1. **When do you think you need global state versus local component state?**
   
   *Your answer:*

2. **What performance issues might you encounter in a large React application?**
   
   *Your answer:*

3. **How do you think React decides when to re-render components?**
   
   *Your answer:*

---

## 📖 Learning Questions
*Answer these as you go through the material:*

### Global State Management
1. **When should you use Context API vs Redux vs local state? Give specific scenarios.**
   
   *Your answer:*

2. **What are the trade-offs between different state management solutions?**
   
   *Your answer:*

3. **How does Redux Toolkit simplify Redux development compared to vanilla Redux?**
   
   *Your answer:*

4. **Explain the Redux data flow: actions, reducers, store, and selectors.**
   
   *Your answer:*

### Performance Optimization
5. **What causes unnecessary re-renders in React and how can you prevent them?**
   
   *Your answer:*

6. **Explain the difference between React.memo, useMemo, and useCallback. When would you use each?**
   
   *Your answer:*

7. **What is code splitting and how does React.lazy work?**
   
   *Your answer:*

8. **How do you identify performance bottlenecks in a React application?**
   
   *Your answer:*

### Error Handling and Monitoring
9. **What are Error Boundaries and when should you use them?**
   
   *Your answer:*

10. **How do you handle errors in async operations and API calls?**
    
    *Your answer:*

11. **What tools and techniques can you use to monitor React application performance?**
    
    *Your answer:*

---

## 🛠️ Practice Projects
Complete these projects today:

### Project 1: Shopping Cart with Redux Toolkit ✅
**Requirements:**
- [ ] Product catalog with Redux store
- [ ] Add/remove items from cart
- [ ] Quantity management
- [ ] Cart total calculations
- [ ] Persistent cart state
- [ ] Loading states for async operations

**Advanced features:**
- [ ] User preferences in global state
- [ ] Order history management
- [ ] Real-time inventory updates
- [ ] Coupon/discount system

**Redux Challenges:**
- [ ] Implement proper action creators
- [ ] Use RTK Query for API calls
- [ ] Handle optimistic updates
- [ ] Implement proper error handling

**Reflection:** How did Redux change the way you think about state management?

*Your answer:*

### Project 2: User Authentication System ✅
**Requirements:**
- [ ] Login/logout functionality
- [ ] User session management
- [ ] Protected route state
- [ ] User profile management
- [ ] Role-based permissions
- [ ] Token refresh handling

**Advanced features:**
- [ ] Remember me functionality
- [ ] Multi-device logout
- [ ] Social login integration
- [ ] Password reset flow

**State Management Challenges:**
- [ ] Sync auth state across components
- [ ] Handle authentication errors gracefully
- [ ] Implement secure token storage

**Reflection:** How did you decide what auth state should be global vs local?

*Your answer:*

### Project 3: Real-time Chat Application State ✅
**Requirements:**
- [ ] Multiple chat rooms
- [ ] Message history management
- [ ] User presence indicators
- [ ] Typing indicators
- [ ] Unread message counts
- [ ] Message search functionality

**Advanced features:**
- [ ] Message reactions
- [ ] File sharing state
- [ ] Chat notifications
- [ ] Message persistence

**Performance Challenges:**
- [ ] Optimize message list rendering
- [ ] Handle large message histories
- [ ] Implement virtual scrolling
- [ ] Debounce typing indicators

**Reflection:** What strategies did you use to handle real-time state updates efficiently?

*Your answer:*

### Project 4: Performance-Optimized Dashboard ✅
**Requirements:**
- [ ] Multiple widgets with data
- [ ] Auto-refresh capabilities
- [ ] Customizable layout
- [ ] Data filtering and sorting
- [ ] Export functionality
- [ ] Loading states for all widgets

**Performance Optimizations:**
- [ ] Implement React.memo for widgets
- [ ] Use useMemo for expensive calculations
- [ ] Implement useCallback for event handlers
- [ ] Add code splitting for different sections
- [ ] Implement error boundaries

**Advanced Performance Challenges:**
- [ ] Virtual scrolling for large datasets
- [ ] Debounced search inputs
- [ ] Lazy loading of widget data
- [ ] Memory leak prevention

**Reflection:** Which performance optimization had the biggest impact?

*Your answer:*

---

## 🔗 Resources for Today
- [Redux Toolkit Documentation](https://redux-toolkit.js.org/)
- [React Performance Guide](https://react.dev/learn/render-and-commit)

---

## 🧪 Performance Challenges

### Challenge 1: Re-render Analysis
Create a component tree and analyze:
- [ ] When components re-render unnecessarily
- [ ] How prop changes affect child components
- [ ] Impact of context value changes
- [ ] Effect of state updates on siblings

**What patterns caused the most unnecessary re-renders?**

*Your answer:*

### Challenge 2: Optimization Techniques
Implement and compare:
- [ ] Component without optimization
- [ ] Component with React.memo
- [ ] Component with useMemo
- [ ] Component with useCallback
- [ ] Component with code splitting

**Which optimization technique was most effective in your scenario?**

*Your answer:*

### Challenge 3: Memory Management
Build examples that demonstrate:
- [ ] Memory leaks from event listeners
- [ ] Memory leaks from intervals/timeouts
- [ ] Memory leaks from subscriptions
- [ ] Proper cleanup techniques
- [ ] WeakMap usage for caching

**What was the most surprising source of memory leaks you discovered?**

*Your answer:*

---

## 🏭 Redux Deep Dive

### Redux Toolkit Questions
1. **How does createSlice simplify reducer creation?**
   
   *Your answer:*

2. **When would you use createAsyncThunk vs regular action creators?**
   
   *Your answer:*

3. **How does RTK Query compare to other data fetching libraries?**
   
   *Your answer:*

4. **What are the benefits of using immer within Redux Toolkit?**
   
   *Your answer:*

---

## 🎯 End-of-Day Assessment

### Knowledge Check
1. **Can you implement global state management with Redux Toolkit?**
   - [ ] Yes, confidently
   - [ ] Yes, with some reference
   - [ ] Not yet, need more practice

2. **Do you understand when and how to optimize React performance?**
   - [ ] Yes, confidently
   - [ ] Yes, with some reference
   - [ ] Not yet, need more practice

3. **Can you identify and fix performance bottlenecks?**
   - [ ] Yes, confidently
   - [ ] Yes, with some reference
   - [ ] Not yet, need more practice

4. **Do you understand error boundaries and error handling strategies?**
   - [ ] Yes, confidently
   - [ ] Yes, with some reference
   - [ ] Not yet, need more practice

### Today's Wins
*Write about your biggest accomplishment today:*

*Your answer:*

### Performance Insights
*What was the most important performance concept you learned today?*

*Your answer:*

### State Management Philosophy
*How has your understanding of state management evolved throughout the week?*

*Your answer:*

---

## 📝 Code Snippets & Notes

```javascript
// Example: Redux Toolkit slice
import { createSlice } from '@reduxjs/toolkit'

const cartSlice = createSlice({
  name: 'cart',
  initialState: { items: [], total: 0 },
  reducers: {
    addItem: (state, action) => {
      // Immer allows "mutation" syntax
      state.items.push(action.payload)
      state.total += action.payload.price
    },
    removeItem: (state, action) => {
      state.items = state.items.filter(item => item.id !== action.payload)
    }
  }
})

// Example: Performance optimization
const MemoizedComponent = React.memo(({ data, onUpdate }) => {
  const expensiveValue = useMemo(() => {
    return computeExpensiveValue(data);
  }, [data]);

  const handleClick = useCallback(() => {
    onUpdate(data.id);
  }, [onUpdate, data.id]);

  return <div onClick={handleClick}>{expensiveValue}</div>;
});
```

*Your notes:*

---

## 🔄 Connecting the Week's Learning
*How do global state management and performance optimization tie together concepts from Days 1-4?*

*Your answer:*

---

## 📊 Performance Metrics
*Document any performance improvements you measured today:*

**Before optimization:**
- Render time: ___ms
- Bundle size: ___KB
- Memory usage: ___MB

**After optimization:**
- Render time: ___ms
- Bundle size: ___KB
- Memory usage: ___MB

**Key optimizations that made the biggest difference:**

*Your answer:*

---

## ✅ Daily Checklist
- [ ] Completed all reading/video materials
- [ ] Answered all learning questions
- [ ] Built all four practice projects
- [ ] Completed performance challenges
- [ ] Analyzed and documented performance improvements
- [ ] Completed end-of-day assessment
- [ ] Connected concepts to previous days

**Time spent today:** _____ hours

**Most impactful optimization learned:**

*Your answer:*

**Confidence level for Day 6 (Testing):** [ ] Ready [ ] Need review [ ] Need more practice

**Areas needing more practice:**
