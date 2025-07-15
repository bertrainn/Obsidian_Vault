# Day 2: State Management & Event Handling

## 🎯 Daily Goal
Master component state and user interactions

## 📚 Topics to Cover
- [ ] useState Hook
- [ ] Event handling in React
- [ ] Controlled vs Uncontrolled components
- [ ] Forms in React
- [ ] Conditional rendering
- [ ] Lists and keys
- [ ] Component lifecycle basics

---

## 🤔 Pre-Learning Questions
*Answer these before you start learning today:*

1. **Based on yesterday's learning, what do you think "state" means in React?**
   
   *Your answer:*

2. **How do you think React handles user interactions like button clicks?**
   
   *Your answer:*

3. **What challenges might arise when dealing with forms in a web application?**
   
   *Your answer:*

---

## 📖 Learning Questions
*Answer these as you go through the material:*

### State Management
1. **What is the useState Hook and why is it important?**
   
   *Your answer:*

2. **Explain the syntax: `const [count, setCount] = useState(0);`**
   
   *Your answer:*

3. **Why can't you directly modify state like `state.count = 5`?**
   
   *Your answer:*

### Event Handling
4. **How is event handling in React different from vanilla JavaScript?**
   
   *Your answer:*

5. **What is a SyntheticEvent in React?**
   
   *Your answer:*

6. **Why do we often need to prevent default behavior in form submissions?**
   
   *Your answer:*

### Forms and Controls
7. **What's the difference between controlled and uncontrolled components? Give examples.**
   
   *Your answer:*

8. **Why are controlled components generally preferred in React?**
   
   *Your answer:*

### Rendering Patterns
9. **Explain three different ways to implement conditional rendering in React.**
   
   *Your answer:*

10. **Why do we need the `key` prop when rendering lists? What happens if we don't use it?**
    
    *Your answer:*

---

## 🛠️ Practice Projects
Complete these projects today:

### Project 1: Todo List App ✅
**Requirements:**
- [ ] Add new todos
- [ ] Mark as complete/incomplete
- [ ] Delete todos
- [ ] Filter (all, active, completed)
- [ ] Show total count

**Challenges to implement:**
- [ ] Local storage persistence
- [ ] Edit existing todos
- [ ] Clear all completed

**Reflection:** How did managing multiple pieces of state feel? What patterns did you notice?

*Your answer:*

### Project 2: Interactive Counter ✅
**Requirements:**
- [ ] Increment/decrement buttons
- [ ] Reset button
- [ ] Custom step size input
- [ ] Display current count

**Advanced features:**
- [ ] Set min/max limits
- [ ] History of operations
- [ ] Undo last operation

**Reflection:** How did you handle different types of state updates?

*Your answer:*

### Project 3: Contact Form with Validation ✅
**Requirements:**
- [ ] Name, email, message fields
- [ ] Real-time validation
- [ ] Show error messages
- [ ] Disable submit when invalid
- [ ] Success message after submission

**Advanced features:**
- [ ] Custom validation rules
- [ ] Async validation (email uniqueness)
- [ ] Form reset functionality

**Reflection:** What was challenging about form state management?

*Your answer:*

### Project 4: Dynamic List Renderer ✅
**Requirements:**
- [ ] Render a list of items from state
- [ ] Add new items
- [ ] Remove items
- [ ] Filter/search items
- [ ] Sort items

**Advanced features:**
- [ ] Drag and drop reordering
- [ ] Bulk operations
- [ ] Export list data

**Reflection:** How did you optimize list rendering performance?

*Your answer:*

---

## 🔗 Resources for Today
- [React Hooks Documentation](https://react.dev/reference/react)
- [Net Ninja React Tutorial](https://www.youtube.com/playlist?list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d)

---

## 🧪 Code Challenges
*Try these mini-challenges to test your understanding:*

### Challenge 1: State Update Patterns
Create a component that demonstrates these state update patterns:
- [ ] Simple state update
- [ ] State update based on previous state
- [ ] Updating object state
- [ ] Updating array state

**What did you learn about state update patterns?**

*Your answer:*

### Challenge 2: Event Handling Scenarios
Create examples of handling these events:
- [ ] onClick
- [ ] onChange
- [ ] onSubmit
- [ ] onFocus/onBlur
- [ ] Custom event handlers

**Which event handling pattern felt most natural to you?**

*Your answer:*

---

## 🎯 End-of-Day Assessment

### Knowledge Check
1. **Can you use useState to manage component state?**
   - [ ] Yes, confidently
   - [ ] Yes, with some reference
   - [ ] Not yet, need more practice

2. **Do you understand controlled vs uncontrolled components?**
   - [ ] Yes, confidently
   - [ ] Yes, with some reference
   - [ ] Not yet, need more practice

3. **Can you handle form submission and validation?**
   - [ ] Yes, confidently
   - [ ] Yes, with some reference
   - [ ] Not yet, need more practice

4. **Do you understand conditional rendering and list rendering?**
   - [ ] Yes, confidently
   - [ ] Yes, with some reference
   - [ ] Not yet, need more practice

### Today's Wins
*Write about your biggest accomplishment today:*

*Your answer:*

### Challenges Faced
*What was the most difficult concept today and how did you overcome it?*

*Your answer:*

### Key Insights
*What "aha" moments did you have about React state management?*

*Your answer:*

---

## 📝 Code Snippets & Notes
*Use this space to jot down important code snippets or concepts:*

```javascript
// Example: useState pattern
const [count, setCount] = useState(0);

// Example: Event handler
const handleClick = () => {
  setCount(prev => prev + 1);
};

// Example: Controlled input
const handleInputChange = (e) => {
  setValue(e.target.value);
};
```

*Your notes:*

---

## 🔄 Connection to Day 1
*How did today's learning build on yesterday's concepts?*

*Your answer:*

---

## ✅ Daily Checklist
- [ ] Completed all reading/video materials
- [ ] Answered all learning questions
- [ ] Built all four practice projects
- [ ] Completed code challenges
- [ ] Completed end-of-day assessment
- [ ] Reviewed and connected to Day 1 concepts
- [ ] Prepared notes for tomorrow

**Time spent today:** _____ hours

**Confidence level for Day 3:** [ ] Ready [ ] Need review [ ] Need more practice

**Areas to review before Day 3:**
*List any topics you want to revisit:*
