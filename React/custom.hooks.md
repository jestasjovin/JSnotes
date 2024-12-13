Creating custom hooks in React is a great way to extract and reuse logic across different components. A custom hook is simply a JavaScript function that uses built-in React hooks (like `useState`, `useEffect`, `useReducer`, etc.) and returns values or functions for reuse.

Here’s how to create and use custom hooks in React:

---

### **1. Basic Custom Hook**

Let's start by creating a simple custom hook that manages a counter.

#### **Example: `useCounter` Hook**

```js
import { useState } from 'react';

// Custom Hook to manage counter
function useCounter(initialValue = 0) {
  const [count, setCount] = useState(initialValue);

  const increment = () => setCount((prevCount) => prevCount + 1);
  const decrement = () => setCount((prevCount) => prevCount - 1);
  const reset = () => setCount(initialValue);

  return { count, increment, decrement, reset };
}

export default useCounter;
```

#### **Using `useCounter` in a Component**

```js
import React from 'react';
import useCounter from './useCounter'; // Import custom hook

const CounterComponent = () => {
  const { count, increment, decrement, reset } = useCounter(10);

  return (
    <div>
      <h1>Count: {count}</h1>
      <button onClick={increment}>Increment</button>
      <button onClick={decrement}>Decrement</button>
      <button onClick={reset}>Reset</button>
    </div>
  );
};

export default CounterComponent;
```

#### **Key Points**:
- `useCounter` is a custom hook that returns `count`, `increment`, `decrement`, and `reset` functions, which are then used in the `CounterComponent`.
- Custom hooks follow the naming convention of `use<name>`, like `useCounter`, `useFetch`, etc.
- A custom hook can use other hooks internally to manage state, side effects, or any logic.

---

### **2. Custom Hook with Fetching Data (`useFetch`)**

Fetching data is a common task in many applications. Let's create a custom hook that handles data fetching.

#### **Example: `useFetch` Hook**

```js
import { useState, useEffect } from 'react';

function useFetch(url) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    const fetchData = async () => {
      try {
        const response = await fetch(url);
        if (!response.ok) {
          throw new Error('Failed to fetch data');
        }
        const result = await response.json();
        setData(result);
      } catch (err) {
        setError(err.message);
      } finally {
        setLoading(false);
      }
    };

    fetchData();
  }, [url]); // Dependency array makes sure it re-fetches if `url` changes.

  return { data, loading, error };
}

export default useFetch;
```

#### **Using `useFetch` in a Component**

```js
import React from 'react';
import useFetch from './useFetch'; // Import custom hook

const DataComponent = () => {
  const { data, loading, error } = useFetch('https://api.example.com/data');

  if (loading) return <p>Loading...</p>;
  if (error) return <p>Error: {error}</p>;

  return (
    <div>
      <h1>Data from API:</h1>
      <pre>{JSON.stringify(data, null, 2)}</pre>
    </div>
  );
};

export default DataComponent;
```

#### **Key Points**:
- The `useFetch` custom hook handles the data fetching logic, such as loading state, error handling, and storing fetched data.
- By calling `useFetch` in different components with different URLs, you can reuse the data fetching logic across your app.

---

### **3. Custom Hook with Local Storage (`useLocalStorage`)**

Sometimes you may want to save the state in the browser’s local storage so it persists across page reloads. You can create a custom hook to manage this.

#### **Example: `useLocalStorage` Hook**

```js
import { useState } from 'react';

// Custom Hook for localStorage
function useLocalStorage(key, initialValue) {
  const storedValue = localStorage.getItem(key);
  const [value, setValue] = useState(storedValue ? JSON.parse(storedValue) : initialValue);

  const setLocalStorage = (newValue) => {
    setValue(newValue);
    localStorage.setItem(key, JSON.stringify(newValue));
  };

  return [value, setLocalStorage];
}

export default useLocalStorage;
```

#### **Using `useLocalStorage` in a Component**

```js
import React from 'react';
import useLocalStorage from './useLocalStorage'; // Import custom hook

const LocalStorageComponent = () => {
  const [name, setName] = useLocalStorage('name', 'John Doe');

  return (
    <div>
      <h1>Stored Name: {name}</h1>
      <input
        type="text"
        value={name}
        onChange={(e) => setName(e.target.value)}
        placeholder="Enter your name"
      />
    </div>
  );
};

export default LocalStorageComponent;
```

#### **Key Points**:
- The `useLocalStorage` hook allows you to store and retrieve a value from the browser's localStorage, while also keeping the state in sync with the UI.
- It persists the state even after a page reload.

---

### **4. Custom Hook for Window Dimensions (`useWindowDimensions`)**

A useful custom hook can track the window’s width and height, especially when building responsive UIs.

#### **Example: `useWindowDimensions` Hook**

```js
import { useState, useEffect } from 'react';

function useWindowDimensions() {
  const [windowSize, setWindowSize] = useState({
    width: window.innerWidth,
    height: window.innerHeight,
  });

  useEffect(() => {
    const handleResize = () => {
      setWindowSize({
        width: window.innerWidth,
        height: window.innerHeight,
      });
    };

    window.addEventListener('resize', handleResize);

    // Cleanup the event listener
    return () => {
      window.removeEventListener('resize', handleResize);
    };
  }, []); // Empty dependency array ensures this effect runs only once (component mount)

  return windowSize;
}

export default useWindowDimensions;
```

#### **Using `useWindowDimensions` in a Component**

```js
import React from 'react';
import useWindowDimensions from './useWindowDimensions'; // Import custom hook

const ResponsiveComponent = () => {
  const { width, height } = useWindowDimensions();

  return (
    <div>
      <p>Window Width: {width}px</p>
      <p>Window Height: {height}px</p>
    </div>
  );
};

export default ResponsiveComponent;
```

#### **Key Points**:
- `useWindowDimensions` listens to window resizing and provides the current window's width and height.
- It ensures the component reacts to changes in the browser window size.

---

### **5. Custom Hook for Timer (`useTimer`)**

If you need a custom hook to implement a timer (e.g., for a countdown timer), here's an example.

#### **Example: `useTimer` Hook**

```js
import { useState, useEffect } from 'react';

function useTimer(initialTime = 60) {
  const [time, setTime] = useState(initialTime);
  const [isRunning, setIsRunning] = useState(false);

  useEffect(() => {
    let timer;

    if (isRunning && time > 0) {
      timer = setInterval(() => setTime((prevTime) => prevTime - 1), 1000);
    } else if (time === 0) {
      setIsRunning(false); // Stop the timer when it hits 0
    }

    return () => clearInterval(timer); // Cleanup on component unmount or effect change
  }, [isRunning, time]);

  const startTimer = () => setIsRunning(true);
  const stopTimer = () => setIsRunning(false);
  const resetTimer = () => setTime(initialTime);

  return { time, startTimer, stopTimer, resetTimer };
}

export default useTimer;
```

#### **Using `useTimer` in a Component**

```js
import React from 'react';
import useTimer from './useTimer'; // Import custom hook

const TimerComponent = () => {
  const { time, startTimer, stopTimer, resetTimer } = useTimer(60);

  return (
    <div>
      <h1>Time Left: {time}s</h1>
      <button onClick={startTimer}>Start</button>
      <button onClick={stopTimer}>Stop</button>
      <button onClick={resetTimer}>Reset</button>
    </div>
  );
};

export default TimerComponent;
```

#### **Key Points**:
- `useTimer` tracks the time and provides control over starting, stopping, and resetting the timer.
- The hook automatically handles interval cleanup.

---

### **Conclusion**

Creating custom hooks in React is a powerful way to share and encapsulate reusable logic across components. By using React’s built-in hooks like `useState`, `useEffect`, `useRef`, and others, you can abstract common functionality and use it in multiple places in your application. Custom hooks allow you to follow the DRY principle (Don’t Repeat Yourself) and keep your code clean and maintainable.

Some key use cases include:
- **State management** (e.g., `useCounter`, `useReducer`)
- **Data fetching** (e.g., `useFetch`)
- **Local storage management** (e.g., `useLocalStorage`)
- **Responsive behavior** (e.g., `useWindowDimensions`)
- **Timers or intervals** (e.g., `useTimer`)

The more you use custom hooks, the more powerful and reusable your application’s logic will become!