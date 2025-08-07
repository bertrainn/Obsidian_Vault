# React Quick Reference for Offline Learning

## 🚀 Essential React Patterns

### Component Creation

```javascript
// Functional Component
function MyComponent({ name, age }) {
  return (
    <div>
      <h1>Hello {name}</h1>
      <p>Age: {age}</p>
    </div>
  );
}

// Arrow Function Component
const MyComponent = ({ name, age }) => {
  return (
    <div>
      <h1>Hello {name}</h1>
      <p>Age: {age}</p>
    </div>
  );
};
```

### State Management

```javascript
import { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
      <button onClick={() => setCount((prev) => prev + 1)}>
        Increment (safer)
      </button>
    </div>
  );
}
```

### Event Handling

```javascript
function FormComponent() {
  const [input, setInput] = useState("");

  const handleSubmit = (e) => {
    e.preventDefault();
    console.log("Submitted:", input);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input
        value={input}
        onChange={(e) => setInput(e.target.value)}
        placeholder="Type something..."
      />
      <button type="submit">Submit</button>
    </form>
  );
}
```

### useEffect Hook

```javascript
import { useState, useEffect } from "react";

function DataComponent() {
  const [data, setData] = useState(null);

  // Component mount
  useEffect(() => {
    console.log("Component mounted");
  }, []);

  // When data changes
  useEffect(() => {
    if (data) {
      console.log("Data updated:", data);
    }
  }, [data]);

  // Cleanup
  useEffect(() => {
    const timer = setInterval(() => {
      console.log("Timer tick");
    }, 1000);

    return () => clearInterval(timer);
  }, []);

  return <div>{data || "Loading..."}</div>;
}
```

### Conditional Rendering

```javascript
function ConditionalComponent({ isLoggedIn, user }) {
  // If-else
  if (isLoggedIn) {
    return <h1>Welcome, {user.name}!</h1>;
  } else {
    return <h1>Please log in</h1>;
  }

  // Ternary operator
  return (
    <div>
      {isLoggedIn ? <h1>Welcome, {user.name}!</h1> : <h1>Please log in</h1>}
    </div>
  );

  // Logical AND
  return (
    <div>
      {isLoggedIn && <h1>Welcome, {user.name}!</h1>}
      {!isLoggedIn && <h1>Please log in</h1>}
    </div>
  );
}
```

### List Rendering

```javascript
function TodoList({ todos }) {
  return (
    <ul>
      {todos.map((todo) => (
        <li key={todo.id}>
          <span className={todo.completed ? "completed" : ""}>{todo.text}</span>
          <button onClick={() => toggleTodo(todo.id)}>
            {todo.completed ? "Undo" : "Complete"}
          </button>
        </li>
      ))}
    </ul>
  );
}
```

---

## 🛠️ Quick Setup Commands

### Create New React App

```bash
# Create React App
npx create-react-app my-app
cd my-app
npm start

# Vite (faster)
npm create vite@latest my-react-app -- --template react
cd my-react-app
npm install
npm run dev
```

### Useful npm Commands

```bash
# Install dependencies
npm install

# Start development server
npm start

# Build for production
npm run build

# Run tests
npm test

# Install specific packages
npm install react-router-dom
npm install axios
npm install styled-components
```

---

## 📝 Common Patterns for Practice

### Simple Calculator

```javascript
function Calculator() {
  const [display, setDisplay] = useState("0");
  const [operation, setOperation] = useState(null);
  const [waitingForOperand, setWaitingForOperand] = useState(false);
  const [value, setValue] = useState(null);

  const inputNumber = (num) => {
    if (waitingForOperand) {
      setDisplay(String(num));
      setWaitingForOperand(false);
    } else {
      setDisplay(display === "0" ? String(num) : display + num);
    }
  };

  const inputOperation = (nextOperation) => {
    const inputValue = parseFloat(display);

    if (value === null) {
      setValue(inputValue);
    } else if (operation) {
      const currentValue = value || 0;
      const newValue = calculate(currentValue, inputValue, operation);

      setDisplay(String(newValue));
      setValue(newValue);
    }

    setWaitingForOperand(true);
    setOperation(nextOperation);
  };

  return (
    <div className="calculator">
      <div className="display">{display}</div>
      {/* Calculator buttons here */}
    </div>
  );
}
```

### Todo App

```javascript
function TodoApp() {
  const [todos, setTodos] = useState([]);
  const [newTodo, setNewTodo] = useState("");

  const addTodo = () => {
    if (newTodo.trim()) {
      setTodos([
        ...todos,
        {
          id: Date.now(),
          text: newTodo,
          completed: false,
        },
      ]);
      setNewTodo("");
    }
  };

  const toggleTodo = (id) => {
    setTodos(
      todos.map((todo) =>
        todo.id === id ? { ...todo, completed: !todo.completed } : todo
      )
    );
  };

  const deleteTodo = (id) => {
    setTodos(todos.filter((todo) => todo.id !== id));
  };

  return (
    <div>
      <input
        value={newTodo}
        onChange={(e) => setNewTodo(e.target.value)}
        placeholder="Add new todo..."
      />
      <button onClick={addTodo}>Add</button>

      <ul>
        {todos.map((todo) => (
          <li key={todo.id}>
            <span
              className={todo.completed ? "completed" : ""}
              onClick={() => toggleTodo(todo.id)}
            >
              {todo.text}
            </span>
            <button onClick={() => deleteTodo(todo.id)}>Delete</button>
          </li>
        ))}
      </ul>
    </div>
  );
}
```

---

## 🎯 Coding Challenges for Flights

### Beginner Challenges (30 min each)

1. **Counter with multiple buttons** (increment, decrement, reset, custom step)
2. **Color picker** (RGB sliders, hex display, color preview)
3. **Simple form** (validation, error messages, success state)
4. **Image gallery** (next/prev buttons, image counter)

### Intermediate Challenges (1 hour each)

1. **Weather dashboard** (mock data, multiple cities, unit conversion)
2. **Shopping cart** (add/remove items, quantity, total calculation)
3. **Task manager** (categories, filters, search, priority levels)
4. **Memory card game** (card flipping, score tracking, timer)

### Advanced Challenges (2+ hours)

1. **Mini social media feed** (posts, likes, comments, user profiles)
2. **Dashboard with widgets** (drag & drop, customizable layout)
3. **File manager UI** (folder navigation, file operations, search)
4. **Chat interface** (message bubbles, typing indicators, user list)

---

## 🐛 Common Issues & Solutions

### State Update Issues

```javascript
// ❌ Wrong - direct mutation
const [items, setItems] = useState([]);
items.push(newItem); // Don't do this

// ✅ Correct - create new array
setItems([...items, newItem]);

// ❌ Wrong - updating based on current state
setCount(count + 1);

// ✅ Correct - using function form
setCount((prev) => prev + 1);
```

### Key Prop Issues

```javascript
// ❌ Wrong - using index as key
{
  items.map((item, index) => <Item key={index} data={item} />);
}

// ✅ Correct - using unique identifier
{
  items.map((item) => <Item key={item.id} data={item} />);
}
```

### Event Handler Issues

```javascript
// ❌ Wrong - calling function immediately
<button onClick={handleClick()}>Click me</button>

// ✅ Correct - passing function reference
<button onClick={handleClick}>Click me</button>

// ✅ Correct - using arrow function
<button onClick={() => handleClick(param)}>Click me</button>
```

---

## 📚 Study Schedule for Different Flight Lengths

### 2-Hour Flight

- **30 min:** Review fundamentals
- **60 min:** Build simple calculator
- **30 min:** Practice component patterns

### 4-Hour Flight

- **45 min:** React concepts review
- **90 min:** Build todo application
- **60 min:** Add advanced features
- **45 min:** Code cleanup and documentation

### 6+ Hour Flight

- **60 min:** Comprehensive review
- **120 min:** Build substantial project
- **90 min:** Add complex features
- **60 min:** Testing and optimization
- **30+ min:** Plan next steps

---

**Happy coding at 30,000 feet! ✈️👨‍💻**
