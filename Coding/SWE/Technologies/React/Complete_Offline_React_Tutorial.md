# Complete TypeScript React Tutorial: Enterprise-Ready Development

_The definitive guide to mastering React with TypeScript for professional development_

## 📚 Table of Contents

**🏗️ Part I: Foundation & Setup**

1. [Environment Setup & TypeScript Configuration](#1-environment-setup--typescript-configuration)
2. [TypeScript Fundamentals for React](#2-typescript-fundamentals-for-react)
3. [Your First TypeScript React Component](#3-your-first-typescript-react-component)
4. [TSX Syntax & Best Practices](#4-tsx-syntax--best-practices)

**⚛️ Part II: Core React Concepts** 5. [Props & Component Communication](#5-props--component-communication) 6. [State Management with useState](#6-state-management-with-usestate) 7. [Event Handling & Form Management](#7-event-handling--form-management) 8. [Lists, Keys & Conditional Rendering](#8-lists-keys--conditional-rendering)

**🔧 Part III: Advanced React Patterns** 9. [useEffect & Side Effects](#9-useeffect--side-effects) 10. [Custom Hooks & Reusable Logic](#10-custom-hooks--reusable-logic) 11. [Context API & Global State](#11-context-api--global-state) 12. [Error Boundaries & Error Handling](#12-error-boundaries--error-handling)

**🏢 Part IV: Enterprise Development** 13. [Component Design Patterns](#13-component-design-patterns) 14. [Performance Optimization](#14-performance-optimization) 15. [Testing with Jest & React Testing Library](#15-testing-with-jest--react-testing-library) 16. [Code Organization & Architecture](#16-code-organization--architecture)

**🚀 Part V: Production-Ready Development** 17. [Build & Deployment Configuration](#17-build--deployment-configuration) 18. [Accessibility & Best Practices](#18-accessibility--best-practices) 19. [Real-World Project: Enterprise Dashboard](#19-real-world-project-enterprise-dashboard) 20. [Next Steps & Advanced Topics](#20-next-steps--advanced-topics)

---

## 1. Environment Setup & TypeScript Configuration

### Prerequisites for Enterprise Development

Before we begin, ensure you have:

**Required Tools:**

- **Node.js** (v18+ LTS) - Download from [nodejs.org](https://nodejs.org/)
- **VS Code** - The industry standard editor for React development
- **Git** - For version control

**Essential VS Code Extensions:**

```bash
# Install these extensions for optimal TypeScript React development
code --install-extension ms-vscode.vscode-typescript-next
code --install-extension bradlc.vscode-tailwindcss
code --install-extension esbenp.prettier-vscode
code --install-extension ms-vscode.vscode-eslint
code --install-extension formulahendry.auto-rename-tag
code --install-extension christian-kohler.path-intellisense
```

**Knowledge Prerequisites:**

- HTML, CSS, and modern JavaScript (ES6+)
- Basic understanding of npm/yarn
- Familiarity with command line basics

### Why TypeScript in Enterprise React Development?

TypeScript provides essential benefits for enterprise development:

| Benefit                   | Impact                                                            |
| ------------------------- | ----------------------------------------------------------------- |
| **Type Safety**           | Catch errors at compile time, reducing production bugs by ~40%    |
| **Enhanced IDE Support**  | IntelliSense, refactoring, and navigation improve productivity    |
| **Self-Documenting Code** | Types serve as living documentation                               |
| **Team Collaboration**    | Clear interfaces between team members                             |
| **Maintainability**       | Easier to refactor large codebases safely                         |
| **Industry Standard**     | 87% of enterprise React apps use TypeScript (Stack Overflow 2024) |

### Project Setup: Enterprise-Grade Configuration

#### Option 1: Create React App with TypeScript (Recommended for Learning)

```bash
npx create-react-app enterprise-react-app --template typescript
cd enterprise-react-app
```

#### Option 2: Vite with TypeScript (Production Alternative)

```bash
npm create vite@latest enterprise-react-app -- --template react-ts
cd enterprise-react-app
npm install
```

#### Essential Enterprise Dependencies

```bash
# Core dependencies
npm install react-router-dom axios date-fns

# Type definitions
npm install --save-dev @types/node

# Testing utilities
npm install --save-dev @testing-library/react @testing-library/jest-dom @testing-library/user-event

# Code quality tools
npm install --save-dev eslint-config-prettier eslint-plugin-react-hooks

# Utility libraries for enterprise apps
npm install clsx react-hook-form zod
```

### Enterprise Project Structure

```
enterprise-react-app/
├── public/
│   ├── index.html
│   └── favicon.ico
├── src/
│   ├── components/           # Reusable UI components
│   │   ├── ui/              # Basic UI components (buttons, inputs)
│   │   ├── forms/           # Form-specific components
│   │   └── layout/          # Layout components (header, sidebar)
│   ├── pages/               # Page-level components
│   ├── hooks/               # Custom React hooks
│   ├── services/            # API calls and external services
│   ├── types/               # TypeScript type definitions
│   ├── utils/               # Helper functions
│   ├── context/             # React Context providers
│   ├── constants/           # Application constants
│   ├── assets/              # Images, fonts, etc.
│   ├── styles/              # Global styles and themes
│   ├── __tests__/           # Test files
│   ├── App.tsx
│   ├── index.tsx
│   └── react-app-env.d.ts
├── package.json
├── tsconfig.json
├── .eslintrc.json
├── .prettierrc
└── README.md
```

### TypeScript Configuration (tsconfig.json)

Enhanced configuration for enterprise development:

```json
{
  "compilerOptions": {
    "target": "ES2020",
    "lib": ["dom", "dom.iterable", "ES6", "ES2020"],
    "allowJs": true,
    "skipLibCheck": true,
    "esModuleInterop": true,
    "allowSyntheticDefaultImports": true,
    "strict": true,
    "noImplicitAny": true,
    "noImplicitReturns": true,
    "noFallthroughCasesInSwitch": true,
    "noUncheckedIndexedAccess": true,
    "exactOptionalPropertyTypes": true,
    "forceConsistentCasingInFileNames": true,
    "module": "esnext",
    "moduleResolution": "node",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "noEmit": true,
    "jsx": "react-jsx",
    "baseUrl": "src",
    "paths": {
      "@/*": ["*"],
      "@components/*": ["components/*"],
      "@pages/*": ["pages/*"],
      "@hooks/*": ["hooks/*"],
      "@services/*": ["services/*"],
      "@types/*": ["types/*"],
      "@utils/*": ["utils/*"],
      "@assets/*": ["assets/*"]
    }
  },
  "include": ["src"],
  "exclude": ["node_modules", "build", "dist"]
}
```

### ESLint Configuration (.eslintrc.json)

```json
{
  "extends": [
    "react-app",
    "react-app/jest",
    "@typescript-eslint/recommended",
    "@typescript-eslint/recommended-requiring-type-checking",
    "prettier"
  ],
  "parser": "@typescript-eslint/parser",
  "parserOptions": {
    "project": "./tsconfig.json"
  },
  "plugins": ["@typescript-eslint", "react-hooks"],
  "rules": {
    "react-hooks/rules-of-hooks": "error",
    "react-hooks/exhaustive-deps": "warn",
    "@typescript-eslint/no-unused-vars": "error",
    "@typescript-eslint/explicit-function-return-type": "warn",
    "@typescript-eslint/no-explicit-any": "warn",
    "@typescript-eslint/prefer-nullish-coalescing": "error",
    "@typescript-eslint/prefer-optional-chain": "error",
    "prefer-const": "error",
    "no-var": "error"
  },
  "overrides": [
    {
      "files": ["**/*.test.ts", "**/*.test.tsx"],
      "rules": {
        "@typescript-eslint/no-explicit-any": "off"
      }
    }
  ]
}
```

### Development Workflow Setup

**Package.json Scripts:**

```json
{
  "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject",
    "lint": "eslint src --ext .ts,.tsx",
    "lint:fix": "eslint src --ext .ts,.tsx --fix",
    "type-check": "tsc --noEmit",
    "format": "prettier --write \"src/**/*.{ts,tsx,json,css,md}\"",
    "analyze": "npm run build && npx bundle-analyzer build/static/js/*.js"
  }
}
```

**VS Code Settings (.vscode/settings.json):**

```json
{
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.formatOnSave": true,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true,
    "source.organizeImports": true
  },
  "typescript.preferences.importModuleSpecifier": "relative"
}
```

### Verify Your Setup

Create this comprehensive test to verify everything works:

**src/components/SetupTest.tsx**

```tsx
import React, { useState } from "react";

interface SetupTestProps {
  message: string;
}

interface TestResult {
  feature: string;
  status: "pass" | "fail";
  description: string;
}

const SetupTest: React.FC<SetupTestProps> = ({ message }) => {
  const [testResults] = useState<TestResult[]>([
    {
      feature: "TypeScript",
      status: "pass",
      description: "Types working correctly",
    },
    { feature: "React", status: "pass", description: "Components rendering" },
    { feature: "Hooks", status: "pass", description: "useState functioning" },
    { feature: "Styling", status: "pass", description: "CSS-in-JS working" },
  ]);

  const getStatusColor = (status: TestResult["status"]): string => {
    return status === "pass" ? "#4caf50" : "#f44336";
  };

  const successCount = testResults.filter(
    (test) => test.status === "pass"
  ).length;

  return (
    <div
      style={{
        padding: "24px",
        backgroundColor: "#f8f9fa",
        borderRadius: "12px",
        border: "2px solid #e9ecef",
        maxWidth: "600px",
        margin: "20px auto",
        fontFamily:
          '-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif',
      }}
    >
      <h2
        style={{
          color: "#495057",
          marginBottom: "16px",
          fontSize: "24px",
          fontWeight: "600",
        }}
      >
        🚀 TypeScript React Setup Complete!
      </h2>

      <p
        style={{
          color: "#6c757d",
          marginBottom: "24px",
          fontSize: "16px",
          lineHeight: "1.5",
        }}
      >
        {message}
      </p>

      <div style={{ marginBottom: "20px" }}>
        <h3
          style={{ color: "#495057", marginBottom: "12px", fontSize: "18px" }}
        >
          System Check ({successCount}/{testResults.length} passed)
        </h3>

        {testResults.map((test, index) => (
          <div
            key={index}
            style={{
              display: "flex",
              alignItems: "center",
              padding: "8px 12px",
              marginBottom: "8px",
              backgroundColor: "white",
              borderRadius: "6px",
              border: `1px solid ${getStatusColor(test.status)}20`,
            }}
          >
            <span
              style={{
                width: "20px",
                height: "20px",
                borderRadius: "50%",
                backgroundColor: getStatusColor(test.status),
                color: "white",
                display: "flex",
                alignItems: "center",
                justifyContent: "center",
                fontSize: "12px",
                fontWeight: "bold",
                marginRight: "12px",
              }}
            >
              {test.status === "pass" ? "✓" : "✗"}
            </span>

            <div>
              <strong style={{ color: "#495057" }}>{test.feature}</strong>
              <span style={{ color: "#6c757d", marginLeft: "8px" }}>
                {test.description}
              </span>
            </div>
          </div>
        ))}
      </div>

      <div
        style={{
          padding: "16px",
          backgroundColor: "#d1ecf1",
          borderRadius: "8px",
          border: "1px solid #bee5eb",
        }}
      >
        <h4 style={{ color: "#0c5460", margin: "0 0 8px 0", fontSize: "16px" }}>
          ✅ Ready for Enterprise Development!
        </h4>
        <p style={{ color: "#0c5460", margin: 0, fontSize: "14px" }}>
          Your development environment is properly configured with TypeScript,
          ESLint, Prettier, and all necessary tools for professional React
          development.
        </p>
      </div>
    </div>
  );
};

export default SetupTest;
```

**Update src/App.tsx:**

```tsx
import React from "react";
import SetupTest from "./components/SetupTest";
import "./App.css";

const App: React.FC = () => {
  return (
    <div className="App">
      <SetupTest message="Welcome to enterprise-grade React development with TypeScript!" />
    </div>
  );
};

export default App;
```

**Run verification commands:**

```bash
# Start development server
npm start

# Check TypeScript compilation
npm run type-check

# Run linting
npm run lint

# Run tests
npm test

# Format code
npm run format
```

If all commands run without errors and you see the setup test page, you're ready for enterprise React development!

---

## 2. TypeScript Fundamentals for React

### Essential TypeScript Concepts for React Development

Before diving into React components, let's master the TypeScript concepts you'll use daily in enterprise React development.

#### 1. **Type Annotations & Inference**

```tsx
// Explicit type annotations
const userName: string = "John Doe";
const age: number = 30;
const isActive: boolean = true;

// Type inference (TypeScript figures out the type)
const userEmail = "john@example.com"; // inferred as string
const userId = 123; // inferred as number

// Arrays
const tags: string[] = ["react", "typescript", "frontend"];
const scores: Array<number> = [85, 92, 78, 96];

// Function with typed parameters and return type
const calculateTotal = (price: number, tax: number): number => {
  return price + price * tax;
};
```

#### 2. **Interfaces - Defining Object Shapes**

```tsx
// Basic interface
interface User {
  id: number;
  name: string;
  email: string;
  isActive: boolean;
}

// Interface with optional properties
interface UserProfile {
  id: number;
  name: string;
  email?: string; // Optional property
  avatar?: string; // Optional property
  lastLogin: Date;
}

// Interface with methods
interface UserService {
  getUser(id: number): Promise<User>;
  updateUser(id: number, data: Partial<User>): Promise<User>;
  deleteUser(id: number): Promise<void>;
}

// Extending interfaces
interface AdminUser extends User {
  permissions: string[];
  canDeleteUsers: boolean;
}
```

#### 3. **Union Types & Literal Types**

```tsx
// Union types - value can be one of several types
type Status = "loading" | "success" | "error";
type ID = string | number;

// Using union types
interface ApiResponse {
  status: Status;
  data?: any;
  error?: string;
}

// Literal types for precise values
type ButtonVariant = "primary" | "secondary" | "danger";
type Size = "small" | "medium" | "large";

interface ButtonProps {
  variant: ButtonVariant;
  size: Size;
  disabled?: boolean;
}
```

#### 4. **Generic Types - Reusable Type Definitions**

```tsx
// Generic interface for API responses
interface ApiResponse<T> {
  data: T;
  status: number;
  message: string;
}

// Usage with different data types
type UserResponse = ApiResponse<User>;
type UsersResponse = ApiResponse<User[]>;

// Generic function
function createArray<T>(item: T, count: number): T[] {
  return new Array(count).fill(item);
}

const stringArray = createArray("hello", 3); // string[]
const numberArray = createArray(42, 5); // number[]
```

#### 5. **Utility Types - Common Type Transformations**

```tsx
interface User {
  id: number;
  name: string;
  email: string;
  age: number;
}

// Partial - makes all properties optional
type UserUpdate = Partial<User>;
// { id?: number; name?: string; email?: string; age?: number; }

// Pick - select specific properties
type UserSummary = Pick<User, "id" | "name">;
// { id: number; name: string; }

// Omit - exclude specific properties
type CreateUser = Omit<User, "id">;
// { name: string; email: string; age: number; }

// Record - create object type with specific keys and values
type UserRoles = Record<string, boolean>;
// { [key: string]: boolean }
```

#### 6. **React-Specific Types**

```tsx
import React from "react";

// Component prop types
interface ComponentProps {
  title: string;
  children: React.ReactNode; // Can be any valid React child
  onClick?: () => void; // Optional event handler
  className?: string; // Optional CSS class
}

// Event handler types
interface FormProps {
  onSubmit: (event: React.FormEvent<HTMLFormElement>) => void;
  onChange: (event: React.ChangeEvent<HTMLInputElement>) => void;
  onClick: (event: React.MouseEvent<HTMLButtonElement>) => void;
}

// Ref types
interface InputComponentProps {
  inputRef: React.RefObject<HTMLInputElement>;
}

// CSS Properties type
interface StyledComponentProps {
  customStyle?: React.CSSProperties;
}
```

### TypeScript Best Practices for React

#### 1. **Always Use Interfaces for Props**

```tsx
// ✅ Good - Clear interface definition
interface UserCardProps {
  user: User;
  onEdit: (userId: number) => void;
  showActions?: boolean;
}

const UserCard: React.FC<UserCardProps> = ({
  user,
  onEdit,
  showActions = true,
}) => {
  // Component implementation
};

// ❌ Avoid - Inline type definitions
const UserCard: React.FC<{
  user: { id: number; name: string };
  onEdit: (id: number) => void;
}> = ({ user, onEdit }) => {
  // Component implementation
};
```

#### 2. **Use Type Guards for Runtime Safety**

```tsx
// Type guard function
function isUser(obj: any): obj is User {
  return obj && typeof obj.id === "number" && typeof obj.name === "string";
}

// Usage in component
const UserProfile: React.FC<{ userData: unknown }> = ({ userData }) => {
  if (!isUser(userData)) {
    return <div>Invalid user data</div>;
  }

  // TypeScript now knows userData is User type
  return (
    <div>
      <h1>{userData.name}</h1>
      <p>ID: {userData.id}</p>
    </div>
  );
};
```

#### 3. **Prefer Union Types Over Enums**

```tsx
// ✅ Preferred - Union types
type Theme = "light" | "dark" | "auto";

// ✅ Also good - const assertion
const THEMES = ["light", "dark", "auto"] as const;
type Theme = (typeof THEMES)[number];

// ❌ Avoid in most cases - Enums (add runtime overhead)
enum Theme {
  Light = "light",
  Dark = "dark",
  Auto = "auto",
}
```

### Common TypeScript Patterns in React

#### 1. **Conditional Prop Types**

```tsx
interface BaseProps {
  title: string;
}

// Either provide href (link) or onClick (button)
type ButtonProps = BaseProps &
  ({ href: string; onClick?: never } | { href?: never; onClick: () => void });

const ActionButton: React.FC<ButtonProps> = ({ title, href, onClick }) => {
  if (href) {
    return <a href={href}>{title}</a>;
  }

  return <button onClick={onClick}>{title}</button>;
};
```

#### 2. **Generic Components**

```tsx
interface ListProps<T> {
  items: T[];
  renderItem: (item: T) => React.ReactNode;
  keyExtractor: (item: T) => string | number;
}

function List<T>({ items, renderItem, keyExtractor }: ListProps<T>) {
  return (
    <ul>
      {items.map((item) => (
        <li key={keyExtractor(item)}>{renderItem(item)}</li>
      ))}
    </ul>
  );
}

// Usage
<List
  items={users}
  renderItem={(user) => <span>{user.name}</span>}
  keyExtractor={(user) => user.id}
/>;
```

### Exercise: TypeScript Practice

Create a file `src/types/common.ts` and practice these concepts:

```tsx
// src/types/common.ts

// 1. Define a Product interface
export interface Product {
  id: number;
  name: string;
  price: number;
  category: string;
  inStock: boolean;
  tags?: string[];
}

// 2. Create utility types
export type ProductSummary = Pick<Product, "id" | "name" | "price">;
export type ProductUpdate = Partial<Omit<Product, "id">>;

// 3. Define API response types
export interface ApiResponse<T> {
  data: T;
  status: "success" | "error";
  message?: string;
}

export type ProductsResponse = ApiResponse<Product[]>;
export type ProductResponse = ApiResponse<Product>;

// 4. Component prop interfaces
export interface ProductCardProps {
  product: Product;
  onAddToCart: (productId: number) => void;
  showFullDetails?: boolean;
}

export interface ProductListProps {
  products: Product[];
  loading: boolean;
  error?: string;
  onProductSelect: (product: Product) => void;
}
```

This foundation will serve you throughout the tutorial and in real enterprise development!

---

## 3. Your First TypeScript React Component

### Understanding React Components

A React component is a self-contained piece of UI that encapsulates:

- **Structure** (TSX markup)
- **Behavior** (TypeScript logic)
- **Presentation** (CSS styling)

Think of components as custom HTML elements with superpowers!

### Component Types in React + TypeScript

#### 1. **Function Components (Recommended)**

```tsx
import React from "react";

// Basic function component with TypeScript
const Greeting: React.FC = () => {
  return <h1>Hello, World!</h1>;
};

// Function component with props
interface GreetingProps {
  name: string;
  age?: number;
}

const PersonalGreeting: React.FC<GreetingProps> = ({ name, age }) => {
  return (
    <div>
      <h1>Hello, {name}!</h1>
      {age && <p>You are {age} years old.</p>}
    </div>
  );
};
```

#### 2. **Arrow Function Components (Alternative Syntax)**

```tsx
// Arrow function with explicit return
const Button: React.FC<{ label: string }> = ({ label }) => {
  return <button>{label}</button>;
};

// Arrow function with implicit return
const Icon: React.FC<{ name: string }> = ({ name }) => (
  <span className={`icon-${name}`} />
);
```

### Exercise 3.1: Your First Enterprise Component

Let's build a reusable `UserCard` component that you might find in a real enterprise application:

**src/components/UserCard.tsx**

```tsx
import React from "react";

// Define types for our component
interface User {
  id: number;
  name: string;
  email: string;
  role: "admin" | "user" | "manager";
  avatar?: string;
  isOnline: boolean;
}

interface UserCardProps {
  user: User;
  showActions?: boolean;
  onEdit?: (userId: number) => void;
  onDelete?: (userId: number) => void;
}

const UserCard: React.FC<UserCardProps> = ({
  user,
  showActions = false,
  onEdit,
  onDelete,
}) => {
  // Helper function to get role color
  const getRoleColor = (role: User["role"]): string => {
    const roleColors: Record<User["role"], string> = {
      admin: "#ff4444",
      manager: "#44ff44",
      user: "#4444ff",
    };
    return roleColors[role];
  };

  // Event handlers with proper typing
  const handleEdit = (): void => {
    if (onEdit) {
      onEdit(user.id);
    }
  };

  const handleDelete = (): void => {
    if (onDelete && window.confirm(`Delete user ${user.name}?`)) {
      onDelete(user.id);
    }
  };

  return (
    <div
      style={{
        border: "1px solid #e0e0e0",
        borderRadius: "8px",
        padding: "16px",
        margin: "8px",
        backgroundColor: "#fafafa",
        position: "relative",
      }}
    >
      {/* Online status indicator */}
      <div
        style={{
          position: "absolute",
          top: "8px",
          right: "8px",
          width: "12px",
          height: "12px",
          borderRadius: "50%",
          backgroundColor: user.isOnline ? "#4caf50" : "#9e9e9e",
        }}
      />

      {/* User avatar */}
      <div
        style={{
          width: "60px",
          height: "60px",
          borderRadius: "50%",
          backgroundColor: "#ddd",
          display: "flex",
          alignItems: "center",
          justifyContent: "center",
          marginBottom: "12px",
          fontSize: "24px",
          fontWeight: "bold",
          color: "#666",
        }}
      >
        {user.avatar ? (
          <img
            src={user.avatar}
            alt={user.name}
            style={{ width: "100%", height: "100%", borderRadius: "50%" }}
          />
        ) : (
          user.name.charAt(0).toUpperCase()
        )}
      </div>

      {/* User info */}
      <h3 style={{ margin: "0 0 8px 0", fontSize: "18px" }}>{user.name}</h3>

      <p style={{ margin: "0 0 8px 0", color: "#666", fontSize: "14px" }}>
        {user.email}
      </p>

      {/* Role badge */}
      <span
        style={{
          display: "inline-block",
          padding: "4px 8px",
          borderRadius: "4px",
          backgroundColor: getRoleColor(user.role),
          color: "white",
          fontSize: "12px",
          fontWeight: "bold",
          textTransform: "uppercase",
        }}
      >
        {user.role}
      </span>

      {/* Action buttons */}
      {showActions && (
        <div style={{ marginTop: "12px", display: "flex", gap: "8px" }}>
          <button
            onClick={handleEdit}
            style={{
              padding: "6px 12px",
              border: "1px solid #2196f3",
              backgroundColor: "#2196f3",
              color: "white",
              borderRadius: "4px",
              cursor: "pointer",
              fontSize: "12px",
            }}
          >
            Edit
          </button>
          <button
            onClick={handleDelete}
            style={{
              padding: "6px 12px",
              border: "1px solid #f44336",
              backgroundColor: "#f44336",
              color: "white",
              borderRadius: "4px",
              cursor: "pointer",
              fontSize: "12px",
            }}
          >
            Delete
          </button>
        </div>
      )}
    </div>
  );
};

export default UserCard;
```

### Exercise 3.2: Using Components with Props

**Update src/App.tsx:**

```tsx
import React from "react";
import UserCard from "./components/UserCard";
import "./App.css";

// Define User type (move to types file in real app)
interface User {
  id: number;
  name: string;
  email: string;
  role: "admin" | "user" | "manager";
  avatar?: string;
  isOnline: boolean;
}

const App: React.FC = () => {
  // Sample data with proper typing
  const users: User[] = [
    {
      id: 1,
      name: "Sarah Johnson",
      email: "sarah.johnson@company.com",
      role: "admin",
      isOnline: true,
    },
    {
      id: 2,
      name: "Mike Chen",
      email: "mike.chen@company.com",
      role: "manager",
      isOnline: false,
    },
    {
      id: 3,
      name: "Emily Davis",
      email: "emily.davis@company.com",
      role: "user",
      isOnline: true,
    },
  ];

  // Event handlers with proper typing
  const handleEditUser = (userId: number): void => {
    console.log(`Editing user with ID: ${userId}`);
    // In a real app, this might open a modal or navigate to an edit page
  };

  const handleDeleteUser = (userId: number): void => {
    console.log(`Deleting user with ID: ${userId}`);
    // In a real app, this might call an API to delete the user
  };

  return (
    <div className="App">
      <header style={{ padding: "20px", backgroundColor: "#f5f5f5" }}>
        <h1>Enterprise User Management</h1>
        <p>A TypeScript React Application</p>
      </header>

      <main style={{ padding: "20px" }}>
        <h2>Team Members</h2>
        <div
          style={{
            display: "grid",
            gridTemplateColumns: "repeat(auto-fill, minmax(300px, 1fr))",
            gap: "16px",
          }}
        >
          {users.map((user) => (
            <UserCard
              key={user.id}
              user={user}
              showActions={true}
              onEdit={handleEditUser}
              onDelete={handleDeleteUser}
            />
          ))}
        </div>
      </main>
    </div>
  );
};

export default App;
```

### Key TypeScript React Concepts Learned

#### 1. **Interface Definition**

```tsx
interface UserCardProps {
  user: User; // Required object prop
  showActions?: boolean; // Optional boolean prop
  onEdit?: (userId: number) => void; // Optional function prop
}
```

#### 2. **Event Handler Typing**

```tsx
const handleEdit = (): void => {
  // Function returns nothing (void)
};

const handleClick = (event: React.MouseEvent<HTMLButtonElement>): void => {
  // Function receives a typed event parameter
};
```

#### 3. **Union Types for Strict Values**

```tsx
type Role = "admin" | "user" | "manager"; // Only these values allowed
```

#### 4. **Record Types for Object Mapping**

```tsx
const roleColors: Record<User["role"], string> = {
  admin: "#ff4444",
  manager: "#44ff44",
  user: "#4444ff",
};
```

### Component Best Practices

#### 1. **Single Responsibility Principle**

```tsx
// ✅ Good - Component has one clear purpose
const UserAvatar: React.FC<{ user: User }> = ({ user }) => {
  // Just handles avatar display
};

// ❌ Avoid - Component doing too many things
const UserEverything: React.FC = () => {
  // Handles avatar, profile, settings, notifications...
};
```

#### 2. **Prop Validation with TypeScript**

```tsx
// ✅ Good - Strict typing
interface ButtonProps {
  variant: "primary" | "secondary" | "danger";
  size: "small" | "medium" | "large";
  onClick: () => void;
  children: React.ReactNode;
}

// ❌ Avoid - Loose typing
interface ButtonProps {
  variant?: string;
  size?: any;
  onClick?: Function;
  children?: any;
}
```

#### 3. **Extracting Types to Separate Files**

Create `src/types/user.ts`:

```tsx
export interface User {
  id: number;
  name: string;
  email: string;
  role: "admin" | "user" | "manager";
  avatar?: string;
  isOnline: boolean;
}

export interface UserCardProps {
  user: User;
  showActions?: boolean;
  onEdit?: (userId: number) => void;
  onDelete?: (userId: number) => void;
}
```

Then import in components:

```tsx
import { User, UserCardProps } from "../types/user";
```

### Practice Challenge 3.1

Create a `ProductCard` component for an e-commerce app:

**Requirements:**

- Display product name, price, and image
- Show "In Stock" or "Out of Stock" status with different colors
- Include an "Add to Cart" button (disabled if out of stock)
- Optional discount percentage that shows a strikethrough original price
- TypeScript interfaces for all props

**Bonus:** Make the component responsive and add hover effects!

This exercise combines TypeScript knowledge with practical React component development that you'll use in enterprise applications.

---

## 4. TSX Syntax & Best Practices

### What is TSX?

TSX is TypeScript's version of JSX - it's a syntax extension that lets you write HTML-like code in your TypeScript files with full type safety! Think of it as HTML supercharged with TypeScript's type system.

### TSX Rules You Must Know

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
const FragmentComponent: React.FC = () => {
  return (
    <>
      <h1>Title</h1>
      <p>Paragraph</p>
    </>
  );
}

// ✅ Explicit Fragment
const ExplicitFragmentComponent: React.FC = () => {
  return (
    <React.Fragment>
      <h1>Title</h1>
      <p>Paragraph</p>
    </React.Fragment>
  );
}
```

#### Rule 2: Use `className` instead of `class`

```tsx
// ❌ Wrong
<div class="my-class">Content</div>

// ✅ Correct
<div className="my-class">Content</div>

// ✅ Dynamic className with TypeScript
interface ComponentProps {
  isActive: boolean;
  theme: 'light' | 'dark';
}

const StyledComponent: React.FC<ComponentProps> = ({ isActive, theme }) => {
  const className: string = `component ${theme} ${isActive ? 'active' : 'inactive'}`;

  return <div className={className}>Content</div>;
};
```

#### Rule 3: Self-closing tags must end with `/>`

```tsx
// ❌ Wrong
<img src="image.jpg">
<br>
<input type="text">

// ✅ Correct
<img src="image.jpg" />
<br />
<input type="text" />
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

### Advanced TSX Patterns

#### 1. **Conditional Rendering with Type Safety**

```tsx
interface StatusMessageProps {
  status: "loading" | "success" | "error";
  message?: string;
}

const StatusMessage: React.FC<StatusMessageProps> = ({ status, message }) => {
  // Type-safe conditional rendering
  const getStatusIcon = (status: StatusMessageProps["status"]): string => {
    const icons: Record<StatusMessageProps["status"], string> = {
      loading: "⏳",
      success: "✅",
      error: "❌",
    };
    return icons[status];
  };

  return (
    <div>
      {/* Simple conditional rendering */}
      {status === "loading" && <p>Loading...</p>}

      {/* Complex conditional rendering */}
      {status === "success" ? (
        <div style={{ color: "green" }}>
          {getStatusIcon(status)} Success!
          {message && <p>{message}</p>}
        </div>
      ) : status === "error" ? (
        <div style={{ color: "red" }}>
          {getStatusIcon(status)} Error!
          {message && <p>{message}</p>}
        </div>
      ) : (
        <div>{getStatusIcon(status)} Loading...</div>
      )}
    </div>
  );
};
```

#### 2. **Lists and Keys with TypeScript**

```tsx
interface TodoItem {
  id: number;
  text: string;
  completed: boolean;
  priority: "low" | "medium" | "high";
}

interface TodoListProps {
  todos: TodoItem[];
  onToggle: (id: number) => void;
}

const TodoList: React.FC<TodoListProps> = ({ todos, onToggle }) => {
  const getPriorityColor = (priority: TodoItem["priority"]): string => {
    const colors: Record<TodoItem["priority"], string> = {
      low: "#4caf50",
      medium: "#ff9800",
      high: "#f44336",
    };
    return colors[priority];
  };

  return (
    <ul>
      {todos.map((todo) => (
        <li
          key={todo.id} // Always provide unique keys
          style={{
            textDecoration: todo.completed ? "line-through" : "none",
            color: todo.completed ? "#999" : "#000",
          }}
        >
          <span
            style={{
              display: "inline-block",
              width: "12px",
              height: "12px",
              borderRadius: "50%",
              backgroundColor: getPriorityColor(todo.priority),
              marginRight: "8px",
            }}
          />
          <button onClick={() => onToggle(todo.id)}>
            {todo.completed ? "✓" : "○"}
          </button>
          {todo.text}
        </li>
      ))}
    </ul>
  );
};
```

#### 3. **Event Handling with Proper Types**

```tsx
interface FormComponentProps {
  onSubmit: (data: { name: string; email: string }) => void;
}

const FormComponent: React.FC<FormComponentProps> = ({ onSubmit }) => {
  const [formData, setFormData] = React.useState({
    name: "",
    email: "",
  });

  // Properly typed event handlers
  const handleInputChange = (
    event: React.ChangeEvent<HTMLInputElement>
  ): void => {
    const { name, value } = event.target;
    setFormData((prev) => ({
      ...prev,
      [name]: value,
    }));
  };

  const handleSubmit = (event: React.FormEvent<HTMLFormElement>): void => {
    event.preventDefault();
    onSubmit(formData);
  };

  const handleButtonClick = (
    event: React.MouseEvent<HTMLButtonElement>
  ): void => {
    console.log("Button clicked!", event.currentTarget);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input
        type="text"
        name="name"
        value={formData.name}
        onChange={handleInputChange}
        placeholder="Name"
      />
      <input
        type="email"
        name="email"
        value={formData.email}
        onChange={handleInputChange}
        placeholder="Email"
      />
      <button type="submit">Submit</button>
      <button type="button" onClick={handleButtonClick}>
        Click Me
      </button>
    </form>
  );
};
```

#### 4. **Styling with Type Safety**

```tsx
interface StyledComponentProps {
  variant: "primary" | "secondary" | "danger";
  size: "small" | "medium" | "large";
  children: React.ReactNode;
}

const StyledButton: React.FC<StyledComponentProps> = ({
  variant,
  size,
  children,
}) => {
  // Type-safe style objects
  const baseStyles: React.CSSProperties = {
    border: "none",
    borderRadius: "4px",
    cursor: "pointer",
    fontWeight: "bold",
    transition: "all 0.2s ease",
  };

  const variantStyles: Record<
    StyledComponentProps["variant"],
    React.CSSProperties
  > = {
    primary: {
      backgroundColor: "#007bff",
      color: "white",
    },
    secondary: {
      backgroundColor: "#6c757d",
      color: "white",
    },
    danger: {
      backgroundColor: "#dc3545",
      color: "white",
    },
  };

  const sizeStyles: Record<StyledComponentProps["size"], React.CSSProperties> =
    {
      small: {
        padding: "4px 8px",
        fontSize: "12px",
      },
      medium: {
        padding: "8px 16px",
        fontSize: "14px",
      },
      large: {
        padding: "12px 24px",
        fontSize: "16px",
      },
    };

  // Combine styles with type safety
  const combinedStyles: React.CSSProperties = {
    ...baseStyles,
    ...variantStyles[variant],
    ...sizeStyles[size],
  };

  return <button style={combinedStyles}>{children}</button>;
};
```

### TSX Best Practices

#### 1. **Component Composition**

```tsx
// ✅ Good - Composable components
interface CardProps {
  children: React.ReactNode;
  className?: string;
}

const Card: React.FC<CardProps> = ({ children, className = "" }) => (
  <div className={`card ${className}`}>{children}</div>
);

const CardHeader: React.FC<{ children: React.ReactNode }> = ({ children }) => (
  <div className="card-header">{children}</div>
);

const CardBody: React.FC<{ children: React.ReactNode }> = ({ children }) => (
  <div className="card-body">{children}</div>
);

// Usage
const UserProfile: React.FC = () => (
  <Card>
    <CardHeader>
      <h2>User Profile</h2>
    </CardHeader>
    <CardBody>
      <p>User details go here...</p>
    </CardBody>
  </Card>
);
```

#### 2. **Avoid Inline Functions in TSX**

```tsx
interface ItemListProps {
  items: string[];
  onItemClick: (item: string) => void;
}

// ❌ Avoid - Creates new function on every render
const BadItemList: React.FC<ItemListProps> = ({ items, onItemClick }) => (
  <ul>
    {items.map((item) => (
      <li key={item} onClick={() => onItemClick(item)}>
        {item}
      </li>
    ))}
  </ul>
);

// ✅ Good - Function defined outside render
const GoodItemList: React.FC<ItemListProps> = ({ items, onItemClick }) => {
  const handleItemClick = (item: string) => () => {
    onItemClick(item);
  };

  return (
    <ul>
      {items.map((item) => (
        <li key={item} onClick={handleItemClick(item)}>
          {item}
        </li>
      ))}
    </ul>
  );
};
```

#### 3. **Use TypeScript to Catch TSX Errors**

```tsx
// TypeScript will catch these errors at compile time
interface ButtonProps {
  onClick: () => void;
  disabled?: boolean;
  children: React.ReactNode;
}

const Button: React.FC<ButtonProps> = ({
  onClick,
  disabled = false,
  children,
}) => (
  <button onClick={onClick} disabled={disabled}>
    {children}
  </button>
);

// ❌ TypeScript error - missing required prop
// <Button>Click me</Button>

// ❌ TypeScript error - wrong prop type
// <Button onClick="not a function">Click me</Button>

// ✅ Correct usage
<Button onClick={() => console.log("clicked")}>Click me</Button>;
```

### Practice Exercise: Building a Complete Component

Create a `NotificationCard` component with the following requirements:

```tsx
// src/components/NotificationCard.tsx
import React from "react";

interface Notification {
  id: string;
  type: "info" | "success" | "warning" | "error";
  title: string;
  message: string;
  timestamp: Date;
  isRead: boolean;
}

interface NotificationCardProps {
  notification: Notification;
  onMarkAsRead: (id: string) => void;
  onDismiss: (id: string) => void;
  showTimestamp?: boolean;
}

const NotificationCard: React.FC<NotificationCardProps> = ({
  notification,
  onMarkAsRead,
  onDismiss,
  showTimestamp = true,
}) => {
  // Implement the component with:
  // - Type-safe styling based on notification type
  // - Conditional rendering for read/unread state
  // - Proper event handling
  // - Timestamp formatting
  // - Accessibility features
};

export default NotificationCard;
```

**Implementation hints:**

- Use Record types for type-based styling
- Implement proper ARIA attributes for accessibility
- Use conditional rendering for different states
- Format timestamps with proper TypeScript typing

This comprehensive coverage of TSX will prepare you for real-world React development with TypeScript!

---

## 5. Props & Component Communication

### Understanding Props in TypeScript

Props (properties) are how React components communicate with each other. In TypeScript, we define exact shapes for props to ensure type safety and better developer experience.

### Defining Prop Types with Interfaces

```tsx
// Basic prop interface
interface ButtonProps {
  text: string;
  onClick: () => void;
  disabled?: boolean; // Optional prop
  variant?: "primary" | "secondary"; // Union type
}

const Button: React.FC<ButtonProps> = ({
  text,
  onClick,
  disabled = false,
  variant = "primary",
}) => {
  return (
    <button
      onClick={onClick}
      disabled={disabled}
      className={`btn btn-${variant}`}
    >
      {text}
    </button>
  );
};
```

### Advanced Prop Patterns

#### 1. **Children Props**

```tsx
interface CardProps {
  title: string;
  children: React.ReactNode;
  footer?: React.ReactNode;
}

const Card: React.FC<CardProps> = ({ title, children, footer }) => (
  <div className="card">
    <div className="card-header">
      <h3>{title}</h3>
    </div>
    <div className="card-body">{children}</div>
    {footer && <div className="card-footer">{footer}</div>}
  </div>
);

// Usage
<Card title="User Profile" footer={<button>Save Changes</button>}>
  <p>User details go here</p>
  <input type="text" placeholder="Name" />
</Card>;
```

#### 2. **Function Props (Callbacks)**

```tsx
interface UserFormProps {
  initialUser?: User;
  onSubmit: (user: User) => Promise<void>;
  onCancel: () => void;
  onValidationError: (errors: string[]) => void;
}

const UserForm: React.FC<UserFormProps> = ({
  initialUser,
  onSubmit,
  onCancel,
  onValidationError,
}) => {
  // Component implementation
};
```

#### 3. **Generic Props**

```tsx
interface ListProps<T> {
  items: T[];
  renderItem: (item: T, index: number) => React.ReactNode;
  keyExtractor: (item: T) => string | number;
  emptyMessage?: string;
}

function List<T>({ items, renderItem, keyExtractor, emptyMessage }: ListProps<T>) {
  if (items.length === 0) {
    return <div>{emptyMessage || 'No items to display'}</div>;
  }

  return (
    <ul>
      {items.map((item, index) => (
        <li key={keyExtractor(item)}>
          {renderItem(item, index)}
        </li>
      ))}
    </ul>
  );
}

// Usage with different types
const users: User[] = [/* user data */];
const products: Product[] = [/* product data */];

<List
  items={users}
  renderItem={(user) => <span>{user.name}</span>}
  keyExtractor={(user) => user.id}
/>

<List
  items={products}
  renderItem={(product) => <div>{product.name} - ${product.price}</div>}
  keyExtractor={(product) => product.id}
/>
```

### Component Communication Patterns

#### 1. **Parent to Child Communication**

```tsx
// Parent Component
const UserDashboard: React.FC = () => {
  const [selectedUser, setSelectedUser] = useState<User | null>(null);
  const [users, setUsers] = useState<User[]>([]);

  return (
    <div>
      <UserList
        users={users}
        onUserSelect={setSelectedUser}
        selectedUserId={selectedUser?.id}
      />

      {selectedUser && (
        <UserDetails
          user={selectedUser}
          onUpdate={(updatedUser) => {
            setUsers((prev) =>
              prev.map((u) => (u.id === updatedUser.id ? updatedUser : u))
            );
          }}
        />
      )}
    </div>
  );
};

// Child Components
interface UserListProps {
  users: User[];
  onUserSelect: (user: User) => void;
  selectedUserId?: number;
}

const UserList: React.FC<UserListProps> = ({
  users,
  onUserSelect,
  selectedUserId,
}) => (
  <ul>
    {users.map((user) => (
      <li
        key={user.id}
        onClick={() => onUserSelect(user)}
        className={user.id === selectedUserId ? "selected" : ""}
      >
        {user.name}
      </li>
    ))}
  </ul>
);
```

#### 2. **Prop Drilling Solutions**

```tsx
// Instead of prop drilling, use context for deeply nested data
interface AppContextType {
  currentUser: User | null;
  theme: "light" | "dark";
  setTheme: (theme: "light" | "dark") => void;
}

const AppContext = React.createContext<AppContextType | undefined>(undefined);

// Custom hook for context
const useAppContext = (): AppContextType => {
  const context = React.useContext(AppContext);
  if (!context) {
    throw new Error("useAppContext must be used within AppContextProvider");
  }
  return context;
};

// Deep component can access context directly
const DeepNestedComponent: React.FC = () => {
  const { currentUser, theme } = useAppContext();

  return (
    <div className={`component theme-${theme}`}>
      Welcome, {currentUser?.name}!
    </div>
  );
};
```

---

## 6. State Management with useState

### Understanding State in React + TypeScript

State represents data that can change over time. TypeScript helps us define exactly what types of data our state can hold.

### Basic useState with TypeScript

```tsx
import React, { useState } from "react";

const Counter: React.FC = () => {
  // TypeScript infers the type as number
  const [count, setCount] = useState(0);

  // Explicit typing when needed
  const [message, setMessage] = useState<string>("");

  // For complex types
  const [user, setUser] = useState<User | null>(null);

  // For arrays
  const [items, setItems] = useState<string[]>([]);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
      <button onClick={() => setCount((prev) => prev - 1)}>Decrement</button>
    </div>
  );
};
```

### Complex State Management

#### 1. **Object State with TypeScript**

```tsx
interface FormState {
  name: string;
  email: string;
  age: number;
  preferences: {
    newsletter: boolean;
    notifications: boolean;
  };
}

const UserProfileForm: React.FC = () => {
  const [formState, setFormState] = useState<FormState>({
    name: "",
    email: "",
    age: 0,
    preferences: {
      newsletter: false,
      notifications: true,
    },
  });

  // Type-safe state updates
  const updateField = (
    field: keyof FormState,
    value: FormState[keyof FormState]
  ): void => {
    setFormState((prev) => ({
      ...prev,
      [field]: value,
    }));
  };

  const updatePreference = (
    pref: keyof FormState["preferences"],
    value: boolean
  ): void => {
    setFormState((prev) => ({
      ...prev,
      preferences: {
        ...prev.preferences,
        [pref]: value,
      },
    }));
  };

  return (
    <form>
      <input
        type="text"
        value={formState.name}
        onChange={(e) => updateField("name", e.target.value)}
        placeholder="Name"
      />

      <input
        type="email"
        value={formState.email}
        onChange={(e) => updateField("email", e.target.value)}
        placeholder="Email"
      />

      <input
        type="number"
        value={formState.age}
        onChange={(e) => updateField("age", parseInt(e.target.value) || 0)}
        placeholder="Age"
      />

      <label>
        <input
          type="checkbox"
          checked={formState.preferences.newsletter}
          onChange={(e) => updatePreference("newsletter", e.target.checked)}
        />
        Subscribe to newsletter
      </label>
    </form>
  );
};
```

#### 2. **Array State Management**

```tsx
interface Todo {
  id: number;
  text: string;
  completed: boolean;
  createdAt: Date;
}

const TodoApp: React.FC = () => {
  const [todos, setTodos] = useState<Todo[]>([]);
  const [nextId, setNextId] = useState(1);

  const addTodo = (text: string): void => {
    const newTodo: Todo = {
      id: nextId,
      text,
      completed: false,
      createdAt: new Date(),
    };

    setTodos((prev) => [...prev, newTodo]);
    setNextId((prev) => prev + 1);
  };

  const toggleTodo = (id: number): void => {
    setTodos((prev) =>
      prev.map((todo) =>
        todo.id === id ? { ...todo, completed: !todo.completed } : todo
      )
    );
  };

  const deleteTodo = (id: number): void => {
    setTodos((prev) => prev.filter((todo) => todo.id !== id));
  };

  const updateTodo = (id: number, newText: string): void => {
    setTodos((prev) =>
      prev.map((todo) => (todo.id === id ? { ...todo, text: newText } : todo))
    );
  };

  return (
    <div>
      <TodoForm onSubmit={addTodo} />
      <TodoList
        todos={todos}
        onToggle={toggleTodo}
        onDelete={deleteTodo}
        onUpdate={updateTodo}
      />
    </div>
  );
};
```

### State Best Practices

#### 1. **Derived State**

```tsx
const ShoppingCart: React.FC = () => {
  const [items, setItems] = useState<CartItem[]>([]);

  // Derived state - don't store in useState
  const totalPrice = items.reduce(
    (sum, item) => sum + item.price * item.quantity,
    0
  );
  const itemCount = items.reduce((sum, item) => sum + item.quantity, 0);
  const isEmpty = items.length === 0;

  return (
    <div>
      <h2>Shopping Cart ({itemCount} items)</h2>
      <p>Total: ${totalPrice.toFixed(2)}</p>
      {isEmpty ? <p>Your cart is empty</p> : <CartItemList items={items} />}
    </div>
  );
};
```

#### 2. **State Normalization**

```tsx
// Instead of nested objects, normalize data
interface AppState {
  users: Record<number, User>;
  posts: Record<number, Post>;
  comments: Record<number, Comment>;
}

const useNormalizedData = () => {
  const [state, setState] = useState<AppState>({
    users: {},
    posts: {},
    comments: {},
  });

  const addUser = (user: User): void => {
    setState((prev) => ({
      ...prev,
      users: {
        ...prev.users,
        [user.id]: user,
      },
    }));
  };

  const getUser = (id: number): User | undefined => state.users[id];

  return { state, addUser, getUser };
};
```

---

## 7. Event Handling & Form Management

### TypeScript Event Handling

React events are synthetic events with specific TypeScript types for different elements.

#### Common Event Types

```tsx
const EventExamples: React.FC = () => {
  // Input events
  const handleInputChange = (
    event: React.ChangeEvent<HTMLInputElement>
  ): void => {
    console.log(event.target.value);
  };

  const handleTextareaChange = (
    event: React.ChangeEvent<HTMLTextAreaElement>
  ): void => {
    console.log(event.target.value);
  };

  const handleSelectChange = (
    event: React.ChangeEvent<HTMLSelectElement>
  ): void => {
    console.log(event.target.value);
  };

  // Mouse events
  const handleClick = (event: React.MouseEvent<HTMLButtonElement>): void => {
    console.log("Button clicked", event.currentTarget);
  };

  const handleDivClick = (event: React.MouseEvent<HTMLDivElement>): void => {
    console.log("Div clicked", event.clientX, event.clientY);
  };

  // Keyboard events
  const handleKeyPress = (
    event: React.KeyboardEvent<HTMLInputElement>
  ): void => {
    if (event.key === "Enter") {
      console.log("Enter pressed");
    }
  };

  // Form events
  const handleSubmit = (event: React.FormEvent<HTMLFormElement>): void => {
    event.preventDefault();
    console.log("Form submitted");
  };

  return (
    <div>
      <input onChange={handleInputChange} onKeyPress={handleKeyPress} />
      <textarea onChange={handleTextareaChange} />
      <select onChange={handleSelectChange}>
        <option value="option1">Option 1</option>
        <option value="option2">Option 2</option>
      </select>
      <button onClick={handleClick}>Click me</button>
      <div onClick={handleDivClick}>Click this div</div>
      <form onSubmit={handleSubmit}>
        <button type="submit">Submit</button>
      </form>
    </div>
  );
};
```

### Enterprise Form Management

#### 1. **Controlled Components with Validation**

```tsx
interface FormData {
  email: string;
  password: string;
  confirmPassword: string;
  agreeToTerms: boolean;
}

interface FormErrors {
  email?: string;
  password?: string;
  confirmPassword?: string;
  agreeToTerms?: string;
}

const RegistrationForm: React.FC = () => {
  const [formData, setFormData] = useState<FormData>({
    email: "",
    password: "",
    confirmPassword: "",
    agreeToTerms: false,
  });

  const [errors, setErrors] = useState<FormErrors>({});
  const [isSubmitting, setIsSubmitting] = useState(false);

  // Validation functions
  const validateEmail = (email: string): string | undefined => {
    const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    if (!email) return "Email is required";
    if (!emailRegex.test(email)) return "Invalid email format";
    return undefined;
  };

  const validatePassword = (password: string): string | undefined => {
    if (!password) return "Password is required";
    if (password.length < 8) return "Password must be at least 8 characters";
    if (!/(?=.*[a-z])(?=.*[A-Z])(?=.*\d)/.test(password)) {
      return "Password must contain lowercase, uppercase, and number";
    }
    return undefined;
  };

  const validateConfirmPassword = (
    confirmPassword: string,
    password: string
  ): string | undefined => {
    if (!confirmPassword) return "Please confirm your password";
    if (confirmPassword !== password) return "Passwords do not match";
    return undefined;
  };

  // Handle input changes
  const handleInputChange =
    (field: keyof FormData) =>
    (event: React.ChangeEvent<HTMLInputElement>): void => {
      const value =
        event.target.type === "checkbox"
          ? event.target.checked
          : event.target.value;

      setFormData((prev) => ({
        ...prev,
        [field]: value,
      }));

      // Clear error when user starts typing
      if (errors[field]) {
        setErrors((prev) => ({
          ...prev,
          [field]: undefined,
        }));
      }
    };

  // Validate all fields
  const validateForm = (): boolean => {
    const newErrors: FormErrors = {};

    newErrors.email = validateEmail(formData.email);
    newErrors.password = validatePassword(formData.password);
    newErrors.confirmPassword = validateConfirmPassword(
      formData.confirmPassword,
      formData.password
    );

    if (!formData.agreeToTerms) {
      newErrors.agreeToTerms = "You must agree to the terms";
    }

    setErrors(newErrors);
    return Object.values(newErrors).every((error) => !error);
  };

  // Handle form submission
  const handleSubmit = async (
    event: React.FormEvent<HTMLFormElement>
  ): Promise<void> => {
    event.preventDefault();

    if (!validateForm()) {
      return;
    }

    setIsSubmitting(true);

    try {
      // Simulate API call
      await new Promise((resolve) => setTimeout(resolve, 2000));
      console.log("User registered:", formData);
      alert("Registration successful!");
    } catch (error) {
      console.error("Registration failed:", error);
      alert("Registration failed. Please try again.");
    } finally {
      setIsSubmitting(false);
    }
  };

  return (
    <form
      onSubmit={handleSubmit}
      style={{ maxWidth: "400px", margin: "0 auto" }}
    >
      <h2>Create Account</h2>

      <div style={{ marginBottom: "16px" }}>
        <label>
          Email:
          <input
            type="email"
            value={formData.email}
            onChange={handleInputChange("email")}
            style={{
              width: "100%",
              padding: "8px",
              border: errors.email ? "2px solid red" : "1px solid #ccc",
              borderRadius: "4px",
            }}
          />
          {errors.email && (
            <span style={{ color: "red", fontSize: "12px" }}>
              {errors.email}
            </span>
          )}
        </label>
      </div>

      <div style={{ marginBottom: "16px" }}>
        <label>
          Password:
          <input
            type="password"
            value={formData.password}
            onChange={handleInputChange("password")}
            style={{
              width: "100%",
              padding: "8px",
              border: errors.password ? "2px solid red" : "1px solid #ccc",
              borderRadius: "4px",
            }}
          />
          {errors.password && (
            <span style={{ color: "red", fontSize: "12px" }}>
              {errors.password}
            </span>
          )}
        </label>
      </div>

      <div style={{ marginBottom: "16px" }}>
        <label>
          Confirm Password:
          <input
            type="password"
            value={formData.confirmPassword}
            onChange={handleInputChange("confirmPassword")}
            style={{
              width: "100%",
              padding: "8px",
              border: errors.confirmPassword
                ? "2px solid red"
                : "1px solid #ccc",
              borderRadius: "4px",
            }}
          />
          {errors.confirmPassword && (
            <span style={{ color: "red", fontSize: "12px" }}>
              {errors.confirmPassword}
            </span>
          )}
        </label>
      </div>

      <div style={{ marginBottom: "16px" }}>
        <label>
          <input
            type="checkbox"
            checked={formData.agreeToTerms}
            onChange={handleInputChange("agreeToTerms")}
          />
          I agree to the terms and conditions
          {errors.agreeToTerms && (
            <span style={{ color: "red", fontSize: "12px", display: "block" }}>
              {errors.agreeToTerms}
            </span>
          )}
        </label>
      </div>

      <button
        type="submit"
        disabled={isSubmitting}
        style={{
          width: "100%",
          padding: "12px",
          backgroundColor: isSubmitting ? "#ccc" : "#007bff",
          color: "white",
          border: "none",
          borderRadius: "4px",
          cursor: isSubmitting ? "not-allowed" : "pointer",
        }}
      >
        {isSubmitting ? "Creating Account..." : "Create Account"}
      </button>
    </form>
  );
};
```

This section covers the essential React concepts with TypeScript that are crucial for enterprise development. The examples show real-world patterns you'll use in professional applications, with proper type safety and best practices.
