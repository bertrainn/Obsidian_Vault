# Complete Offline React + TypeScript Tutorial: From Zero to Hero

## 📚 Table of Contents

1. [Getting Started - Setting Up Your TypeScript Environment](#1-getting-started)
2. [Chapter 1: Your First React TypeScript Component](#2-chapter-1-your-first-react-typescript-component)
3. [Chapter 2: Understanding TSX and TypeScript Basics](#3-chapter-2-understanding-tsx-and-typescript-basics)
4. [Chapter 3: Props with TypeScript Types](#4-chapter-3-props-with-typescript-types)
5. [Chapter 4: State and Event Handling with Types](#5-chapter-4-state-and-event-handling-with-types)
6. [Chapter 5: Lists and Conditional Rendering with TypeScript](#6-chapter-5-lists-and-conditional-rendering-with-typescript)
7. [Chapter 6: Forms and User Input with Type Safety](#7-chapter-6-forms-and-user-input-with-type-safety)
8. [Chapter 7: useEffect and Side Effects with TypeScript](#8-chapter-7-useeffect-and-side-effects-with-typescript)
9. [Chapter 8: Custom Hooks with TypeScript](#9-chapter-8-custom-hooks-with-typescript)
10. [Chapter 9: Building Real TypeScript Projects](#10-chapter-9-building-real-typescript-projects)

---

## 1. Getting Started - Setting Up Your TypeScript Environment

### Prerequisites

Before we begin, make sure you have:

- Node.js installed (version 14 or higher)
- A code editor (VS Code recommended with TypeScript support)
- Basic knowledge of HTML, CSS, and JavaScript
- **Why TypeScript?** TypeScript adds type safety, better IDE support, and catches errors at compile time!

### Setting Up Your First React TypeScript Project

1. Open your terminal/command prompt
2. Create a new React project with TypeScript:

```bash
npx create-react-app my-first-react-ts-app --template typescript
cd my-first-react-ts-app
npm start
```

3. Your browser should open to `http://localhost:3000` showing the React welcome page

### Project Structure Overview

```
my-first-react-ts-app/
├── public/
│   ├── index.html
│   └── favicon.ico
├── src/
│   ├── App.tsx          # Main component (TypeScript!)
│   ├── App.css
│   ├── index.tsx        # Entry point (TypeScript!)
│   ├── index.css
│   └── react-app-env.d.ts # TypeScript declarations
├── package.json
└── tsconfig.json        # TypeScript configuration
```

**Key Files:**

- `src/index.tsx` - Entry point of your React app (TypeScript)
- `src/App.tsx` - Main component (TypeScript)
- `tsconfig.json` - TypeScript configuration
- `public/index.html` - HTML template

### TypeScript Configuration (tsconfig.json)

Your project comes with a pre-configured `tsconfig.json`. Key settings:

```json
{
  "compilerOptions": {
    "target": "es5",
    "lib": ["dom", "dom.iterable", "es6"],
    "allowJs": true,
    "skipLibCheck": true,
    "esModuleInterop": true,
    "allowSyntheticDefaultImports": true,
    "strict": true, // Enables strict type checking
    "forceConsistentCasingInFileNames": true,
    "module": "esnext",
    "moduleResolution": "node",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "noEmit": true,
    "jsx": "react-jsx" // Enables TSX
  },
  "include": ["src"]
}
```

---

## 2. Chapter 1: Your First TypeScript React Component

### TypeScript Fundamentals for React

Before we dive into components, let's understand the key TypeScript concepts you'll use throughout this tutorial:

#### 1. **Type Annotations**

```tsx
// Basic types
const name: string = "John";
const age: number = 25;
const isActive: boolean = true;
const hobbies: string[] = ["reading", "coding"];
const user: { name: string; age: number } = { name: "John", age: 25 };
```

#### 2. **Interfaces** - Define object shapes

```tsx
interface User {
  name: string;
  age: number;
  email?: string; // Optional property
  hobbies: string[];
}

const user: User = {
  name: "John",
  age: 25,
  hobbies: ["reading", "coding"],
  // email is optional, so we can omit it
};
```

#### 3. **Union Types** - Multiple possible types

```tsx
type Status = "loading" | "success" | "error";
type ButtonSize = "small" | "medium" | "large";

const status: Status = "loading";
const buttonSize: ButtonSize = "medium";
```

#### 4. **React.FC** - TypeScript component type

```tsx
import React from "react";

const MyComponent: React.FC = () => {
  return <div>Hello TypeScript!</div>;
};
```

#### 5. **Event Handlers** - Properly typed events

```tsx
const handleClick = (e: React.MouseEvent<HTMLButtonElement>): void => {
  console.log("Button clicked!");
};

const handleInputChange = (e: React.ChangeEvent<HTMLInputElement>): void => {
  console.log("Input value:", e.target.value);
};
```

### What is a Component?

A component is like a LEGO block - a reusable piece of UI that you can combine with other components to build complex interfaces. With TypeScript, we add type safety to make our components more reliable!

### Exercise 1.1: Create Your First TypeScript Component

**Step 1:** Open `src/App.tsx` and replace everything with:

```tsx
import React from "react";
import "./App.css";

const App: React.FC = () => {
  const appTitle: string = "Hello, TypeScript React World!";
  const isLearning: boolean = true;

  return (
    <div className="App">
      <h1>{appTitle}</h1>
      <p>This is my first React component with TypeScript!</p>
      {isLearning && <p>🎉 You're learning TypeScript + React!</p>}
    </div>
  );
};

export default App;
```

**Step 2:** Save the file and check your browser - you should see your message!

**TypeScript Benefits You Just Used:**

- `React.FC` - Type annotation for functional components
- `string` and `boolean` - Explicit type declarations
- Type checking prevents runtime errors

### Exercise 1.2: Create a Separate TypeScript Component

**Step 1:** Create a new file `src/Welcome.tsx`:

```tsx
import React from "react";

interface WelcomeProps {
  userName?: string; // Optional prop
  learningTopic: string; // Required prop
}

const Welcome: React.FC<WelcomeProps> = ({
  userName = "Developer",
  learningTopic,
}) => {
  const encouragements: string[] = [
    "You're doing great!",
    "Keep it up!",
    "TypeScript makes React better!",
  ];

  const randomEncouragement: string =
    encouragements[Math.floor(Math.random() * encouragements.length)];

  return (
    <div
      style={{
        backgroundColor: "#f0f8ff",
        padding: "20px",
        borderRadius: "8px",
        margin: "10px 0",
      }}
    >
      <h2>
        Welcome to {learningTopic}, {userName}!
      </h2>
      <p>{randomEncouragement}</p>
      <small>💡 This component uses TypeScript interfaces for props!</small>
    </div>
  );
};

export default Welcome;
```

**Step 2:** Import and use it in `App.tsx`:

```tsx
import React from "react";
import Welcome from "./Welcome";
import "./App.css";

const App: React.FC = () => {
  const appTitle: string = "Hello, TypeScript React World!";
  const currentUser: string = "Future React Developer";

  return (
    <div className="App">
      <h1>{appTitle}</h1>
      <Welcome learningTopic="React + TypeScript" userName={currentUser} />
      <Welcome learningTopic="Modern Web Development" />
    </div>
  );
};

export default App;
```

**TypeScript Magic:** Notice how TypeScript helps you:

- ✅ `learningTopic` is required - TypeScript will error if you forget it
- ✅ `userName` is optional - has a default value
- ✅ IntelliSense shows you available props as you type

### Key TypeScript Concepts Learned:

- **Interfaces**: Define the shape of props with `interface`
- **Optional Props**: Use `?` to make props optional (`userName?: string`)
- **Type Annotations**: Explicitly declare types (`const name: string`)
- **Array Types**: `string[]` for arrays of strings
- **React.FC**: Type for functional components

### TypeScript Benefits You'll Experience:

1. **Compile-time Error Detection**: Catch bugs before runtime
2. **Better IDE Support**: IntelliSense, autocomplete, and refactoring
3. **Self-documenting Code**: Types serve as documentation
4. **Safer Refactoring**: TypeScript ensures changes don't break existing code
5. **Enhanced Team Collaboration**: Clear contracts between components

### TypeScript Best Practices:

```tsx
// ✅ Good - Explicit types
const [count, setCount] = useState<number>(0);
const handleClick = (): void => {
  /* ... */
};

// ❌ Avoid - Type inference when unclear
const [count, setCount] = useState(0); // OK for simple cases
const handleClick = () => {
  /* ... */
}; // Less clear

// ✅ Good - Interface for complex props
interface UserCardProps {
  user: User;
  onEdit?: (id: string) => void;
}

// ✅ Good - Union types for constrained values
type ButtonVariant = "primary" | "secondary" | "danger";
```

### Practice Challenge 1.1:

Create a `PersonCard` component with TypeScript that displays:

- A person's name (required)
- Their job title (required)
- Their age (optional)
- A short bio (required)
- Whether they're available for hire (required boolean)

**Solution:**

```tsx
// src/PersonCard.tsx
import React from "react";

interface Person {
  name: string;
  jobTitle: string;
  age?: number;
  bio: string;
  availableForHire: boolean;
}

interface PersonCardProps {
  person: Person;
  cardColor?: string;
}

const PersonCard: React.FC<PersonCardProps> = ({
  person,
  cardColor = "#ffffff",
}) => {
  const { name, jobTitle, age, bio, availableForHire } = person;

  return (
    <div
      style={{
        border: "2px solid #333",
        padding: "20px",
        margin: "10px",
        borderRadius: "10px",
        backgroundColor: cardColor,
        boxShadow: "0 2px 4px rgba(0,0,0,0.1)",
      }}
    >
      <h3>
        {name} {age && <span style={{ color: "#666" }}>({age})</span>}
      </h3>
      <p>
        <strong>Job:</strong> {jobTitle}
      </p>
      <p>
        <strong>Bio:</strong> {bio}
      </p>
      <div
        style={{
          display: "inline-block",
          padding: "4px 8px",
          borderRadius: "4px",
          backgroundColor: availableForHire ? "#4CAF50" : "#f44336",
          color: "white",
          fontSize: "12px",
        }}
      >
        {availableForHire ? "✅ Available for hire" : "❌ Not available"}
      </div>
    </div>
  );
};

export default PersonCard;
```

**Usage in App.tsx:**

```tsx
import PersonCard from "./PersonCard";

const samplePerson: Person = {
  name: "Sarah Johnson",
  jobTitle: "Frontend Developer",
  age: 28,
  bio: "Passionate about creating amazing user experiences with React and TypeScript!",
  availableForHire: true,
};

// In your component's return:
<PersonCard person={samplePerson} cardColor="#e3f2fd" />;
```

---

## 3. Chapter 2: Understanding TSX (TypeScript JSX)

### What is TSX?

TSX is TypeScript's version of JSX - it's a syntax extension that lets you write HTML-like code in your TypeScript files with full type safety!

### TSX Rules You Must Know:

#### Rule 1: Return a Single Parent Element

```tsx
// ❌ Wrong - Multiple elements without a parent
const BadComponent: React.FC = () => {
  return (
    <h1>Title</h1>
    <p>Paragraph</p>
  );
}

// ✅ Correct - Wrapped in a div
const GoodComponent: React.FC = () => {
  return (
    <div>
      <h1>Title</h1>
      <p>Paragraph</p>
    </div>
  );
}

// ✅ Also correct - Using React Fragment
const AnotherGoodComponent: React.FC = () => {
  return (
    <>
      <h1>Title</h1>
      <p>Paragraph</p>
    </>
  );
}
```

#### Rule 2: Use `className` instead of `class`

```tsx
// ❌ Wrong
<div class="my-class">Content</div>

// ✅ Correct
<div className="my-class">Content</div>
```

#### Rule 3: Self-closing tags must end with `/>`

```tsx
// ❌ Wrong
<img src="image.jpg">
<br>

// ✅ Correct
<img src="image.jpg" />
<br />
```

#### Rule 4: TypeScript expressions go in curly braces

```tsx
interface User {
  name: string;
  age: number;
}

const GreetingComponent: React.FC = () => {
  const user: User = { name: "Alice", age: 25 };
  const currentYear: number = new Date().getFullYear();

  return (
    <div>
      <h1>Hello, {user.name}!</h1>
      <p>You are {user.age} years old.</p>
      <p>Next year you'll be {user.age + 1}!</p>
      <p>Born in: {currentYear - user.age}</p>
    </div>
  );
};
```

### Exercise 2.1: Practice TSX with TypeScript

Create a `ProfileCard` component that uses TSX expressions with proper typing:

```tsx
// src/ProfileCard.tsx
import React from "react";

interface User {
  name: string;
  age: number;
  profession: string;
  hobbies: string[];
  email?: string; // Optional field
}

interface ProfileCardProps {
  user: User;
  showBirthYear?: boolean;
}

const ProfileCard: React.FC<ProfileCardProps> = ({
  user,
  showBirthYear = true,
}) => {
  const currentYear: number = new Date().getFullYear();
  const birthYear: number = currentYear - user.age;
  const hobbyCount: number = user.hobbies.length;

  // Type-safe array method
  const hobbyList: string = user.hobbies.join(", ");

  return (
    <div
      className="profile-card"
      style={{
        border: "2px solid #4CAF50",
        borderRadius: "12px",
        padding: "20px",
        margin: "16px",
        backgroundColor: "#f9f9f9",
        maxWidth: "400px",
      }}
    >
      <h2 style={{ color: "#2196F3" }}>{user.name}</h2>
      <p>
        <strong>Age:</strong> {user.age}
      </p>
      <p>
        <strong>Profession:</strong> {user.profession}
      </p>
      {showBirthYear && (
        <p>
          <strong>Born in:</strong> {birthYear}
        </p>
      )}
      {user.email && (
        <p>
          <strong>Email:</strong> {user.email}
        </p>
      )}
      <p>
        <strong>Hobbies:</strong> {hobbyList}
      </p>
      <p>
        <strong>Number of hobbies:</strong> {hobbyCount}
      </p>

      {/* Conditional rendering with TypeScript */}
      {hobbyCount > 3 ? (
        <p style={{ color: "#FF9800" }}>🌟 Wow, you have many hobbies!</p>
      ) : (
        <p style={{ color: "#4CAF50" }}>📚 Room for more hobbies!</p>
      )}
    </div>
  );
};

export default ProfileCard;
```

**Usage in App.tsx:**

```tsx
import ProfileCard from "./ProfileCard";

const App: React.FC = () => {
  const sampleUser: User = {
    name: "Sarah Johnson",
    age: 28,
    profession: "UX Designer",
    hobbies: ["Photography", "Hiking", "Reading", "Cooking"],
    email: "sarah@example.com",
  };

  const anotherUser: User = {
    name: "Mike Chen",
    age: 32,
    profession: "Software Engineer",
    hobbies: ["Gaming", "Basketball"],
  };

  return (
    <div className="App">
      <h1>User Profiles</h1>
      <ProfileCard user={sampleUser} showBirthYear={true} />
      <ProfileCard user={anotherUser} showBirthYear={false} />
    </div>
  );
};
```

### Exercise 2.2: Styling with TSX and TypeScript

```tsx
// src/StyledComponent.tsx
import React from "react";

interface StyleProps {
  backgroundColor?: string;
  textColor?: string;
}

interface StyledComponentProps {
  title: string;
  description: string;
  styling?: StyleProps;
}

const StyledComponent: React.FC<StyledComponentProps> = ({
  title,
  description,
  styling = {},
}) => {
  // Type-safe style objects
  const cardStyle: React.CSSProperties = {
    backgroundColor: styling.backgroundColor || "#f0f0f0",
    padding: "20px",
    borderRadius: "8px",
    margin: "10px",
    boxShadow: "0 2px 4px rgba(0,0,0,0.1)",
    transition: "transform 0.2s ease",
  };

  const titleStyle: React.CSSProperties = {
    color: styling.textColor || "#333",
    fontSize: "24px",
    marginBottom: "10px",
    fontWeight: "bold",
  };

  const textStyle: React.CSSProperties = {
    color: styling.textColor || "#666",
    fontSize: "16px",
    lineHeight: "1.5",
  };

  return (
    <div style={cardStyle}>
      <h2 style={titleStyle}>{title}</h2>
      <p style={textStyle}>{description}</p>
    </div>
  );
};

export default StyledComponent;
```

### Practice Challenge 2.1:

Create a `WeatherCard` component with TypeScript that:

- Shows a city name
- Displays temperature in both Celsius and Fahrenheit
- Shows weather condition with appropriate emoji
- Uses type-safe inline styles

**Solution:**

```tsx
import React from "react";

interface WeatherData {
  city: string;
  tempCelsius: number;
  condition: "Sunny" | "Rainy" | "Cloudy" | "Snowy"; // Union type for valid conditions
  humidity?: number;
}

interface WeatherCardProps {
  weather: WeatherData;
  showHumidity?: boolean;
}

const WeatherCard: React.FC<WeatherCardProps> = ({
  weather,
  showHumidity = false,
}) => {
  const tempFahrenheit: number = Math.round((weather.tempCelsius * 9) / 5 + 32);

  // Type-safe condition mapping
  const weatherEmojis: Record<WeatherData["condition"], string> = {
    Sunny: "☀️",
    Rainy: "🌧️",
    Cloudy: "☁️",
    Snowy: "❄️",
  };

  const cardStyle: React.CSSProperties = {
    backgroundColor: getBackgroundColor(weather.condition),
    padding: "20px",
    borderRadius: "10px",
    textAlign: "center",
    color: "white",
    minWidth: "250px",
    boxShadow: "0 4px 8px rgba(0,0,0,0.2)",
  };

  function getBackgroundColor(condition: WeatherData["condition"]): string {
    const colors: Record<WeatherData["condition"], string> = {
      Sunny: "#87CEEB",
      Rainy: "#778899",
      Cloudy: "#696969",
      Snowy: "#B0C4DE",
    };
    return colors[condition];
  }

  return (
    <div style={cardStyle}>
      <h2>
        {weather.city} {weatherEmojis[weather.condition]}
      </h2>
      <h3>
        {weather.tempCelsius}°C / {tempFahrenheit}°F
      </h3>
      <p>{weather.condition}</p>
      {showHumidity && weather.humidity && <p>Humidity: {weather.humidity}%</p>}
    </div>
  );
};

export default WeatherCard;
```

**Usage:**

```tsx
const weatherData: WeatherData = {
  city: "New York",
  tempCelsius: 22,
  condition: "Sunny",
  humidity: 65,
};

<WeatherCard weather={weatherData} showHumidity={true} />;
```

### TypeScript Benefits in This Chapter:

- ✅ **Type-safe props**: Interface definitions prevent wrong data types
- ✅ **Union types**: `'Sunny' | 'Rainy'` restricts to valid values only
- ✅ **Optional properties**: `humidity?: number` for flexible data
- ✅ **React.CSSProperties**: Type-safe inline styles
- ✅ **Record types**: Type-safe object mapping for emojis and colors

---

## 5. Chapter 4: State and Event Handling

### What is State?

State is like a component's memory - it remembers information that can change over time.

### Exercise 4.1: Your First State with TypeScript

```tsx
// src/Counter.tsx
import React, { useState } from "react";

const Counter: React.FC = () => {
  // useState with TypeScript - type is inferred as number
  const [count, setCount] = useState<number>(0);

  const handleIncrement = (): void => {
    setCount((prevCount) => prevCount + 1);
  };

  const handleDecrement = (): void => {
    setCount((prevCount) => prevCount - 1);
  };

  const handleReset = (): void => {
    setCount(0);
  };

  return (
    <div>
      <h2>Counter: {count}</h2>
      <button onClick={handleIncrement}>Increment</button>
      <button onClick={handleDecrement}>Decrement</button>
      <button onClick={handleReset}>Reset</button>
    </div>
  );
};

export default Counter;
```

### Exercise 4.2: State with Different Data Types in TypeScript

```tsx
// src/UserProfile.tsx
import React, { useState } from "react";

interface User {
  name: string;
  age: number;
  hobbies: string[];
}

const UserProfile: React.FC = () => {
  const [name, setName] = useState<string>("");
  const [age, setAge] = useState<number>(0);
  const [hobbies, setHobbies] = useState<string[]>([]);
  const [isVisible, setIsVisible] = useState<boolean>(true);

  const addHobby = (): void => {
    const newHobby: string | null = prompt("Enter a hobby:");
    if (newHobby && newHobby.trim()) {
      setHobbies((prevHobbies) => [...prevHobbies, newHobby.trim()]);
    }
  };

  const removeHobby = (indexToRemove: number): void => {
    setHobbies((prevHobbies) =>
      prevHobbies.filter((_, index) => index !== indexToRemove)
    );
  };

  const handleNameChange = (e: React.ChangeEvent<HTMLInputElement>): void => {
    setName(e.target.value);
  };

  const handleAgeChange = (e: React.ChangeEvent<HTMLInputElement>): void => {
    const value: number = parseInt(e.target.value) || 0;
    setAge(value);
  };

  const toggleVisibility = (): void => {
    setIsVisible((prev) => !prev);
  };

  if (!isVisible) {
    return (
      <div>
        <button onClick={toggleVisibility}>Show Profile</button>
      </div>
    );
  }

  return (
    <div style={{ padding: "20px", border: "1px solid #ccc" }}>
      <button onClick={toggleVisibility}>Hide Profile</button>

      <div>
        <label>Name: </label>
        <input
          value={name}
          onChange={handleNameChange}
          placeholder="Enter your name"
        />
      </div>

      <div>
        <label>Age: </label>
        <input type="number" value={age} onChange={handleAgeChange} />
      </div>

      <div>
        <h3>Profile:</h3>
        <p>Name: {name || "Not provided"}</p>
        <p>Age: {age}</p>
      </div>

      <div>
        <h3>Hobbies:</h3>
        <button onClick={addHobby}>Add Hobby</button>
        <ul>
          {hobbies.map((hobby: string, index: number) => (
            <li key={index}>
              {hobby}
              <button onClick={() => removeHobby(index)}>Remove</button>
            </li>
          ))}
        </ul>
      </div>
    </div>
  );
};

export default UserProfile;
```

### Exercise 4.3: Event Handling with TypeScript

```tsx
// src/EventDemo.tsx
import React, { useState } from "react";

const EventDemo: React.FC = () => {
  const [message, setMessage] = useState<string>("");
  const [clickCount, setClickCount] = useState<number>(0);
  const [inputValue, setInputValue] = useState<string>("");

  const handleClick = (): void => {
    setClickCount((prevCount) => prevCount + 1);
    setMessage(`Button clicked ${clickCount + 1} times!`);
  };

  const handleInputChange = (
    event: React.ChangeEvent<HTMLInputElement>
  ): void => {
    setInputValue(event.target.value);
  };

  const handleSubmit = (event: React.FormEvent<HTMLFormElement>): void => {
    event.preventDefault(); // Prevents page reload
    alert(`You entered: ${inputValue}`);
    setInputValue(""); // Clear the input
  };

  const handleKeyPress = (
    event: React.KeyboardEvent<HTMLInputElement>
  ): void => {
    if (event.key === "Enter") {
      setMessage(`You pressed Enter! Input value: ${inputValue}`);
    }
  };

  return (
    <div style={{ padding: "20px" }}>
      <h2>Event Handling Demo</h2>

      <div>
        <button onClick={handleClick}>
          Click me! (Clicked {clickCount} times)
        </button>
        <p>{message}</p>
      </div>

      <form onSubmit={handleSubmit}>
        <input
          type="text"
          value={inputValue}
          onChange={handleInputChange}
          onKeyPress={handleKeyPress}
          placeholder="Type something and press Enter or submit"
        />
        <button type="submit">Submit</button>
      </form>

      <p>Current input: {inputValue}</p>
    </div>
  );
};

export default EventDemo;
```

### Practice Challenge 4.1:

Create a `ColorPicker` component that:

- Has buttons for Red, Green, Blue, Yellow
- Changes background color when buttons are clicked
- Shows the current color name
- Has a reset button to go back to white

**Solution:**

```tsx
// src/ColorPicker.tsx
import React, { useState } from "react";

interface Color {
  name: string;
  value: string;
}

const ColorPicker: React.FC = () => {
  const [currentColor, setCurrentColor] = useState<string>("white");

  const colors: Color[] = [
    { name: "Red", value: "#ff0000" },
    { name: "Green", value: "#00ff00" },
    { name: "Blue", value: "#0000ff" },
    { name: "Yellow", value: "#ffff00" },
  ];

  const containerStyle: React.CSSProperties = {
    padding: "20px",
    backgroundColor: currentColor,
    minHeight: "200px",
    border: "2px solid #ccc",
    textAlign: "center",
  };

  const handleColorChange = (colorValue: string): void => {
    setCurrentColor(colorValue);
  };

  const handleReset = (): void => {
    setCurrentColor("white");
  };

  return (
    <div style={containerStyle}>
      <h2>Color Picker</h2>
      <p>Current Color: {currentColor}</p>

      <div>
        {colors.map((color: Color) => (
          <button
            key={color.name}
            onClick={() => handleColorChange(color.value)}
            style={{ margin: "5px", padding: "10px" }}
          >
            {color.name}
          </button>
        ))}

        <button
          onClick={handleReset}
          style={{ margin: "5px", padding: "10px" }}
        >
          Reset
        </button>
      </div>
    </div>
  );
};

export default ColorPicker;
```

---

## 6. Chapter 5: Lists and Conditional Rendering

### Rendering Lists

Lists are everywhere in web applications. Here's how to render them in React:

### Exercise 5.1: Basic List Rendering

```tsx
// src/ShoppingList.tsx
import React, { useState } from "react";

interface ShoppingItem {
  id: number;
  name: string;
  bought: boolean;
}

const ShoppingList: React.FC = () => {
  const [items, setItems] = useState<ShoppingItem[]>([
    { id: 1, name: "Apples", bought: false },
    { id: 2, name: "Bread", bought: true },
    { id: 3, name: "Milk", bought: false },
    { id: 4, name: "Eggs", bought: false },
  ]);

  const toggleItem = (id: number): void => {
    setItems(
      items.map((item) =>
        item.id === id ? { ...item, bought: !item.bought } : item
      )
    );
  };

  return (
    <div style={{ padding: "20px" }}>
      <h2>Shopping List</h2>
      <ul style={{ listStyle: "none", padding: 0 }}>
        {items.map((item: ShoppingItem) => (
          <li
            key={item.id}
            style={{
              padding: "10px",
              margin: "5px 0",
              backgroundColor: item.bought ? "#d4edda" : "#f8f9fa",
              border: "1px solid #ccc",
              borderRadius: "4px",
              cursor: "pointer",
            }}
            onClick={() => toggleItem(item.id)}
          >
            <span
              style={{
                textDecoration: item.bought ? "line-through" : "none",
              }}
            >
              {item.name}
            </span>
            {item.bought && " ✓"}
          </li>
        ))}
      </ul>
    </div>
  );
};

export default ShoppingList;
```

### Exercise 5.2: Conditional Rendering

```tsx
// src/UserDashboard.tsx
import React, { useState } from "react";

interface User {
  id: number;
  name: string;
  email: string;
  role: "admin" | "user";
  notifications: number;
}

const UserDashboard: React.FC = () => {
  const [user, setUser] = useState<User | null>(null);
  const [loading, setLoading] = useState<boolean>(false);

  const loginUser = (): void => {
    setLoading(true);
    // Simulate API call
    setTimeout(() => {
      setUser({
        id: 1,
        name: "John Doe",
        email: "john@example.com",
        role: "admin",
        notifications: 3,
      });
      setLoading(false);
    }, 2000);
  };

  const logoutUser = (): void => {
    setUser(null);
  };

  // Loading state
  if (loading) {
    return (
      <div style={{ textAlign: "center", padding: "50px" }}>
        <h2>Loading...</h2>
        <div>Please wait while we log you in.</div>
      </div>
    );
  }

  // Not logged in state
  if (!user) {
    return (
      <div style={{ textAlign: "center", padding: "50px" }}>
        <h2>Welcome!</h2>
        <p>Please log in to access your dashboard.</p>
        <button
          onClick={loginUser}
          style={{ padding: "10px 20px", fontSize: "16px" }}
        >
          Login
        </button>
      </div>
    );
  }

  // Logged in state
  return (
    <div style={{ padding: "20px" }}>
      <header
        style={{
          display: "flex",
          justifyContent: "space-between",
          alignItems: "center",
          borderBottom: "1px solid #ccc",
          paddingBottom: "10px",
        }}
      >
        <h1>Dashboard</h1>
        <div>
          <span>Welcome, {user.name}!</span>
          <button
            onClick={logoutUser}
            style={{ marginLeft: "10px", padding: "5px 10px" }}
          >
            Logout
          </button>
        </div>
      </header>

      <div style={{ marginTop: "20px" }}>
        <div
          style={{
            display: "grid",
            gridTemplateColumns: "repeat(auto-fit, minmax(200px, 1fr))",
            gap: "20px",
          }}
        >
          <div
            style={{
              padding: "20px",
              border: "1px solid #ccc",
              borderRadius: "8px",
            }}
          >
            <h3>Profile</h3>
            <p>Name: {user.name}</p>
            <p>Email: {user.email}</p>
            <p>Role: {user.role}</p>
          </div>

          <div
            style={{
              padding: "20px",
              border: "1px solid #ccc",
              borderRadius: "8px",
            }}
          >
            <h3>Notifications</h3>
            {user.notifications > 0 ? (
              <p style={{ color: "red" }}>
                You have {user.notifications} new notifications!
              </p>
            ) : (
              <p style={{ color: "green" }}>No new notifications</p>
            )}
          </div>

          {user.role === "admin" && (
            <div
              style={{
                padding: "20px",
                border: "1px solid #ccc",
                borderRadius: "8px",
              }}
            >
              <h3>Admin Panel</h3>
              <p>You have admin access!</p>
              <button>Manage Users</button>
            </div>
          )}
        </div>
      </div>
    </div>
  );
};

export default UserDashboard;
```

### Exercise 5.3: Dynamic Lists with Add/Remove

```tsx
// src/TodoApp.tsx
import React, { useState } from "react";

interface Todo {
  id: number;
  text: string;
  completed: boolean;
  createdAt: string;
}

type FilterType = "all" | "active" | "completed";

const TodoApp: React.FC = () => {
  const [todos, setTodos] = useState<Todo[]>([]);
  const [inputValue, setInputValue] = useState<string>("");
  const [filter, setFilter] = useState<FilterType>("all");

  const addTodo = (): void => {
    if (inputValue.trim()) {
      const newTodo: Todo = {
        id: Date.now(),
        text: inputValue.trim(),
        completed: false,
        createdAt: new Date().toLocaleString(),
      };
      setTodos([...todos, newTodo]);
      setInputValue("");
    }
  };

  const toggleTodo = (id: number): void => {
    setTodos(
      todos.map((todo) =>
        todo.id === id ? { ...todo, completed: !todo.completed } : todo
      )
    );
  };

  const deleteTodo = (id: number): void => {
    setTodos(todos.filter((todo) => todo.id !== id));
  };

  const clearCompleted = (): void => {
    setTodos(todos.filter((todo) => !todo.completed));
  };

  const getFilteredTodos = (): Todo[] => {
    switch (filter) {
      case "active":
        return todos.filter((todo) => !todo.completed);
      case "completed":
        return todos.filter((todo) => todo.completed);
      default:
        return todos;
    }
  };

  const handleInputChange = (e: React.ChangeEvent<HTMLInputElement>): void => {
    setInputValue(e.target.value);
  };

  const handleKeyPress = (e: React.KeyboardEvent<HTMLInputElement>): void => {
    if (e.key === "Enter") {
      addTodo();
    }
  };

  const handleFilterChange = (filterType: FilterType): void => {
    setFilter(filterType);
  };

  const filteredTodos = getFilteredTodos();
  const activeCount = todos.filter((todo) => !todo.completed).length;

  return (
    <div style={{ maxWidth: "600px", margin: "0 auto", padding: "20px" }}>
      <h1>Todo App</h1>

      {/* Add Todo */}
      <div style={{ marginBottom: "20px" }}>
        <input
          type="text"
          value={inputValue}
          onChange={handleInputChange}
          onKeyPress={handleKeyPress}
          placeholder="What needs to be done?"
          style={{
            width: "70%",
            padding: "10px",
            fontSize: "16px",
            border: "1px solid #ccc",
            borderRadius: "4px",
          }}
        />
        <button
          onClick={addTodo}
          style={{
            width: "25%",
            padding: "10px",
            marginLeft: "5%",
            fontSize: "16px",
            backgroundColor: "#007bff",
            color: "white",
            border: "none",
            borderRadius: "4px",
            cursor: "pointer",
          }}
        >
          Add
        </button>
      </div>

      {/* Filter Buttons */}
      <div style={{ marginBottom: "20px" }}>
        {(["all", "active", "completed"] as FilterType[]).map((filterType) => (
          <button
            key={filterType}
            onClick={() => handleFilterChange(filterType)}
            style={{
              margin: "0 5px",
              padding: "5px 15px",
              backgroundColor: filter === filterType ? "#007bff" : "#f8f9fa",
              color: filter === filterType ? "white" : "black",
              border: "1px solid #ccc",
              borderRadius: "4px",
              cursor: "pointer",
            }}
          >
            {filterType.charAt(0).toUpperCase() + filterType.slice(1)}
          </button>
        ))}
      </div>

      {/* Todo List */}
      {filteredTodos.length === 0 ? (
        <p style={{ textAlign: "center", color: "#666" }}>
          {filter === "all" ? "No todos yet!" : `No ${filter} todos!`}
        </p>
      ) : (
        <ul style={{ listStyle: "none", padding: 0 }}>
          {filteredTodos.map((todo: Todo) => (
            <li
              key={todo.id}
              style={{
                display: "flex",
                alignItems: "center",
                padding: "15px",
                margin: "5px 0",
                backgroundColor: "#f8f9fa",
                border: "1px solid #dee2e6",
                borderRadius: "4px",
              }}
            >
              <input
                type="checkbox"
                checked={todo.completed}
                onChange={() => toggleTodo(todo.id)}
                style={{ marginRight: "10px" }}
              />
              <div style={{ flex: 1 }}>
                <span
                  style={{
                    textDecoration: todo.completed ? "line-through" : "none",
                    color: todo.completed ? "#6c757d" : "black",
                    fontSize: "16px",
                  }}
                >
                  {todo.text}
                </span>
                <div style={{ fontSize: "12px", color: "#6c757d" }}>
                  Created: {todo.createdAt}
                </div>
              </div>
              <button
                onClick={() => deleteTodo(todo.id)}
                style={{
                  backgroundColor: "#dc3545",
                  color: "white",
                  border: "none",
                  borderRadius: "4px",
                  padding: "5px 10px",
                  cursor: "pointer",
                }}
              >
                Delete
              </button>
            </li>
          ))}
        </ul>
      )}

      {/* Footer */}
      {todos.length > 0 && (
        <div
          style={{
            marginTop: "20px",
            padding: "10px",
            backgroundColor: "#f8f9fa",
            border: "1px solid #dee2e6",
            borderRadius: "4px",
            display: "flex",
            justifyContent: "space-between",
            alignItems: "center",
          }}
        >
          <span>
            {activeCount} item{activeCount !== 1 ? "s" : ""} left
          </span>
          <button
            onClick={clearCompleted}
            disabled={todos.filter((todo) => todo.completed).length === 0}
            style={{
              backgroundColor: "#6c757d",
              color: "white",
              border: "none",
              borderRadius: "4px",
              padding: "5px 10px",
              cursor: "pointer",
              opacity:
                todos.filter((todo) => todo.completed).length === 0 ? 0.5 : 1,
            }}
          >
            Clear Completed
          </button>
        </div>
      )}
    </div>
  );
};

export default TodoApp;
```

### Practice Challenge 5.1:

Create a `MovieList` component that:

- Displays a list of movies with title, year, and rating
- Allows filtering by rating (All, 8+, 9+)
- Allows sorting by title or year
- Shows "No movies found" when filter returns empty results

---

## 7. Chapter 6: Forms and User Input

### Exercise 6.1: Controlled Components with TypeScript

```tsx
// src/ContactForm.tsx
import React, { useState } from 'react';

interface FormData {
  name: string;
  email: string;
  message: string;
  category: 'general' | 'support' | 'sales' | 'feedback';
  subscribe: boolean;
}

interface FormErrors {
  name?: string;
  email?: string;
  message?: string;
}

const ContactForm: React.FC = () => {
  const [formData, setFormData] = useState<FormData>({
    name: '',
    email: '',
    message: '',
    category: 'general',
    subscribe: false
  });

  const [errors, setErrors] = useState<FormErrors>({});
  const [submitted, setSubmitted] = useState<boolean>(false);

  const handleInputChange = (
    e: React.ChangeEvent<HTMLInputElement | HTMLTextAreaElement | HTMLSelectElement>
  ): void => {
    const { name, value, type } = e.target;
    const checked = (e.target as HTMLInputElement).checked;

    setFormData(prev => ({
      ...prev,
      [name]: type === 'checkbox' ? checked : value
    }));

    // Clear error when user starts typing
    if (errors[name as keyof FormErrors]) {
      setErrors(prev => ({
        ...prev,
        [name]: undefined
      }));
    }
  };

  const validateForm = (): FormErrors => {
    const newErrors: FormErrors = {};

    if (!formData.name.trim()) {
      newErrors.name = 'Name is required';
    }

    if (!formData.email.trim()) {
      newErrors.email = 'Email is required';
    } else if (!/\S+@\S+\.\S+/.test(formData.email)) {
      newErrors.email = 'Please enter a valid email';
    }

    if (!formData.message.trim()) {
      newErrors.message = 'Message is required';
    } else if (formData.message.trim().length < 10) {
      newErrors.message = 'Message must be at least 10 characters';
    }

    return newErrors;
  };

  const handleSubmit = (e: React.FormEvent<HTMLFormElement>): void => {
    e.preventDefault();

    const newErrors = validateForm();

    if (Object.keys(newErrors).length === 0) {
      // Form is valid
      console.log('Form submitted:', formData);
      setSubmitted(true);

      // Reset form after 3 seconds
      setTimeout(() => {
        setFormData({
          name: '',
          email: '',
          message: '',
          category: 'general',
          subscribe: false
        });
        setSubmitted(false);
      }, 3000);
    } else {
      setErrors(newErrors);
    }
  };

  if (submitted) {
    return (
      <div style={{
        textAlign: 'center',
        padding: '50px',
        backgroundColor: '#d4edda',
        border: '1px solid #c3e6cb',
        borderRadius: '8px',
        margin: '20px'
      }}>
        <h2>Thank you!</h2>
        <p>Your message has been sent successfully.</p>
        <p>We'll get back to you soon!</p>
      </div>
    );
  }

  return (
    <div style={{ maxWidth: '600px', margin: '0 auto', padding: '20px' }}>
      <h2>Contact Us</h2>

      <form onSubmit={handleSubmit}>
        {/* Name Field */}
        <div style={{ marginBottom: '20px' }}>
          <label style={{ display: 'block', marginBottom: '5px', fontWeight: 'bold' }}>
            Name *
          </label>
          <input
            type="text"
            name="name"
            value={formData.name}
            onChange={handleInputChange}
            style={{
              width: '100%',
              padding: '10px',
              border: `1px solid ${errors.name ? '#dc3545' : '#ccc'},
              borderRadius: '4px',
              fontSize: '16px'
            }}
            placeholder="Enter your full name"
          />
          {errors.name && (
            <div style={{ color: '#dc3545', fontSize: '14px', marginTop: '5px' }}>
              {errors.name}
            </div>
          )}
        </div>

        {/* Email Field */}
        <div style={{ marginBottom: '20px' }}>
          <label style={{ display: 'block', marginBottom: '5px', fontWeight: 'bold' }}>
            Email *
          </label>
          <input
            type="email"
            name="email"
            value={formData.email}
            onChange={handleInputChange}
            style={{
              width: '100%',
              padding: '10px',
              border: `1px solid ${errors.email ? '#dc3545' : '#ccc'}`,
              borderRadius: '4px',
              fontSize: '16px'
            }}
            placeholder="Enter your email address"
          />
          {errors.email && (
            <div style={{ color: '#dc3545', fontSize: '14px', marginTop: '5px' }}>
              {errors.email}
            </div>
          )}
        </div>

        {/* Category Select */}
        <div style={{ marginBottom: '20px' }}>
          <label style={{ display: 'block', marginBottom: '5px', fontWeight: 'bold' }}>
            Category
          </label>
          <select
            name="category"
            value={formData.category}
            onChange={handleInputChange}
            style={{
              width: '100%',
              padding: '10px',
              border: '1px solid #ccc',
              borderRadius: '4px',
              fontSize: '16px'
            }}
          >
            <option value="general">General Inquiry</option>
            <option value="support">Technical Support</option>
            <option value="sales">Sales</option>
            <option value="feedback">Feedback</option>
          </select>
        </div>

        {/* Message Textarea */}
        <div style={{ marginBottom: '20px' }}>
          <label style={{ display: 'block', marginBottom: '5px', fontWeight: 'bold' }}>
            Message *
          </label>
          <textarea
            name="message"
            value={formData.message}
            onChange={handleInputChange}
            rows="5"
            style={{
              width: '100%',
              padding: '10px',
              border: `1px solid ${errors.message ? '#dc3545' : '#ccc'}`,
              borderRadius: '4px',
              fontSize: '16px',
              resize: 'vertical'
            }}
            placeholder="Enter your message here..."
          />
          {errors.message && (
            <div style={{ color: '#dc3545', fontSize: '14px', marginTop: '5px' }}>
              {errors.message}
            </div>
          )}
          <div style={{ fontSize: '12px', color: '#6c757d', marginTop: '5px' }}>
            Characters: {formData.message.length}
          </div>
        </div>

        {/* Subscribe Checkbox */}
        <div style={{ marginBottom: '20px' }}>
          <label style={{ display: 'flex', alignItems: 'center' }}>
            <input
              type="checkbox"
              name="subscribe"
              checked={formData.subscribe}
              onChange={handleInputChange}
              style={{ marginRight: '10px' }}
            />
            Subscribe to our newsletter
          </label>
        </div>

        {/* Submit Button */}
        <button
          type="submit"
          style={{
            backgroundColor: '#007bff',
            color: 'white',
            padding: '12px 30px',
            border: 'none',
            borderRadius: '4px',
            fontSize: '16px',
            cursor: 'pointer',
            width: '100%'
          }}
        >
          Send Message
        </button>
      </form>

      {/* Form Data Preview */}
      <div style={{
        marginTop: '30px',
        padding: '15px',
        backgroundColor: '#f8f9fa',
        border: '1px solid #dee2e6',
        borderRadius: '4px'
      }}>
        <h3>Form Data Preview:</h3>
        <pre style={{ fontSize: '14px' }}>
          {JSON.stringify(formData, null, 2)}
        </pre>
      </div>
    </div>
  );
}

export default ContactForm;
```

---

## 8. Chapter 7: useEffect and Side Effects

### Exercise 7.1: Basic useEffect with TypeScript

```tsx
// src/TimerComponent.tsx
import React, { useState, useEffect } from "react";

const TimerComponent: React.FC = () => {
  const [seconds, setSeconds] = useState<number>(0);
  const [isRunning, setIsRunning] = useState<boolean>(false);

  // Effect that runs when isRunning changes
  useEffect(() => {
    let interval: NodeJS.Timeout | null = null;

    if (isRunning) {
      interval = setInterval(() => {
        setSeconds((prevSeconds) => prevSeconds + 1);
      }, 1000);
    } else {
      if (interval) {
        clearInterval(interval);
      }
    }

    // Cleanup function
    return () => {
      if (interval) {
        clearInterval(interval);
      }
    };
  }, [isRunning]);

  // Effect that runs only once (on mount)
  useEffect(() => {
    console.log("Timer component mounted");

    // Cleanup function (runs on unmount)
    return () => {
      console.log("Timer component unmounted");
    };
  }, []); // Empty dependency array = run once

  const formatTime = (seconds: number): string => {
    const mins: number = Math.floor(seconds / 60);
    const secs: number = seconds % 60;
    return `${mins.toString().padStart(2, "0")}:${secs
      .toString()
      .padStart(2, "0")}`;
  };

  const toggleTimer = (): void => {
    setIsRunning((prev) => !prev);
  };

  const resetTimer = (): void => {
    setSeconds(0);
    setIsRunning(false);
  };

  return (
    <div style={{ textAlign: "center", padding: "20px" }}>
      <h2>Timer</h2>
      <div
        style={{ fontSize: "48px", fontFamily: "monospace", margin: "20px 0" }}
      >
        {formatTime(seconds)}
      </div>

      <div>
        <button
          onClick={toggleTimer}
          style={{
            backgroundColor: isRunning ? "#dc3545" : "#28a745",
            color: "white",
            border: "none",
            padding: "10px 20px",
            margin: "0 5px",
            borderRadius: "4px",
            cursor: "pointer",
          }}
        >
          {isRunning ? "Stop" : "Start"}
        </button>

        <button
          onClick={resetTimer}
          style={{
            backgroundColor: "#6c757d",
            color: "white",
            border: "none",
            padding: "10px 20px",
            margin: "0 5px",
            borderRadius: "4px",
            cursor: "pointer",
          }}
        >
          Reset
        </button>
      </div>
    </div>
  );
};

export default TimerComponent;
```

### Exercise 7.2: Data Fetching Simulation

```tsx
// src/UserList.tsx
import React, { useState, useEffect } from "react";

interface User {
  id: number;
  name: string;
  email: string;
  city: string;
}

// Mock API function (simulates real API call)
const fetchUsers = (): Promise<User[]> => {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve([
        {
          id: 1,
          name: "John Doe",
          email: "john@example.com",
          city: "New York",
        },
        {
          id: 2,
          name: "Jane Smith",
          email: "jane@example.com",
          city: "Los Angeles",
        },
        {
          id: 3,
          name: "Bob Johnson",
          email: "bob@example.com",
          city: "Chicago",
        },
        {
          id: 4,
          name: "Alice Brown",
          email: "alice@example.com",
          city: "Houston",
        },
      ]);
    }, 2000); // 2 second delay to simulate network request
  });
};

const UserList: React.FC = () => {
  const [users, setUsers] = useState<User[]>([]);
  const [loading, setLoading] = useState<boolean>(true);
  const [error, setError] = useState<string | null>(null);
  const [refetchTrigger, setRefetchTrigger] = useState<number>(0);

  useEffect(() => {
    const loadUsers = async (): Promise<void> => {
      try {
        setLoading(true);
        setError(null);

        // Simulate API call
        const userData = await fetchUsers();
        setUsers(userData);
      } catch (err) {
        setError("Failed to load users");
        console.error(err);
      } finally {
        setLoading(false);
      }
    };

    loadUsers();
  }, [refetchTrigger]); // Refetch when refetchTrigger changes

  const handleRefresh = (): void => {
    setRefetchTrigger((prev) => prev + 1);
  };

  if (loading) {
    return (
      <div style={{ textAlign: "center", padding: "50px" }}>
        <h2>Loading Users...</h2>
        <div style={{ fontSize: "20px" }}>⏳</div>
      </div>
    );
  }

  if (error) {
    return (
      <div style={{ textAlign: "center", padding: "50px" }}>
        <h2>Error</h2>
        <p style={{ color: "red" }}>{error}</p>
        <button onClick={handleRefresh}>Try Again</button>
      </div>
    );
  }

  return (
    <div style={{ padding: "20px" }}>
      <div
        style={{
          display: "flex",
          justifyContent: "space-between",
          alignItems: "center",
          marginBottom: "20px",
        }}
      >
        <h2>Users ({users.length})</h2>
        <button
          onClick={handleRefresh}
          style={{
            backgroundColor: "#007bff",
            color: "white",
            border: "none",
            padding: "8px 16px",
            borderRadius: "4px",
            cursor: "pointer",
          }}
        >
          Refresh
        </button>
      </div>

      <div
        style={{
          display: "grid",
          gridTemplateColumns: "repeat(auto-fill, minmax(300px, 1fr))",
          gap: "20px",
        }}
      >
        {users.map((user: User) => (
          <div
            key={user.id}
            style={{
              border: "1px solid #dee2e6",
              borderRadius: "8px",
              padding: "20px",
              backgroundColor: "#f8f9fa",
            }}
          >
            <h3 style={{ margin: "0 0 10px 0" }}>{user.name}</h3>
            <p style={{ margin: "5px 0" }}>📧 {user.email}</p>
            <p style={{ margin: "5px 0" }}>🏙️ {user.city}</p>
          </div>
        ))}
      </div>
    </div>
  );
};

export default UserList;
```

---

## 9. Chapter 8: Custom Hooks

### Exercise 8.1: Creating Your First Custom Hook with TypeScript

```tsx
// src/hooks/useCounter.ts
import { useState } from "react";

interface UseCounterReturn {
  count: number;
  increment: () => void;
  decrement: () => void;
  reset: () => void;
  setValue: (value: number) => void;
}

const useCounter = (initialValue: number = 0): UseCounterReturn => {
  const [count, setCount] = useState<number>(initialValue);

  const increment = (): void => setCount((prev) => prev + 1);
  const decrement = (): void => setCount((prev) => prev - 1);
  const reset = (): void => setCount(initialValue);
  const setValue = (value: number): void => setCount(value);

  return {
    count,
    increment,
    decrement,
    reset,
    setValue,
  };
};

export default useCounter;
```

```tsx
// src/CounterWithHook.tsx
import React from "react";
import useCounter from "./hooks/useCounter";

const CounterWithHook: React.FC = () => {
  const { count, increment, decrement, reset, setValue } = useCounter(10);

  const handleSetToHundred = (): void => {
    setValue(100);
  };

  return (
    <div style={{ textAlign: "center", padding: "20px" }}>
      <h2>Counter with Custom Hook</h2>
      <div style={{ fontSize: "32px", margin: "20px 0" }}>Count: {count}</div>

      <div>
        <button onClick={decrement}>-1</button>
        <button onClick={increment}>+1</button>
        <button onClick={reset}>Reset</button>
        <button onClick={handleSetToHundred}>Set to 100</button>
      </div>
    </div>
  );
};

export default CounterWithHook;
```

### Exercise 8.2: useLocalStorage Hook with TypeScript

```tsx
// src/hooks/useLocalStorage.ts
import { useState, useEffect } from "react";

function useLocalStorage<T>(
  key: string,
  initialValue: T
): [T, (value: T | ((val: T) => T)) => void] {
  // Get value from localStorage or use initial value
  const [storedValue, setStoredValue] = useState<T>(() => {
    try {
      const item = window.localStorage.getItem(key);
      return item ? JSON.parse(item) : initialValue;
    } catch (error) {
      console.error(`Error reading localStorage key "${key}":`, error);
      return initialValue;
    }
  });

  // Return wrapped version of useState's setter function
  const setValue = (value: T | ((val: T) => T)): void => {
    try {
      // Allow value to be a function like useState
      const valueToStore =
        value instanceof Function ? value(storedValue) : value;
      setStoredValue(valueToStore);
      window.localStorage.setItem(key, JSON.stringify(valueToStore));
    } catch (error) {
      console.error(`Error setting localStorage key "${key}":`, error);
    }
  };

  return [storedValue, setValue];
}

export default useLocalStorage;
```

```tsx
// src/SettingsComponent.tsx
import React from "react";
import useLocalStorage from "./hooks/useLocalStorage";

type Theme = "light" | "dark";

interface ThemeStyles {
  backgroundColor: string;
  color: string;
}

const SettingsComponent: React.FC = () => {
  const [theme, setTheme] = useLocalStorage<Theme>("theme", "light");
  const [username, setUsername] = useLocalStorage<string>("username", "");
  const [notifications, setNotifications] = useLocalStorage<boolean>(
    "notifications",
    true
  );

  const themes: Record<Theme, ThemeStyles> = {
    light: { backgroundColor: "#ffffff", color: "#000000" },
    dark: { backgroundColor: "#333333", color: "#ffffff" },
  };

  const handleUsernameChange = (
    e: React.ChangeEvent<HTMLInputElement>
  ): void => {
    setUsername(e.target.value);
  };

  const handleThemeChange = (e: React.ChangeEvent<HTMLSelectElement>): void => {
    setTheme(e.target.value as Theme);
  };

  const handleNotificationChange = (
    e: React.ChangeEvent<HTMLInputElement>
  ): void => {
    setNotifications(e.target.checked);
  };

  return (
    <div
      style={{
        ...themes[theme],
        padding: "20px",
        minHeight: "400px",
        transition: "all 0.3s ease",
      }}
    >
      <h2>Settings (Persisted in LocalStorage)</h2>

      <div style={{ marginBottom: "20px" }}>
        <label style={{ display: "block", marginBottom: "5px" }}>
          Username:
        </label>
        <input
          type="text"
          value={username}
          onChange={handleUsernameChange}
          placeholder="Enter your username"
          style={{ padding: "8px", width: "200px" }}
        />
      </div>

      <div style={{ marginBottom: "20px" }}>
        <label style={{ display: "block", marginBottom: "5px" }}>Theme:</label>
        <select
          value={theme}
          onChange={handleThemeChange}
          style={{ padding: "8px" }}
        >
          <option value="light">Light</option>
          <option value="dark">Dark</option>
        </select>
      </div>

      <div style={{ marginBottom: "20px" }}>
        <label style={{ display: "flex", alignItems: "center" }}>
          <input
            type="checkbox"
            checked={notifications}
            onChange={handleNotificationChange}
            style={{ marginRight: "8px" }}
          />
          Enable notifications
        </label>
      </div>

      <div
        style={{
          padding: "15px",
          border: "1px solid #ccc",
          borderRadius: "4px",
          backgroundColor: theme === "light" ? "#f8f9fa" : "#555555",
        }}
      >
        <h3>Current Settings:</h3>
        <p>Username: {username || "Not set"}</p>
        <p>Theme: {theme}</p>
        <p>Notifications: {notifications ? "Enabled" : "Disabled"}</p>
      </div>
    </div>
  );
};

export default SettingsComponent;
```

---

## 10. Chapter 9: Building Real Projects

### Project 1: Complete Calculator App with TypeScript

```tsx
// src/Calculator.tsx
import React, { useState } from "react";

type Operation = "/" | "*" | "+" | "-" | "=";

interface CalculatorState {
  display: string;
  previousValue: number | null;
  operation: Operation | null;
  waitingForOperand: boolean;
  history: string[];
}

const Calculator: React.FC = () => {
  const [display, setDisplay] = useState<string>("0");
  const [previousValue, setPreviousValue] = useState<number | null>(null);
  const [operation, setOperation] = useState<Operation | null>(null);
  const [waitingForOperand, setWaitingForOperand] = useState<boolean>(false);
  const [history, setHistory] = useState<string[]>([]);

  const inputNumber = (num: number): void => {
    if (waitingForOperand) {
      setDisplay(String(num));
      setWaitingForOperand(false);
    } else {
      setDisplay(display === "0" ? String(num) : display + num);
    }
  };

  const inputDecimal = (): void => {
    if (waitingForOperand) {
      setDisplay("0.");
      setWaitingForOperand(false);
    } else if (display.indexOf(".") === -1) {
      setDisplay(display + ".");
    }
  };

  const clear = (): void => {
    setDisplay("0");
    setPreviousValue(null);
    setOperation(null);
    setWaitingForOperand(false);
  };

  const performCalculation: Record<
    Operation,
    (prevValue: number, nextValue: number) => number
  > = {
    "/": (prevValue, nextValue) => prevValue / nextValue,
    "*": (prevValue, nextValue) => prevValue * nextValue,
    "+": (prevValue, nextValue) => prevValue + nextValue,
    "-": (prevValue, nextValue) => prevValue - nextValue,
    "=": (prevValue, nextValue) => nextValue,
  };

  const calculate = (nextOperation: Operation): void => {
    const inputValue: number = parseFloat(display);

    if (previousValue === null) {
      setPreviousValue(inputValue);
    } else if (operation) {
      const currentValue: number = previousValue || 0;
      const newValue: number = performCalculation[operation](
        currentValue,
        inputValue
      );

      // Add to history
      const calculation: string = `${currentValue} ${operation} ${inputValue} = ${newValue}`;
      setHistory((prev) => [calculation, ...prev.slice(0, 9)]); // Keep last 10

      setDisplay(String(newValue));
      setPreviousValue(newValue);
    }

    setWaitingForOperand(true);
    setOperation(nextOperation);
  };

  const buttonStyle = {
    fontSize: "18px",
    padding: "20px",
    margin: "2px",
    border: "none",
    borderRadius: "4px",
    cursor: "pointer",
    minWidth: "60px",
    minHeight: "60px",
  };

  const numberButtonStyle = {
    ...buttonStyle,
    backgroundColor: "#f8f9fa",
    border: "1px solid #dee2e6",
  };

  const operatorButtonStyle = {
    ...buttonStyle,
    backgroundColor: "#007bff",
    color: "white",
  };

  const specialButtonStyle = {
    ...buttonStyle,
    backgroundColor: "#6c757d",
    color: "white",
  };

  return (
    <div
      style={{
        maxWidth: "400px",
        margin: "0 auto",
        padding: "20px",
        border: "1px solid #ccc",
        borderRadius: "8px",
        backgroundColor: "#f8f9fa",
      }}
    >
      <h2 style={{ textAlign: "center" }}>Calculator</h2>

      {/* Display */}
      <div
        style={{
          backgroundColor: "#000",
          color: "#00ff00",
          padding: "20px",
          marginBottom: "20px",
          borderRadius: "4px",
          fontSize: "24px",
          textAlign: "right",
          fontFamily: "monospace",
          minHeight: "30px",
          wordBreak: "break-all",
        }}
      >
        {display}
      </div>

      {/* Button Grid */}
      <div
        style={{
          display: "grid",
          gridTemplateColumns: "repeat(4, 1fr)",
          gap: "2px",
        }}
      >
        <button style={specialButtonStyle} onClick={clear}>
          C
        </button>
        <button
          style={specialButtonStyle}
          onClick={() => setDisplay(display.slice(0, -1) || "0")}
        >
          ⌫
        </button>
        <button style={operatorButtonStyle} onClick={() => calculate("/")}>
          /
        </button>
        <button style={operatorButtonStyle} onClick={() => calculate("*")}>
          ×
        </button>

        <button style={numberButtonStyle} onClick={() => inputNumber(7)}>
          7
        </button>
        <button style={numberButtonStyle} onClick={() => inputNumber(8)}>
          8
        </button>
        <button style={numberButtonStyle} onClick={() => inputNumber(9)}>
          9
        </button>
        <button style={operatorButtonStyle} onClick={() => calculate("-")}>
          -
        </button>

        <button style={numberButtonStyle} onClick={() => inputNumber(4)}>
          4
        </button>
        <button style={numberButtonStyle} onClick={() => inputNumber(5)}>
          5
        </button>
        <button style={numberButtonStyle} onClick={() => inputNumber(6)}>
          6
        </button>
        <button style={operatorButtonStyle} onClick={() => calculate("+")}>
          +
        </button>

        <button style={numberButtonStyle} onClick={() => inputNumber(1)}>
          1
        </button>
        <button style={numberButtonStyle} onClick={() => inputNumber(2)}>
          2
        </button>
        <button style={numberButtonStyle} onClick={() => inputNumber(3)}>
          3
        </button>
        <button
          style={{ ...operatorButtonStyle, gridRow: "span 2" }}
          onClick={() => calculate("=")}
        >
          =
        </button>

        <button
          style={{ ...numberButtonStyle, gridColumn: "span 2" }}
          onClick={() => inputNumber(0)}
        >
          0
        </button>
        <button style={numberButtonStyle} onClick={inputDecimal}>
          .
        </button>
      </div>

      {/* History */}
      {history.length > 0 && (
        <div style={{ marginTop: "20px" }}>
          <h3>History:</h3>
          <div
            style={{
              maxHeight: "150px",
              overflowY: "auto",
              backgroundColor: "white",
              padding: "10px",
              borderRadius: "4px",
              border: "1px solid #dee2e6",
            }}
          >
            {history.map((calc, index) => (
              <div
                key={index}
                style={{
                  fontSize: "14px",
                  fontFamily: "monospace",
                  padding: "2px 0",
                  borderBottom:
                    index < history.length - 1 ? "1px solid #eee" : "none",
                }}
              >
                {calc}
              </div>
            ))}
          </div>
          <button
            onClick={() => setHistory([])}
            style={{
              marginTop: "10px",
              padding: "5px 15px",
              backgroundColor: "#dc3545",
              color: "white",
              border: "none",
              borderRadius: "4px",
              cursor: "pointer",
            }}
          >
            Clear History
          </button>
        </div>
      )}
    </div>
  );
};

export default Calculator;
```

---

## 🎯 Final Challenge: Personal Dashboard

Create a personal dashboard that combines all the concepts you've learned:

**Requirements:**

1. **Weather Widget** - Show current weather (use mock data)
2. **Todo List** - Add, edit, delete, and mark todos as complete
3. **Notes Section** - Create and save notes
4. **Settings Panel** - Theme switcher, user preferences
5. **Calculator** - Embed the calculator you built
6. **Timer/Stopwatch** - Time management tools

**Technical Requirements:**

- Use custom hooks for shared logic
- Implement local storage for persistence
- Use conditional rendering for different views
- Handle all user interactions with proper state management
- Include loading states and error handling
- Make it responsive and well-styled

**Bonus Features:**

- Export data functionality
- Keyboard shortcuts
- Dark/light theme toggle
- Data visualization (charts for todos, time tracking)

---

## 🎓 Congratulations!

You've completed the comprehensive offline React tutorial! You now have solid foundation in:

- ✅ React components and JSX
- ✅ Props and component communication
- ✅ State management with hooks
- ✅ Event handling and user interactions
- ✅ Lists and conditional rendering
- ✅ Forms and controlled components
- ✅ useEffect and side effects
- ✅ Custom hooks for reusable logic
- ✅ Building complete applications

### Next Steps:

1. **Practice** - Build more projects using these concepts
2. **Explore** - Learn about React Router, Context API, Redux
3. **Advanced Topics** - Performance optimization, testing, TypeScript
4. **Real APIs** - Integrate with actual backend services
5. **Deployment** - Learn to deploy your React apps

**Keep coding and building amazing things with React! 🚀**

---

## 📚 TypeScript Glossary for React Developers

### Basic Types

```tsx
// Primitive types
const str: string = "hello";
const num: number = 42;
const bool: boolean = true;
const undef: undefined = undefined;
const nul: null = null;

// Array types
const numbers: number[] = [1, 2, 3];
const strings: Array<string> = ["a", "b", "c"];

// Object types
const obj: { name: string; age: number } = { name: "John", age: 25 };
```

### React-Specific Types

```tsx
// Component types
const MyComponent: React.FC = () => <div>Hello</div>;
const MyComponentWithProps: React.FC<{ name: string }> = ({ name }) => (
  <div>Hello {name}</div>
);

// Event types
const handleClick = (e: React.MouseEvent<HTMLButtonElement>): void => {};
const handleChange = (e: React.ChangeEvent<HTMLInputElement>): void => {};
const handleSubmit = (e: React.FormEvent<HTMLFormElement>): void => {};

// State types
const [count, setCount] = useState<number>(0);
const [user, setUser] = useState<User | null>(null);
const [items, setItems] = useState<string[]>([]);
```

### Advanced TypeScript Patterns

```tsx
// Generic types
interface ApiResponse<T> {
  data: T;
  status: number;
  message: string;
}

// Union types
type Status = "idle" | "loading" | "success" | "error";
type ButtonSize = "small" | "medium" | "large";

// Intersection types
interface User {
  name: string;
  age: number;
}
interface Admin {
  permissions: string[];
}
type AdminUser = User & Admin;

// Utility types
type PartialUser = Partial<User>; // All properties optional
type RequiredUser = Required<User>; // All properties required
type PickUser = Pick<User, "name" | "age">; // Pick specific properties
type OmitUser = Omit<User, "age">; // Exclude specific properties
```

### Common React + TypeScript Patterns

```tsx
// Props interface
interface ButtonProps {
  children: React.ReactNode;
  onClick?: () => void;
  variant?: "primary" | "secondary";
  disabled?: boolean;
}

// Component with props
const Button: React.FC<ButtonProps> = ({
  children,
  onClick,
  variant = "primary",
  disabled = false,
}) => {
  return (
    <button
      onClick={onClick}
      disabled={disabled}
      className={`btn btn-${variant}`}
    >
      {children}
    </button>
  );
};

// Custom hook with types
const useCounter = (initialValue: number = 0) => {
  const [count, setCount] = useState<number>(initialValue);

  const increment = (): void => setCount((prev) => prev + 1);
  const decrement = (): void => setCount((prev) => prev - 1);
  const reset = (): void => setCount(initialValue);

  return { count, increment, decrement, reset };
};
```

### TypeScript Configuration Tips

```json
// tsconfig.json - Key settings for React
{
  "compilerOptions": {
    "target": "es5",
    "lib": ["dom", "dom.iterable", "es6"],
    "allowJs": true,
    "skipLibCheck": true,
    "esModuleInterop": true,
    "allowSyntheticDefaultImports": true,
    "strict": true, // Enables all strict type checking options
    "forceConsistentCasingInFileNames": true,
    "module": "esnext",
    "moduleResolution": "node",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "noEmit": true,
    "jsx": "react-jsx" // Enables JSX in .tsx files
  },
  "include": ["src"]
}
```

### Common TypeScript Errors and Solutions

```tsx
// ❌ Error: Object is possibly 'undefined'
const user: User | undefined = getUser();
console.log(user.name); // Error!

// ✅ Solution: Optional chaining
console.log(user?.name);

// ✅ Solution: Type guard
if (user) {
  console.log(user.name);
}

// ❌ Error: Type 'string' is not assignable to type 'number'
const [count, setCount] = useState<number>(0);
setCount("1"); // Error!

// ✅ Solution: Proper type conversion
setCount(parseInt("1") || 0);

// ❌ Error: Property 'onClick' does not exist on type 'HTMLDivElement'
<div onClick={handleClick}>Click me</div> // Error!

// ✅ Solution: Use button or add proper event handling
<button onClick={handleClick}>Click me</button>
```

This glossary covers the essential TypeScript concepts you'll use in React development. Refer back to it as you build more complex applications!
