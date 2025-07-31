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
    "strict": true,              // Enables strict type checking
    "forceConsistentCasingInFileNames": true,
    "module": "esnext",
    "moduleResolution": "node",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "noEmit": true,
    "jsx": "react-jsx"           // Enables TSX
  },
  "include": ["src"]
}
```

---

## 2. Chapter 1: Your First TypeScript React Component

### What is a Component?
A component is like a LEGO block - a reusable piece of UI that you can combine with other components to build complex interfaces. With TypeScript, we add type safety to make our components more reliable!

### Exercise 1.1: Create Your First TypeScript Component

**Step 1:** Open `src/App.tsx` and replace everything with:

```tsx
import React from 'react';
import './App.css';

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
import React from 'react';

interface WelcomeProps {
  userName?: string; // Optional prop
  learningTopic: string; // Required prop
}

const Welcome: React.FC<WelcomeProps> = ({ userName = "Developer", learningTopic }) => {
  const encouragements: string[] = [
    "You're doing great!",
    "Keep it up!",
    "TypeScript makes React better!"
  ];
  
  const randomEncouragement: string = encouragements[Math.floor(Math.random() * encouragements.length)];
  
  return (
    <div style={{ 
      backgroundColor: '#f0f8ff', 
      padding: '20px', 
      borderRadius: '8px',
      margin: '10px 0'
    }}>
      <h2>Welcome to {learningTopic}, {userName}!</h2>
      <p>{randomEncouragement}</p>
      <small>💡 This component uses TypeScript interfaces for props!</small>
    </div>
  );
};

export default Welcome;
```

**Step 2:** Import and use it in `App.tsx`:

```tsx
import React from 'react';
import Welcome from './Welcome';
import './App.css';

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
import React from 'react';

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
  cardColor = '#ffffff' 
}) => {
  const { name, jobTitle, age, bio, availableForHire } = person;
  
  return (
    <div style={{ 
      border: '2px solid #333', 
      padding: '20px', 
      margin: '10px',
      borderRadius: '10px',
      backgroundColor: cardColor,
      boxShadow: '0 2px 4px rgba(0,0,0,0.1)'
    }}>
      <h3>{name} {age && <span style={{ color: '#666' }}>({age})</span>}</h3>
      <p><strong>Job:</strong> {jobTitle}</p>
      <p><strong>Bio:</strong> {bio}</p>
      <div style={{ 
        display: 'inline-block',
        padding: '4px 8px',
        borderRadius: '4px',
        backgroundColor: availableForHire ? '#4CAF50' : '#f44336',
        color: 'white',
        fontSize: '12px'
      }}>
        {availableForHire ? '✅ Available for hire' : '❌ Not available'}
      </div>
    </div>
  );
};

export default PersonCard;
```

**Usage in App.tsx:**
```tsx
import PersonCard from './PersonCard';

const samplePerson: Person = {
  name: "Sarah Johnson",
  jobTitle: "Frontend Developer",
  age: 28,
  bio: "Passionate about creating amazing user experiences with React and TypeScript!",
  availableForHire: true
};

// In your component's return:
<PersonCard person={samplePerson} cardColor="#e3f2fd" />
```

export default PersonCard;
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
}
```

### Exercise 2.1: Practice TSX with TypeScript

Create a `ProfileCard` component that uses TSX expressions with proper typing:

```tsx
// src/ProfileCard.tsx
import React from 'react';

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
  showBirthYear = true 
}) => {
  const currentYear: number = new Date().getFullYear();
  const birthYear: number = currentYear - user.age;
  const hobbyCount: number = user.hobbies.length;
  
  // Type-safe array method
  const hobbyList: string = user.hobbies.join(", ");
  
  return (
    <div className="profile-card" style={{
      border: '2px solid #4CAF50',
      borderRadius: '12px',
      padding: '20px',
      margin: '16px',
      backgroundColor: '#f9f9f9',
      maxWidth: '400px'
    }}>
      <h2 style={{ color: '#2196F3' }}>{user.name}</h2>
      <p><strong>Age:</strong> {user.age}</p>
      <p><strong>Profession:</strong> {user.profession}</p>
      {showBirthYear && <p><strong>Born in:</strong> {birthYear}</p>}
      {user.email && <p><strong>Email:</strong> {user.email}</p>}
      <p><strong>Hobbies:</strong> {hobbyList}</p>
      <p><strong>Number of hobbies:</strong> {hobbyCount}</p>
      
      {/* Conditional rendering with TypeScript */}
      {hobbyCount > 3 ? (
        <p style={{ color: '#FF9800' }}>🌟 Wow, you have many hobbies!</p>
      ) : (
        <p style={{ color: '#4CAF50' }}>📚 Room for more hobbies!</p>
      )}
    </div>
  );
};

export default ProfileCard;

```

**Usage in App.tsx:**
```tsx
import ProfileCard from './ProfileCard';

const App: React.FC = () => {
  const sampleUser: User = {
    name: "Sarah Johnson",
    age: 28,
    profession: "UX Designer",
    hobbies: ["Photography", "Hiking", "Reading", "Cooking"],
    email: "sarah@example.com"
  };
  
  const anotherUser: User = {
    name: "Mike Chen",
    age: 32,
    profession: "Software Engineer",
    hobbies: ["Gaming", "Basketball"]
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
import React from 'react';

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
  styling = {} 
}) => {
  // Type-safe style objects
  const cardStyle: React.CSSProperties = {
    backgroundColor: styling.backgroundColor || '#f0f0f0',
    padding: '20px',
    borderRadius: '8px',
    margin: '10px',
    boxShadow: '0 2px 4px rgba(0,0,0,0.1)',
    transition: 'transform 0.2s ease'
  };
  
  const titleStyle: React.CSSProperties = {
    color: styling.textColor || '#333',
    fontSize: '24px',
    marginBottom: '10px',
    fontWeight: 'bold'
  };
  
  const textStyle: React.CSSProperties = {
    color: styling.textColor || '#666',
    fontSize: '16px',
    lineHeight: '1.5'
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
import React from 'react';

interface WeatherData {
  city: string;
  tempCelsius: number;
  condition: 'Sunny' | 'Rainy' | 'Cloudy' | 'Snowy'; // Union type for valid conditions
  humidity?: number;
}

interface WeatherCardProps {
  weather: WeatherData;
  showHumidity?: boolean;
}

const WeatherCard: React.FC<WeatherCardProps> = ({ 
  weather, 
  showHumidity = false 
}) => {
  const tempFahrenheit: number = Math.round((weather.tempCelsius * 9/5) + 32);
  
  // Type-safe condition mapping
  const weatherEmojis: Record<WeatherData['condition'], string> = {
    'Sunny': '☀️',
    'Rainy': '🌧️',
    'Cloudy': '☁️',
    'Snowy': '❄️'
  };
  
  const cardStyle: React.CSSProperties = {
    backgroundColor: getBackgroundColor(weather.condition),
    padding: '20px',
    borderRadius: '10px',
    textAlign: 'center',
    color: 'white',
    minWidth: '250px',
    boxShadow: '0 4px 8px rgba(0,0,0,0.2)'
  };
  
  function getBackgroundColor(condition: WeatherData['condition']): string {
    const colors: Record<WeatherData['condition'], string> = {
      'Sunny': '#87CEEB',
      'Rainy': '#778899',
      'Cloudy': '#696969',
      'Snowy': '#B0C4DE'
    };
    return colors[condition];
  }
  
  return (
    <div style={cardStyle}>
      <h2>{weather.city} {weatherEmojis[weather.condition]}</h2>
      <h3>{weather.tempCelsius}°C / {tempFahrenheit}°F</h3>
      <p>{weather.condition}</p>
      {showHumidity && weather.humidity && (
        <p>Humidity: {weather.humidity}%</p>
      )}
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
  humidity: 65
};

<WeatherCard weather={weatherData} showHumidity={true} />
```

### TypeScript Benefits in This Chapter:
- ✅ **Type-safe props**: Interface definitions prevent wrong data types
- ✅ **Union types**: `'Sunny' | 'Rainy'` restricts to valid values only
- ✅ **Optional properties**: `humidity?: number` for flexible data
- ✅ **React.CSSProperties**: Type-safe inline styles
- ✅ **Record types**: Type-safe object mapping for emojis and colors
  };
  
  return (
    <div style={cardStyle}>
      <h2>{weather.city}</h2>
      <p>{weather.tempCelsius}°C / {tempFahrenheit.toFixed(1)}°F</p>
      <p>{weather.condition}</p>
    </div>
  );
}

export default WeatherCard;
```

---

## 4. Chapter 3: Props - Passing Data Between Components

### What are Props?
Props (properties) are like arguments to a function - they let you pass data from a parent component to a child component.

### Exercise 3.1: Your First Props

**Step 1:** Create a flexible greeting component:

```javascript
// src/Greeting.js
import React from 'react';

function Greeting(props) {
  return (
    <div>
      <h2>Hello, {props.name}!</h2>
      <p>Welcome to {props.website}</p>
    </div>
  );
}

export default Greeting;
```

**Step 2:** Use it in `App.js`:

```javascript
import React from 'react';
import Greeting from './Greeting';

function App() {
  return (
    <div className="App">
      <Greeting name="Alice" website="React Tutorial" />
      <Greeting name="Bob" website="JavaScript World" />
      <Greeting name="Charlie" website="Web Development" />
    </div>
  );
}

export default App;
```

### Exercise 3.2: Destructuring Props

You can make your code cleaner by destructuring props:

```javascript
// Instead of props.name, props.website
function Greeting({ name, website }) {
  return (
    <div>
      <h2>Hello, {name}!</h2>
      <p>Welcome to {website}</p>
    </div>
  );
}
```

### Exercise 3.3: Props with Different Data Types

```javascript
// src/ProductCard.js
import React from 'react';

function ProductCard({ name, price, inStock, features, onSale }) {
  return (
    <div style={{ 
      border: '1px solid #ddd', 
      padding: '20px', 
      margin: '10px',
      backgroundColor: onSale ? '#ffeb3b' : 'white'
    }}>
      <h3>{name}</h3>
      <p>Price: ${price}</p>
      <p>In Stock: {inStock ? '✅ Yes' : '❌ No'}</p>
      <p>Features: {features.join(', ')}</p>
      {onSale && <p style={{ color: 'red', fontWeight: 'bold' }}>ON SALE!</p>}
    </div>
  );
}

export default ProductCard;
```

**Use it in App.js:**

```javascript
function App() {
  return (
    <div className="App">
      <ProductCard 
        name="Laptop"
        price={999}
        inStock={true}
        features={["16GB RAM", "512GB SSD", "Intel i7"]}
        onSale={true}
      />
      <ProductCard 
        name="Phone"
        price={599}
        inStock={false}
        features={["128GB Storage", "Dual Camera", "5G"]}
        onSale={false}
      />
    </div>
  );
}
```

### Exercise 3.4: Default Props

```javascript
// src/Button.js
import React from 'react';

function Button({ text, color, size, onClick }) {
  const buttonStyle = {
    backgroundColor: color,
    padding: size === 'large' ? '15px 30px' : '10px 20px',
    fontSize: size === 'large' ? '18px' : '14px',
    border: 'none',
    borderRadius: '5px',
    color: 'white',
    cursor: 'pointer'
  };
  
  return (
    <button style={buttonStyle} onClick={onClick}>
      {text}
    </button>
  );
}

// Default props
Button.defaultProps = {
  text: 'Click me',
  color: 'blue',
  size: 'medium',
  onClick: () => console.log('Button clicked!')
};

export default Button;
```

### Practice Challenge 3.1:
Create a `StudentCard` component that receives:
- name (string)
- age (number)
- grades (array of numbers)
- isGraduated (boolean)

The component should:
- Display all the information
- Calculate and show the average grade
- Show "Graduated" or "Current Student" based on status
- Use different background colors for graduated vs current students

**Solution:**
```javascript
// src/StudentCard.js
import React from 'react';

function StudentCard({ name, age, grades, isGraduated }) {
  const average = grades.reduce((sum, grade) => sum + grade, 0) / grades.length;
  
  const cardStyle = {
    backgroundColor: isGraduated ? '#d4edda' : '#e2e3e5',
    border: `2px solid ${isGraduated ? '#28a745' : '#6c757d'}`,
    padding: '20px',
    margin: '10px',
    borderRadius: '8px'
  };
  
  return (
    <div style={cardStyle}>
      <h3>{name}</h3>
      <p>Age: {age}</p>
      <p>Grades: {grades.join(', ')}</p>
      <p>Average: {average.toFixed(2)}</p>
      <p>Status: {isGraduated ? '🎓 Graduated' : '📚 Current Student'}</p>
    </div>
  );
}

export default StudentCard;
```

---

## 5. Chapter 4: State and Event Handling

### What is State?
State is like a component's memory - it remembers information that can change over time.

### Exercise 4.1: Your First State

```javascript
// src/Counter.js
import React, { useState } from 'react';

function Counter() {
  // useState returns an array: [currentValue, functionToUpdateValue]
  const [count, setCount] = useState(0);
  
  return (
    <div>
      <h2>Counter: {count}</h2>
      <button onClick={() => setCount(count + 1)}>
        Increment
      </button>
      <button onClick={() => setCount(count - 1)}>
        Decrement
      </button>
      <button onClick={() => setCount(0)}>
        Reset
      </button>
    </div>
  );
}

export default Counter;
```

### Exercise 4.2: State with Different Data Types

```javascript
// src/UserProfile.js
import React, { useState } from 'react';

function UserProfile() {
  const [name, setName] = useState('');
  const [age, setAge] = useState(0);
  const [hobbies, setHobbies] = useState([]);
  const [isVisible, setIsVisible] = useState(true);
  
  const addHobby = () => {
    const newHobby = prompt('Enter a hobby:');
    if (newHobby) {
      setHobbies([...hobbies, newHobby]);
    }
  };
  
  const removeHobby = (indexToRemove) => {
    setHobbies(hobbies.filter((_, index) => index !== indexToRemove));
  };
  
  if (!isVisible) {
    return (
      <div>
        <button onClick={() => setIsVisible(true)}>Show Profile</button>
      </div>
    );
  }
  
  return (
    <div style={{ padding: '20px', border: '1px solid #ccc' }}>
      <button onClick={() => setIsVisible(false)}>Hide Profile</button>
      
      <div>
        <label>Name: </label>
        <input 
          value={name} 
          onChange={(e) => setName(e.target.value)}
          placeholder="Enter your name"
        />
      </div>
      
      <div>
        <label>Age: </label>
        <input 
          type="number"
          value={age} 
          onChange={(e) => setAge(parseInt(e.target.value) || 0)}
        />
      </div>
      
      <div>
        <h3>Profile:</h3>
        <p>Name: {name || 'Not provided'}</p>
        <p>Age: {age}</p>
      </div>
      
      <div>
        <h3>Hobbies:</h3>
        <button onClick={addHobby}>Add Hobby</button>
        <ul>
          {hobbies.map((hobby, index) => (
            <li key={index}>
              {hobby} 
              <button onClick={() => removeHobby(index)}>Remove</button>
            </li>
          ))}
        </ul>
      </div>
    </div>
  );
}

export default UserProfile;
```

### Exercise 4.3: Event Handling

```javascript
// src/EventDemo.js
import React, { useState } from 'react';

function EventDemo() {
  const [message, setMessage] = useState('');
  const [clickCount, setClickCount] = useState(0);
  const [inputValue, setInputValue] = useState('');
  
  const handleClick = () => {
    setClickCount(clickCount + 1);
    setMessage(`Button clicked ${clickCount + 1} times!`);
  };
  
  const handleInputChange = (event) => {
    setInputValue(event.target.value);
  };
  
  const handleSubmit = (event) => {
    event.preventDefault(); // Prevents page reload
    alert(`You entered: ${inputValue}`);
    setInputValue(''); // Clear the input
  };
  
  const handleKeyPress = (event) => {
    if (event.key === 'Enter') {
      setMessage(`You pressed Enter! Input value: ${inputValue}`);
    }
  };
  
  return (
    <div style={{ padding: '20px' }}>
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
}

export default EventDemo;
```

### Practice Challenge 4.1:
Create a `ColorPicker` component that:
- Has buttons for Red, Green, Blue, Yellow
- Changes background color when buttons are clicked
- Shows the current color name
- Has a reset button to go back to white

**Solution:**
```javascript
// src/ColorPicker.js
import React, { useState } from 'react';

function ColorPicker() {
  const [currentColor, setCurrentColor] = useState('white');
  
  const colors = [
    { name: 'Red', value: '#ff0000' },
    { name: 'Green', value: '#00ff00' },
    { name: 'Blue', value: '#0000ff' },
    { name: 'Yellow', value: '#ffff00' }
  ];
  
  const containerStyle = {
    padding: '20px',
    backgroundColor: currentColor,
    minHeight: '200px',
    border: '2px solid #ccc',
    textAlign: 'center'
  };
  
  return (
    <div style={containerStyle}>
      <h2>Color Picker</h2>
      <p>Current Color: {currentColor}</p>
      
      <div>
        {colors.map(color => (
          <button
            key={color.name}
            onClick={() => setCurrentColor(color.value)}
            style={{ margin: '5px', padding: '10px' }}
          >
            {color.name}
          </button>
        ))}
        
        <button
          onClick={() => setCurrentColor('white')}
          style={{ margin: '5px', padding: '10px' }}
        >
          Reset
        </button>
      </div>
    </div>
  );
}

export default ColorPicker;
```

---

## 6. Chapter 5: Lists and Conditional Rendering

### Rendering Lists

Lists are everywhere in web applications. Here's how to render them in React:

### Exercise 5.1: Basic List Rendering

```javascript
// src/ShoppingList.js
import React, { useState } from 'react';

function ShoppingList() {
  const [items, setItems] = useState([
    { id: 1, name: 'Apples', bought: false },
    { id: 2, name: 'Bread', bought: true },
    { id: 3, name: 'Milk', bought: false },
    { id: 4, name: 'Eggs', bought: false }
  ]);
  
  const toggleItem = (id) => {
    setItems(items.map(item => 
      item.id === id ? { ...item, bought: !item.bought } : item
    ));
  };
  
  return (
    <div style={{ padding: '20px' }}>
      <h2>Shopping List</h2>
      <ul style={{ listStyle: 'none', padding: 0 }}>
        {items.map(item => (
          <li 
            key={item.id} 
            style={{
              padding: '10px',
              margin: '5px 0',
              backgroundColor: item.bought ? '#d4edda' : '#f8f9fa',
              border: '1px solid #ccc',
              borderRadius: '4px',
              cursor: 'pointer'
            }}
            onClick={() => toggleItem(item.id)}
          >
            <span style={{ 
              textDecoration: item.bought ? 'line-through' : 'none' 
            }}>
              {item.name}
            </span>
            {item.bought && ' ✓'}
          </li>
        ))}
      </ul>
    </div>
  );
}

export default ShoppingList;
```

### Exercise 5.2: Conditional Rendering

```javascript
// src/UserDashboard.js
import React, { useState } from 'react';

function UserDashboard() {
  const [user, setUser] = useState(null);
  const [loading, setLoading] = useState(false);
  
  const loginUser = () => {
    setLoading(true);
    // Simulate API call
    setTimeout(() => {
      setUser({
        id: 1,
        name: 'John Doe',
        email: 'john@example.com',
        role: 'admin',
        notifications: 3
      });
      setLoading(false);
    }, 2000);
  };
  
  const logoutUser = () => {
    setUser(null);
  };
  
  // Loading state
  if (loading) {
    return (
      <div style={{ textAlign: 'center', padding: '50px' }}>
        <h2>Loading...</h2>
        <div>Please wait while we log you in.</div>
      </div>
    );
  }
  
  // Not logged in state
  if (!user) {
    return (
      <div style={{ textAlign: 'center', padding: '50px' }}>
        <h2>Welcome!</h2>
        <p>Please log in to access your dashboard.</p>
        <button 
          onClick={loginUser}
          style={{ padding: '10px 20px', fontSize: '16px' }}
        >
          Login
        </button>
      </div>
    );
  }
  
  // Logged in state
  return (
    <div style={{ padding: '20px' }}>
      <header style={{ 
        display: 'flex', 
        justifyContent: 'space-between', 
        alignItems: 'center',
        borderBottom: '1px solid #ccc',
        paddingBottom: '10px'
      }}>
        <h1>Dashboard</h1>
        <div>
          <span>Welcome, {user.name}!</span>
          <button 
            onClick={logoutUser}
            style={{ marginLeft: '10px', padding: '5px 10px' }}
          >
            Logout
          </button>
        </div>
      </header>
      
      <div style={{ marginTop: '20px' }}>
        <div style={{ display: 'grid', gridTemplateColumns: 'repeat(auto-fit, minmax(200px, 1fr))', gap: '20px' }}>
          <div style={{ padding: '20px', border: '1px solid #ccc', borderRadius: '8px' }}>
            <h3>Profile</h3>
            <p>Name: {user.name}</p>
            <p>Email: {user.email}</p>
            <p>Role: {user.role}</p>
          </div>
          
          <div style={{ padding: '20px', border: '1px solid #ccc', borderRadius: '8px' }}>
            <h3>Notifications</h3>
            {user.notifications > 0 ? (
              <p style={{ color: 'red' }}>
                You have {user.notifications} new notifications!
              </p>
            ) : (
              <p style={{ color: 'green' }}>No new notifications</p>
            )}
          </div>
          
          {user.role === 'admin' && (
            <div style={{ padding: '20px', border: '1px solid #ccc', borderRadius: '8px' }}>
              <h3>Admin Panel</h3>
              <p>You have admin access!</p>
              <button>Manage Users</button>
            </div>
          )}
        </div>
      </div>
    </div>
  );
}

export default UserDashboard;
```

### Exercise 5.3: Dynamic Lists with Add/Remove

```javascript
// src/TodoApp.js
import React, { useState } from 'react';

function TodoApp() {
  const [todos, setTodos] = useState([]);
  const [inputValue, setInputValue] = useState('');
  const [filter, setFilter] = useState('all'); // 'all', 'active', 'completed'
  
  const addTodo = () => {
    if (inputValue.trim()) {
      const newTodo = {
        id: Date.now(),
        text: inputValue.trim(),
        completed: false,
        createdAt: new Date().toLocaleString()
      };
      setTodos([...todos, newTodo]);
      setInputValue('');
    }
  };
  
  const toggleTodo = (id) => {
    setTodos(todos.map(todo =>
      todo.id === id ? { ...todo, completed: !todo.completed } : todo
    ));
  };
  
  const deleteTodo = (id) => {
    setTodos(todos.filter(todo => todo.id !== id));
  };
  
  const clearCompleted = () => {
    setTodos(todos.filter(todo => !todo.completed));
  };
  
  const getFilteredTodos = () => {
    switch (filter) {
      case 'active':
        return todos.filter(todo => !todo.completed);
      case 'completed':
        return todos.filter(todo => todo.completed);
      default:
        return todos;
    }
  };
  
  const filteredTodos = getFilteredTodos();
  const activeCount = todos.filter(todo => !todo.completed).length;
  
  return (
    <div style={{ maxWidth: '600px', margin: '0 auto', padding: '20px' }}>
      <h1>Todo App</h1>
      
      {/* Add Todo */}
      <div style={{ marginBottom: '20px' }}>
        <input
          value={inputValue}
          onChange={(e) => setInputValue(e.target.value)}
          onKeyPress={(e) => e.key === 'Enter' && addTodo()}
          placeholder="What needs to be done?"
          style={{ 
            width: '70%', 
            padding: '10px', 
            fontSize: '16px',
            border: '1px solid #ccc',
            borderRadius: '4px'
          }}
        />
        <button 
          onClick={addTodo}
          style={{ 
            width: '25%', 
            padding: '10px', 
            marginLeft: '5%',
            fontSize: '16px',
            backgroundColor: '#007bff',
            color: 'white',
            border: 'none',
            borderRadius: '4px',
            cursor: 'pointer'
          }}
        >
          Add
        </button>
      </div>
      
      {/* Filter Buttons */}
      <div style={{ marginBottom: '20px' }}>
        {['all', 'active', 'completed'].map(filterType => (
          <button
            key={filterType}
            onClick={() => setFilter(filterType)}
            style={{
              margin: '0 5px',
              padding: '5px 15px',
              backgroundColor: filter === filterType ? '#007bff' : '#f8f9fa',
              color: filter === filterType ? 'white' : 'black',
              border: '1px solid #ccc',
              borderRadius: '4px',
              cursor: 'pointer'
            }}
          >
            {filterType.charAt(0).toUpperCase() + filterType.slice(1)}
          </button>
        ))}
      </div>
      
      {/* Todo List */}
      {filteredTodos.length === 0 ? (
        <p style={{ textAlign: 'center', color: '#666' }}>
          {filter === 'all' ? 'No todos yet!' : `No ${filter} todos!`}
        </p>
      ) : (
        <ul style={{ listStyle: 'none', padding: 0 }}>
          {filteredTodos.map(todo => (
            <li 
              key={todo.id}
              style={{
                display: 'flex',
                alignItems: 'center',
                padding: '15px',
                margin: '5px 0',
                backgroundColor: '#f8f9fa',
                border: '1px solid #dee2e6',
                borderRadius: '4px'
              }}
            >
              <input
                type="checkbox"
                checked={todo.completed}
                onChange={() => toggleTodo(todo.id)}
                style={{ marginRight: '10px' }}
              />
              <div style={{ flex: 1 }}>
                <span style={{
                  textDecoration: todo.completed ? 'line-through' : 'none',
                  color: todo.completed ? '#6c757d' : 'black',
                  fontSize: '16px'
                }}>
                  {todo.text}
                </span>
                <div style={{ fontSize: '12px', color: '#6c757d' }}>
                  Created: {todo.createdAt}
                </div>
              </div>
              <button
                onClick={() => deleteTodo(todo.id)}
                style={{
                  backgroundColor: '#dc3545',
                  color: 'white',
                  border: 'none',
                  borderRadius: '4px',
                  padding: '5px 10px',
                  cursor: 'pointer'
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
        <div style={{ 
          marginTop: '20px', 
          padding: '10px', 
          backgroundColor: '#f8f9fa',
          border: '1px solid #dee2e6',
          borderRadius: '4px',
          display: 'flex',
          justifyContent: 'space-between',
          alignItems: 'center'
        }}>
          <span>{activeCount} item{activeCount !== 1 ? 's' : ''} left</span>
          <button
            onClick={clearCompleted}
            disabled={todos.filter(todo => todo.completed).length === 0}
            style={{
              backgroundColor: '#6c757d',
              color: 'white',
              border: 'none',
              borderRadius: '4px',
              padding: '5px 10px',
              cursor: 'pointer',
              opacity: todos.filter(todo => todo.completed).length === 0 ? 0.5 : 1
            }}
          >
            Clear Completed
          </button>
        </div>
      )}
    </div>
  );
}

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

### Exercise 6.1: Controlled Components

```javascript
// src/ContactForm.js
import React, { useState } from 'react';

function ContactForm() {
  const [formData, setFormData] = useState({
    name: '',
    email: '',
    message: '',
    category: 'general',
    subscribe: false
  });
  
  const [errors, setErrors] = useState({});
  const [submitted, setSubmitted] = useState(false);
  
  const handleInputChange = (e) => {
    const { name, value, type, checked } = e.target;
    setFormData(prev => ({
      ...prev,
      [name]: type === 'checkbox' ? checked : value
    }));
    
    // Clear error when user starts typing
    if (errors[name]) {
      setErrors(prev => ({
        ...prev,
        [name]: ''
      }));
    }
  };
  
  const validateForm = () => {
    const newErrors = {};
    
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
  
  const handleSubmit = (e) => {
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
              border: `1px solid ${errors.name ? '#dc3545' : '#ccc'}`,
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

### Exercise 7.1: Basic useEffect

```javascript
// src/TimerComponent.js
import React, { useState, useEffect } from 'react';

function TimerComponent() {
  const [seconds, setSeconds] = useState(0);
  const [isRunning, setIsRunning] = useState(false);
  
  // Effect that runs when isRunning changes
  useEffect(() => {
    let interval = null;
    
    if (isRunning) {
      interval = setInterval(() => {
        setSeconds(prevSeconds => prevSeconds + 1);
      }, 1000);
    } else {
      clearInterval(interval);
    }
    
    // Cleanup function
    return () => clearInterval(interval);
  }, [isRunning]);
  
  // Effect that runs only once (on mount)
  useEffect(() => {
    console.log('Timer component mounted');
    
    // Cleanup function (runs on unmount)
    return () => {
      console.log('Timer component unmounted');
    };
  }, []); // Empty dependency array = run once
  
  const formatTime = (seconds) => {
    const mins = Math.floor(seconds / 60);
    const secs = seconds % 60;
    return `${mins.toString().padStart(2, '0')}:${secs.toString().padStart(2, '0')}`;
  };
  
  return (
    <div style={{ textAlign: 'center', padding: '20px' }}>
      <h2>Timer</h2>
      <div style={{ fontSize: '48px', fontFamily: 'monospace', margin: '20px 0' }}>
        {formatTime(seconds)}
      </div>
      
      <div>
        <button
          onClick={() => setIsRunning(!isRunning)}
          style={{
            backgroundColor: isRunning ? '#dc3545' : '#28a745',
            color: 'white',
            border: 'none',
            padding: '10px 20px',
            margin: '0 5px',
            borderRadius: '4px',
            cursor: 'pointer'
          }}
        >
          {isRunning ? 'Stop' : 'Start'}
        </button>
        
        <button
          onClick={() => {
            setSeconds(0);
            setIsRunning(false);
          }}
          style={{
            backgroundColor: '#6c757d',
            color: 'white',
            border: 'none',
            padding: '10px 20px',
            margin: '0 5px',
            borderRadius: '4px',
            cursor: 'pointer'
          }}
        >
          Reset
        </button>
      </div>
    </div>
  );
}

export default TimerComponent;
```

### Exercise 7.2: Data Fetching Simulation

```javascript
// src/UserList.js
import React, { useState, useEffect } from 'react';

// Mock API function (simulates real API call)
const fetchUsers = () => {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve([
        { id: 1, name: 'John Doe', email: 'john@example.com', city: 'New York' },
        { id: 2, name: 'Jane Smith', email: 'jane@example.com', city: 'Los Angeles' },
        { id: 3, name: 'Bob Johnson', email: 'bob@example.com', city: 'Chicago' },
        { id: 4, name: 'Alice Brown', email: 'alice@example.com', city: 'Houston' }
      ]);
    }, 2000); // 2 second delay to simulate network request
  });
};

function UserList() {
  const [users, setUsers] = useState([]);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);
  const [refetchTrigger, setRefetchTrigger] = useState(0);
  
  useEffect(() => {
    const loadUsers = async () => {
      try {
        setLoading(true);
        setError(null);
        
        // Simulate API call
        const userData = await fetchUsers();
        setUsers(userData);
      } catch (err) {
        setError('Failed to load users');
        console.error(err);
      } finally {
        setLoading(false);
      }
    };
    
    loadUsers();
  }, [refetchTrigger]); // Refetch when refetchTrigger changes
  
  const handleRefresh = () => {
    setRefetchTrigger(prev => prev + 1);
  };
  
  if (loading) {
    return (
      <div style={{ textAlign: 'center', padding: '50px' }}>
        <h2>Loading Users...</h2>
        <div style={{ fontSize: '20px' }}>⏳</div>
      </div>
    );
  }
  
  if (error) {
    return (
      <div style={{ textAlign: 'center', padding: '50px' }}>
        <h2>Error</h2>
        <p style={{ color: 'red' }}>{error}</p>
        <button onClick={handleRefresh}>Try Again</button>
      </div>
    );
  }
  
  return (
    <div style={{ padding: '20px' }}>
      <div style={{ 
        display: 'flex', 
        justifyContent: 'space-between', 
        alignItems: 'center',
        marginBottom: '20px'
      }}>
        <h2>Users ({users.length})</h2>
        <button
          onClick={handleRefresh}
          style={{
            backgroundColor: '#007bff',
            color: 'white',
            border: 'none',
            padding: '8px 16px',
            borderRadius: '4px',
            cursor: 'pointer'
          }}
        >
          Refresh
        </button>
      </div>
      
      <div style={{ 
        display: 'grid', 
        gridTemplateColumns: 'repeat(auto-fill, minmax(300px, 1fr))',
        gap: '20px'
      }}>
        {users.map(user => (
          <div
            key={user.id}
            style={{
              border: '1px solid #dee2e6',
              borderRadius: '8px',
              padding: '20px',
              backgroundColor: '#f8f9fa'
            }}
          >
            <h3 style={{ margin: '0 0 10px 0' }}>{user.name}</h3>
            <p style={{ margin: '5px 0' }}>📧 {user.email}</p>
            <p style={{ margin: '5px 0' }}>🏙️ {user.city}</p>
          </div>
        ))}
      </div>
    </div>
  );
}

export default UserList;
```

---

## 9. Chapter 8: Custom Hooks

### Exercise 8.1: Creating Your First Custom Hook

```javascript
// src/hooks/useCounter.js
import { useState } from 'react';

function useCounter(initialValue = 0) {
  const [count, setCount] = useState(initialValue);
  
  const increment = () => setCount(prev => prev + 1);
  const decrement = () => setCount(prev => prev - 1);
  const reset = () => setCount(initialValue);
  const setValue = (value) => setCount(value);
  
  return {
    count,
    increment,
    decrement,
    reset,
    setValue
  };
}

export default useCounter;
```

```javascript
// src/CounterWithHook.js
import React from 'react';
import useCounter from './hooks/useCounter';

function CounterWithHook() {
  const { count, increment, decrement, reset, setValue } = useCounter(10);
  
  return (
    <div style={{ textAlign: 'center', padding: '20px' }}>
      <h2>Counter with Custom Hook</h2>
      <div style={{ fontSize: '32px', margin: '20px 0' }}>
        Count: {count}
      </div>
      
      <div>
        <button onClick={decrement}>-1</button>
        <button onClick={increment}>+1</button>
        <button onClick={reset}>Reset</button>
        <button onClick={() => setValue(100)}>Set to 100</button>
      </div>
    </div>
  );
}

export default CounterWithHook;
```

### Exercise 8.2: useLocalStorage Hook

```javascript
// src/hooks/useLocalStorage.js
import { useState, useEffect } from 'react';

function useLocalStorage(key, initialValue) {
  // Get value from localStorage or use initial value
  const [storedValue, setStoredValue] = useState(() => {
    try {
      const item = window.localStorage.getItem(key);
      return item ? JSON.parse(item) : initialValue;
    } catch (error) {
      console.error(`Error reading localStorage key "${key}":`, error);
      return initialValue;
    }
  });
  
  // Return wrapped version of useState's setter function
  const setValue = (value) => {
    try {
      // Allow value to be a function like useState
      const valueToStore = value instanceof Function ? value(storedValue) : value;
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

```javascript
// src/SettingsComponent.js
import React from 'react';
import useLocalStorage from './hooks/useLocalStorage';

function SettingsComponent() {
  const [theme, setTheme] = useLocalStorage('theme', 'light');
  const [username, setUsername] = useLocalStorage('username', '');
  const [notifications, setNotifications] = useLocalStorage('notifications', true);
  
  const themes = {
    light: { backgroundColor: '#ffffff', color: '#000000' },
    dark: { backgroundColor: '#333333', color: '#ffffff' }
  };
  
  return (
    <div style={{ 
      ...themes[theme], 
      padding: '20px', 
      minHeight: '400px',
      transition: 'all 0.3s ease'
    }}>
      <h2>Settings (Persisted in LocalStorage)</h2>
      
      <div style={{ marginBottom: '20px' }}>
        <label style={{ display: 'block', marginBottom: '5px' }}>
          Username:
        </label>
        <input
          type="text"
          value={username}
          onChange={(e) => setUsername(e.target.value)}
          placeholder="Enter your username"
          style={{ padding: '8px', width: '200px' }}
        />
      </div>
      
      <div style={{ marginBottom: '20px' }}>
        <label style={{ display: 'block', marginBottom: '5px' }}>
          Theme:
        </label>
        <select
          value={theme}
          onChange={(e) => setTheme(e.target.value)}
          style={{ padding: '8px' }}
        >
          <option value="light">Light</option>
          <option value="dark">Dark</option>
        </select>
      </div>
      
      <div style={{ marginBottom: '20px' }}>
        <label style={{ display: 'flex', alignItems: 'center' }}>
          <input
            type="checkbox"
            checked={notifications}
            onChange={(e) => setNotifications(e.target.checked)}
            style={{ marginRight: '8px' }}
          />
          Enable notifications
        </label>
      </div>
      
      <div style={{ 
        padding: '15px', 
        border: '1px solid #ccc', 
        borderRadius: '4px',
        backgroundColor: theme === 'light' ? '#f8f9fa' : '#555555'
      }}>
        <h3>Current Settings:</h3>
        <p>Username: {username || 'Not set'}</p>
        <p>Theme: {theme}</p>
        <p>Notifications: {notifications ? 'Enabled' : 'Disabled'}</p>
      </div>
    </div>
  );
}

export default SettingsComponent;
```

---

## 10. Chapter 9: Building Real Projects

### Project 1: Complete Calculator App

```javascript
// src/Calculator.js
import React, { useState } from 'react';

function Calculator() {
  const [display, setDisplay] = useState('0');
  const [previousValue, setPreviousValue] = useState(null);
  const [operation, setOperation] = useState(null);
  const [waitingForOperand, setWaitingForOperand] = useState(false);
  const [history, setHistory] = useState([]);
  
  const inputNumber = (num) => {
    if (waitingForOperand) {
      setDisplay(String(num));
      setWaitingForOperand(false);
    } else {
      setDisplay(display === '0' ? String(num) : display + num);
    }
  };
  
  const inputDecimal = () => {
    if (waitingForOperand) {
      setDisplay('0.');
      setWaitingForOperand(false);
    } else if (display.indexOf('.') === -1) {
      setDisplay(display + '.');
    }
  };
  
  const clear = () => {
    setDisplay('0');
    setPreviousValue(null);
    setOperation(null);
    setWaitingForOperand(false);
  };
  
  const performCalculation = {
    '/': (prevValue, nextValue) => prevValue / nextValue,
    '*': (prevValue, nextValue) => prevValue * nextValue,
    '+': (prevValue, nextValue) => prevValue + nextValue,
    '-': (prevValue, nextValue) => prevValue - nextValue,
    '=': (prevValue, nextValue) => nextValue
  };
  
  const calculate = (nextOperation) => {
    const inputValue = parseFloat(display);
    
    if (previousValue === null) {
      setPreviousValue(inputValue);
    } else if (operation) {
      const currentValue = previousValue || 0;
      const newValue = performCalculation[operation](currentValue, inputValue);
      
      // Add to history
      const calculation = `${currentValue} ${operation} ${inputValue} = ${newValue}`;
      setHistory(prev => [calculation, ...prev.slice(0, 9)]); // Keep last 10
      
      setDisplay(String(newValue));
      setPreviousValue(newValue);
    }
    
    setWaitingForOperand(true);
    setOperation(nextOperation);
  };
  
  const buttonStyle = {
    fontSize: '18px',
    padding: '20px',
    margin: '2px',
    border: 'none',
    borderRadius: '4px',
    cursor: 'pointer',
    minWidth: '60px',
    minHeight: '60px'
  };
  
  const numberButtonStyle = {
    ...buttonStyle,
    backgroundColor: '#f8f9fa',
    border: '1px solid #dee2e6'
  };
  
  const operatorButtonStyle = {
    ...buttonStyle,
    backgroundColor: '#007bff',
    color: 'white'
  };
  
  const specialButtonStyle = {
    ...buttonStyle,
    backgroundColor: '#6c757d',
    color: 'white'
  };
  
  return (
    <div style={{ 
      maxWidth: '400px', 
      margin: '0 auto', 
      padding: '20px',
      border: '1px solid #ccc',
      borderRadius: '8px',
      backgroundColor: '#f8f9fa'
    }}>
      <h2 style={{ textAlign: 'center' }}>Calculator</h2>
      
      {/* Display */}
      <div style={{
        backgroundColor: '#000',
        color: '#00ff00',
        padding: '20px',
        marginBottom: '20px',
        borderRadius: '4px',
        fontSize: '24px',
        textAlign: 'right',
        fontFamily: 'monospace',
        minHeight: '30px',
        wordBreak: 'break-all'
      }}>
        {display}
      </div>
      
      {/* Button Grid */}
      <div style={{ display: 'grid', gridTemplateColumns: 'repeat(4, 1fr)', gap: '2px' }}>
        <button style={specialButtonStyle} onClick={clear}>C</button>
        <button style={specialButtonStyle} onClick={() => setDisplay(display.slice(0, -1) || '0')}>⌫</button>
        <button style={operatorButtonStyle} onClick={() => calculate('/')}>/</button>
        <button style={operatorButtonStyle} onClick={() => calculate('*')}>×</button>
        
        <button style={numberButtonStyle} onClick={() => inputNumber(7)}>7</button>
        <button style={numberButtonStyle} onClick={() => inputNumber(8)}>8</button>
        <button style={numberButtonStyle} onClick={() => inputNumber(9)}>9</button>
        <button style={operatorButtonStyle} onClick={() => calculate('-')}>-</button>
        
        <button style={numberButtonStyle} onClick={() => inputNumber(4)}>4</button>
        <button style={numberButtonStyle} onClick={() => inputNumber(5)}>5</button>
        <button style={numberButtonStyle} onClick={() => inputNumber(6)}>6</button>
        <button style={operatorButtonStyle} onClick={() => calculate('+')}>+</button>
        
        <button style={numberButtonStyle} onClick={() => inputNumber(1)}>1</button>
        <button style={numberButtonStyle} onClick={() => inputNumber(2)}>2</button>
        <button style={numberButtonStyle} onClick={() => inputNumber(3)}>3</button>
        <button 
          style={{...operatorButtonStyle, gridRow: 'span 2'}} 
          onClick={() => calculate('=')}
        >
          =
        </button>
        
        <button 
          style={{...numberButtonStyle, gridColumn: 'span 2'}} 
          onClick={() => inputNumber(0)}
        >
          0
        </button>
        <button style={numberButtonStyle} onClick={inputDecimal}>.</button>
      </div>
      
      {/* History */}
      {history.length > 0 && (
        <div style={{ marginTop: '20px' }}>
          <h3>History:</h3>
          <div style={{ 
            maxHeight: '150px', 
            overflowY: 'auto',
            backgroundColor: 'white',
            padding: '10px',
            borderRadius: '4px',
            border: '1px solid #dee2e6'
          }}>
            {history.map((calc, index) => (
              <div key={index} style={{ 
                fontSize: '14px', 
                fontFamily: 'monospace',
                padding: '2px 0',
                borderBottom: index < history.length - 1 ? '1px solid #eee' : 'none'
              }}>
                {calc}
              </div>
            ))}
          </div>
          <button 
            onClick={() => setHistory([])}
            style={{
              marginTop: '10px',
              padding: '5px 15px',
              backgroundColor: '#dc3545',
              color: 'white',
              border: 'none',
              borderRadius: '4px',
              cursor: 'pointer'
            }}
          >
            Clear History
          </button>
        </div>
      )}
    </div>
  );
}

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
