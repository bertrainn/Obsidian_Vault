# Day 3: Advanced Hooks & Component Patterns

## 🎯 Daily Goal
Learn essential React hooks and component composition patterns

## 📚 Topics to Cover
- [ ] useEffect Hook (side effects, cleanup, dependencies)
- [ ] useContext Hook
- [ ] useReducer Hook
- [ ] Custom Hooks
- [ ] Component composition
- [ ] Higher-Order Components (HOCs)
- [ ] Render props pattern

---

## 🤔 Pre-Learning Questions
*Answer these before you start learning today:*

1. **What do you think "side effects" means in React programming?**
   
   *Your answer:*

2. **When might you need to share state between components that aren't directly connected?**
   
   *Your answer:*

3. **What patterns have you noticed for reusing logic between components?**
   
   *Your answer:*

---

## 📖 Learning Questions
*Answer these as you go through the material:*

### useEffect Hook
1. **What is useEffect used for? Give at least 3 examples.**
   
   *Your answer:*

2. **Explain the useEffect dependency array. What happens with [], [value], and no array?**
   
   *Your answer:*

3. **Why and when do you need cleanup functions in useEffect?**
   
   *Your answer:*

4. **How would you implement componentDidMount, componentDidUpdate, and componentWillUnmount using useEffect?**
   
   *Your answer:*

### useContext Hook
5. **What problem does the Context API solve?**
   
   *Your answer:*

6. **When should you use Context vs props? What are the trade-offs?**
   
   *Your answer:*

7. **How do you create and consume a Context in React?**
   
   *Your answer:*

### useReducer Hook
8. **When would you choose useReducer over useState?**
   
   *Your answer:*

9. **What are the parts of a reducer function and how do they work together?**
   
   *Your answer:*

### Custom Hooks
10. **What makes a custom hook different from a regular function?**
    
    *Your answer:*

11. **What are the rules for creating custom hooks?**
    
    *Your answer:*

### Component Patterns
12. **Explain component composition and why it's preferred over inheritance in React.**
    
    *Your answer:*

13. **What is a Higher-Order Component (HOC) and when would you use one?**
    
    *Your answer:*

14. **What are render props and how do they enable code reuse?**
    
    *Your answer:*

---

## 🛠️ Practice Projects
Complete these projects today:

### Project 1: Weather App with API Calls ✅
**Requirements:**
- [ ] Fetch weather data from API on component mount
- [ ] Search for different cities
- [ ] Loading states during API calls
- [ ] Error handling for failed requests
- [ ] Cleanup any ongoing requests

**Advanced features:**
- [ ] Cache recent searches
- [ ] Auto-refresh every 5 minutes
- [ ] Geolocation for current weather

**useEffect Challenges:**
- [ ] Prevent memory leaks from cancelled requests
- [ ] Implement proper cleanup
- [ ] Handle multiple dependency changes

**Reflection:** How did you handle the different useEffect scenarios?

*Your answer:*

### Project 2: Theme Switcher with Context ✅
**Requirements:**
- [ ] Create a ThemeContext
- [ ] Provide theme state to entire app
- [ ] Multiple components consuming theme
- [ ] Toggle between light/dark themes
- [ ] Persist theme preference

**Advanced features:**
- [ ] Multiple color schemes
- [ ] System theme detection
- [ ] Smooth theme transitions

**Context Challenges:**
- [ ] Avoid unnecessary re-renders
- [ ] Split contexts for performance
- [ ] Handle context updates properly

**Reflection:** How did Context change the way you think about state sharing?

*Your answer:*

### Project 3: Custom Hook for localStorage ✅
**Requirements:**
- [ ] Create useLocalStorage hook
- [ ] Sync state with localStorage
- [ ] Handle JSON serialization
- [ ] Return current value and setter
- [ ] Handle edge cases (unavailable localStorage)

**Advanced features:**
- [ ] useSessionStorage variant
- [ ] Expiration dates for stored data
- [ ] Validation for stored values

**Custom Hook Challenges:**
- [ ] Make it type-safe (if using TypeScript)
- [ ] Handle SSR scenarios
- [ ] Optimize performance

**Reflection:** What benefits did you see from extracting logic into a custom hook?

*Your answer:*

### Project 4: Data Fetching Hook ✅
**Requirements:**
- [ ] Create useFetch custom hook
- [ ] Handle loading, data, and error states
- [ ] Support different HTTP methods
- [ ] Request cancellation
- [ ] Retry logic

**Advanced features:**
- [ ] Caching mechanism
- [ ] Optimistic updates
- [ ] Pagination support

**Hook Composition Challenges:**
- [ ] Combine with other hooks
- [ ] Make it reusable across different APIs
- [ ] Handle complex loading states

**Reflection:** How did creating reusable hooks change your development approach?

*Your answer:*

---

## 🔗 Resources for Today
- [React Hooks in Action (Book)](https://www.manning.com/books/react-hooks-in-action)
- [Dave Gray React Course](https://www.youtube.com/playlist?list=PL0Zuz27SZ-6PrE9srvEn8nbhOOyxnWXfp)

---

## 🧪 Advanced Challenges

### Challenge 1: useEffect Mastery
Create examples demonstrating:
- [ ] Data fetching on mount
- [ ] Subscribing to external data
- [ ] Cleanup subscriptions
- [ ] Dependent effects
- [ ] Conditional effects

**What useEffect pattern was most challenging to implement?**

*Your answer:*

### Challenge 2: Custom Hook Library
Build these custom hooks:
- [ ] useToggle
- [ ] useCounter
- [ ] useInput
- [ ] useDebounce
- [ ] usePrevious

**Which custom hook taught you the most about hook composition?**

*Your answer:*

### Challenge 3: Component Pattern Comparison
Implement the same functionality using:
- [ ] Higher-Order Component
- [ ] Render props
- [ ] Custom hook
- [ ] Component composition

**Which pattern felt most natural and why?**

*Your answer:*

---

## 🎯 End-of-Day Assessment

### Knowledge Check
1. **Can you use useEffect for different lifecycle scenarios?**
   - [ ] Yes, confidently
   - [ ] Yes, with some reference
   - [ ] Not yet, need more practice

2. **Do you understand when and how to use Context API?**
   - [ ] Yes, confidently
   - [ ] Yes, with some reference
   - [ ] Not yet, need more practice

3. **Can you create effective custom hooks?**
   - [ ] Yes, confidently
   - [ ] Yes, with some reference
   - [ ] Not yet, need more practice

4. **Do you understand different component composition patterns?**
   - [ ] Yes, confidently
   - [ ] Yes, with some reference
   - [ ] Not yet, need more practice

### Today's Wins
*Write about your biggest accomplishment today:*

*Your answer:*

### Most Challenging Concept
*What was the most difficult concept today and how are you working to understand it better?*

*Your answer:*

### Pattern Preferences
*Which component pattern or hook resonated most with you and why?*

*Your answer:*

---

## 📝 Code Snippets & Notes

```javascript
// Example: useEffect with cleanup
useEffect(() => {
  const subscription = subscribeToSomething();
  return () => {
    subscription.unsubscribe();
  };
}, []);

// Example: Custom hook
function useLocalStorage(key, initialValue) {
  const [storedValue, setStoredValue] = useState(() => {
    try {
      const item = window.localStorage.getItem(key);
      return item ? JSON.parse(item) : initialValue;
    } catch (error) {
      return initialValue;
    }
  });
  
  const setValue = (value) => {
    try {
      setStoredValue(value);
      window.localStorage.setItem(key, JSON.stringify(value));
    } catch (error) {
      console.error(error);
    }
  };
  
  return [storedValue, setValue];
}
```

*Your notes:*

---

## 🔄 Building on Previous Days
*How did today's advanced concepts build on your understanding from Days 1-2?*

*Your answer:*

---

## ✅ Daily Checklist
- [ ] Completed all reading/video materials
- [ ] Answered all learning questions
- [ ] Built all four practice projects
- [ ] Completed advanced challenges
- [ ] Completed end-of-day assessment
- [ ] Connected concepts to previous days
- [ ] Identified areas for tomorrow's focus

**Time spent today:** _____ hours

**Most valuable learning today:**

*Your answer:*

**Ready for Day 4 (Routing)?** [ ] Yes [ ] Need review [ ] Need more practice

**Specific areas to review:**
