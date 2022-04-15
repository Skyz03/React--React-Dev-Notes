# React--React-Dev-Notes

Once into a React Developer, What are the necessary things you need to know to be a React Developer.<br>
Steps and Researched from this [link](https://roadmap.sh/react)

## JSX:

- React doesn’t require using JSX, but most people find it helpful as a visual aid when working with UI inside the JavaScript code.
- AS a matter of fact it can be used inside expression too.
- Attrinute specifying = quote => string , Curly braces for JS expression.
- JS tag can contain children.
- It represent objects.

## Rendering Elements:

- Applications built with just React usually have a single root DOM node. If you are integrating React into an existing app, you may have as many isolated root DOM nodes as you like.
- React elements are immutable.
- Once you create an element, you can’t change its children or attributes. An element is like a single frame in a movie: it represents the UI at a certain point in time.
- It Only Updates when necessary.
- Even though we create an element describing the whole UI tree on every tick, only the text node whose contents have changed gets updated by React DOM.

## Components & Props

- Components let you split the UI into independent, reusable pieces, and think about each piece in isolation.
- When React sees an element representing a user-defined component, it passes JSX attributes and children to this component as a single object. We call this object “props”.
- Components can be rendered multiple times.
- Components can be extracted and used in multiple places.
- Props are read-only
- Pure function doesnt change their inputs and return the same output like the sum function.

```
function sum(a, b) {
  return a + b;
}
```

- Impure is it changes its own input.

```
function withdraw(account, amount) {
  account.total -= amount;
}
```

- All React components must act like pure functions with respect to their props.
- Props VS State => the true/false condition we pass like starting game or dice one.

1.                                    Props are read-only. 	State changes can be asynchronous.
2.                                    Props are immutable. 	State is mutable.
3.                                    Props allow you to pass data from one component to other components as an argument. 	State holds information about the components.
4.                                    Props can be accessed by the child component. 	State cannot be accessed by child components.
5.                                    Props are used to communicate between components. 	States can be used for rendering dynamic changes with the component.
6.                                    Stateless component can have Props. 	Stateless components cannot have State.
7.                                    Props make components reusable. 	State cannot make components reusable.
8.                                    Props are external and controlled by whatever renders the component. 	The State is internal and controlled by the React Component itself.

## Conditional Rendering

In React, you can create distinct components that encapsulate behavior you need. Then, you can render only some of them, depending on the state of your application.

```
function Greeting(props) {
  const isLoggedIn = props.isLoggedIn;
  if (isLoggedIn) {    return <UserGreeting />;  }  return <GuestGreeting />;}
ReactDOM.render(
  // Try changing to isLoggedIn={true}:
  <Greeting isLoggedIn={false} />,  document.getElementById('root'));
```

** It works because in JavaScript, true && expression always evaluates to expression, and false && expression always evaluates to false.**<br>
Or use the Ternary operators.<br>
In rare cases you might want a component to hide itself even though it was rendered by another component. To do this return null instead of its render output.

## Lists & Keys:

```
const numbers = [1, 2, 3, 4, 5];
const doubled = numbers.map((number) => number * 2);console.log(doubled);
```

Rendering Multiple Items:

You can build collections of elements and include them in JSX using curly braces {}.

Below, we loop through the numbers array using the JavaScript map() function. We return a <li> element for each item. Finally, we assign the resulting array of elements to listItems:

```
const numbers = [1, 2, 3, 4, 5];
const listItems = numbers.map((number) =>  <li>{number}</li>);

Then, we can include the entire listItems array inside a <ul> element:

<ul>{listItems}</ul>
```

Keys help React identify which items have changed, are added, or are removed. Keys should be given to the elements inside the array to give the elements a stable identity: <br>

We don’t recommend using indexes for keys if the order of items may change. This can negatively impact performance and may cause issues with component state. Check out Robin Pokorny’s article for an in-depth explanation on the negative impacts of using an index as a key. If you choose not to assign an explicit key to list items then React will default to using indexes as keys.

![image](https://user-images.githubusercontent.com/42742924/163166703-90044b8e-97c5-499d-aef4-cc885dcb2f1c.png)

![image](https://user-images.githubusercontent.com/42742924/163166723-ddb30ffb-24e3-46a0-b081-6cb9fbf446a4.png)

Key doesn't get passed into the props if we want used another name.

## Context:

Context provides a way to pass data through the component tree without having to pass props down manually at every level.
Context provides a way to share values like these between components without having to explicitly pass a prop through every level of the tree.

When to use it?

1. Light & dark theme
2. User data for authentication.
3. Location specific data like language or locale

You can think of React context as the equivalent of global variables for our React components.

What Problem Does it Solve?

- Props Drilling:

```
export default function App({ theme }) {
  return (
    <>
      <Header theme={theme} />
      <Main theme={theme} />
      <Sidebar theme={theme} />
      <Footer theme={theme} />
    </>
  );
}

function Header({ theme }) {
  return (
    <>
      <User theme={theme} />
      <Login theme={theme} />
      <Menu theme={theme} />
    </>
  );
}
```

The issue is that we are drilling the theme prop through multiple components that don't immediately need it.

The Header component doesn't need theme other than to pass it down to its child component. In other words, it would be better for User , Login and Menu to consume the theme data directly.

This is the benefit of React context – we can bypass using props entirely and therefore avoid the issue of props drilling.

The 4 easy steps to use context:
There are four steps to using React context:

- Create context using the createContext method.
- Take your created context and wrap the context provider around your component tree.
- Put any value you like on your context provider using the value prop.
- Read that value within any component by using the context consumer.

## Ref or useRef Hooks:

The useRef Hook allows you to persist values between renders.<br>
It can be used to store a mutable value that does not cause a re-render when updated.<br>
It can be used to access a DOM element directly.<br>

If we tried to count how many times our application renders using the useState Hook, we would be caught in an infinite loop since this Hook itself causes a re-render.<br>

To avoid this, we can use the useRef Hook. It can be used in the the counter of the application.

It has three uses:

[W3](https://www.w3schools.com/react/react_useref.asp)

- Use useRef to track application renders.
- useRef() only returns one item. It returns an Object called current.
- Accessing DOM Elements
- Tracking State Changes

## Render Props

It refers to a technique for sharing code between React Components using a prop whose value is a function.
MOre information on this article useful: [Medium](https://medium.com/geekculture/render-props-in-reactjs-d672e3106bc1).

And need to follow couple of youtube videos.

## Higher Order Components:

A higher order function is a function that takes a function as an argument, or returns a function. Higher order function is in contrast to first order functions, which don’t take a function as an argument or return a function as output.

A higher-order component (HOC) is an advanced technique in React for reusing component logic. HOCs are not part of the React API, per se. They are a pattern that emerges from React’s compositional nature.

Higher-order components (HOCs) in React were inspired by higher-order functions in JavaScript. A HOC is an advanced technique for reusing logic in React components. It is a pattern created out of React’s compositional nature.

HOCs basically incorporate the don’t-repeat-yourself (DRY) principle of programming, which you’ve most likely come across at some point in your career as a software developer. It is one of the best-known principles of software development, and observing it is very important when building an application or writing code in general.
[Samshing](https://www.smashingmagazine.com/2020/06/higher-order-components-react/)
[Medium](https://medium.com/javascript-scene/higher-order-functions-composing-software-5365cf2cbe99)

## Portals:

Portals provide a first-class way to render children into a DOM node that exists outside the DOM hierarchy of the parent component.
For instance, like their is a root id and their is a portal id.
It keeps the event and other delegation of the parent eleement but reder it outside of the root element.
[Youtube in 12mins](https://www.youtube.com/watch?v=LyLa7dU5tp8)

What the their use cases:

- Modal dialog boxes.
- ToolTips
- HoverCards
- Loaders

[More on this article](https://blog.bitsrc.io/understanding-react-portals-ab79827732c7)

## Error Boundries:

It is a class component.

[Article](https://www.digitalocean.com/community/tutorials/react-error-boundaries)
[NPM](https://www.npmjs.com/package/react-error-boundary)

Error Boundaries were introduced in React v16 as a way to catch tricky errors that occur during the render phase. In the past, this would have caused the app to unmount completely, and the user would just see a blank web page, which is not ideal!

Error Boundaries actually aren’t in direct competition with try...catch statements. Error Boundaries are only designed for intercepting errors that originate from 3 places in a React component:

    During render phase
    In a lifecycle method
    In the constructor

Basically… the React-y parts of a component.

As a counterpoint, these are the places where Error Boundaries will not be able to catch an error:

    Event handlers (e.g., onClick, onChange, etc.)
    setTimeout or requestAnimationFramecallbacks
    Server-side rendering (SSR)
    And errors caused by the error boundary itself (rather than its children)

So Error Boundaries don’t really impact how you use try...catch. They’re both needed as a robust strategy for handling errors in React.

## Fiber Artitechture:

Its like the algorithm behind the react code.

[Best article](https://dev.to/burhanuday/react-internals-fiber-architecture-280l)

[Simple](https://www.youtube.com/watch?v=gsvHmZ3hXjo)

[Lin](https://www.youtube.com/watch?v=ZCuYPiUIONs)

[Devz](https://dzone.com/articles/understanding-of-react-fiber-architecture)

## React Hooks:

Hooks allow us to "hook" into React features such as state and lifecycle methods. So, that we don't have to use them anymore.

You must import Hooks from react.

There are 3 rules of Hooks:

- Hooks can only be called inside React function components.
- Hooks can only be called at the top level of a component.
- Hooks cannot be conditional

There are different hooks for different purposes:

1. useState.
2. useEffect.
3. useCallback.
4. useRef.
5. useMemo.
6. useReducer.
7. useContext.

### useState:

The React useState Hook allows us to track state in a function component.
State generally refers to data or properties that need to be tracking in an application.

Initialize useState

```
import { useState } from "react";

function FavoriteColor() {
  const [color, setColor] = useState("");
}
```

Read State: 

```
import { useState } from "react";
import ReactDOM from "react-dom";

function FavoriteColor() {
  const [color, setColor] = useState("red");

  return <h1>My favorite color is {color}!</h1>
}

The color component is being read.

ReactDOM.render(<FavoriteColor />, document.getElementById('root'));
```

Update State: 

To Update our state, we use our state updater function.

Never directly update the state. 

For instance, 
```
import { useState } from "react";
import ReactDOM from "react-dom";

function FavoriteColor() {
  const [color, setColor] = useState("red");

  return (
    <>
      <h1>My favorite color is {color}!</h1>
      <button
        type="button"
        onClick={() => setColor("blue")}
      >Blue</button>
    </>
  )
}

ReactDOM.render(<FavoriteColor />, document.getElementById('root'));
```

The possibilities of the useState: 

The useState Hook can be used to keep track of strings, numbers, booleans, arrays, objects, and any combination of these!

1. Creating multiple state: 

```
import { useState } from "react";
import ReactDOM from "react-dom";

function Car() {
  const [brand, setBrand] = useState("Ford");
  const [model, setModel] = useState("Mustang");
  const [year, setYear] = useState("1964");
  const [color, setColor] = useState("red");

  return (
    <>
      <h1>My {brand}</h1>
      <p>
        It is a {color} {model} from {year}.
      </p>
    </>
  )
}

ReactDOM.render(<Car />, document.getElementById('root'));
```

2. Use of Object that holds the object.

```
import { useState } from "react";
import ReactDOM from "react-dom";

function Car() {
  const [car, setCar] = useState({
    brand: "Ford",
    model: "Mustang",
    year: "1964",
    color: "red"
  });

  return (
    <>
      <h1>My {car.brand}</h1>
      <p>
        It is a {car.color} {car.model} from {car.year}.
      </p>
    </>
  )
}

ReactDOM.render(<Car />, document.getElementById('root'));
```

While updating our state when we just call the respective color to state it it gets overwritten and remove the previous data. 
This is where the spread operator comes in handy as shown in the example below. 

```
import { useState } from "react";
import ReactDOM from "react-dom";

function Car() {
  const [car, setCar] = useState({
    brand: "Ford",
    model: "Mustang",
    year: "1964",
    color: "red"
  });

  const updateColor = () => {
    setCar(previousState => {
      return { ...previousState, color: "blue" }
    });
  }

  return (
    <>
      <h1>My {car.brand}</h1>
      <p>
        It is a {car.color} {car.model} from {car.year}.
      </p>
      <button
        type="button"
        onClick={updateColor}
      >Blue</button>
    </>
  )
}

ReactDOM.render(<Car />, document.getElementById('root'));
```
We then return an object, spreading the previousState and overwriting only the color.


### useEffect Hook: 

The useEffect Hook allows you to perform side effects in your components.

Some examples of side effects are: fetching data, directly updating the DOM, and timers.

useEffect accepts two arguments. The second argument is optional.

useEffect(<function>, <dependency>)

First example: Where it renders every time like a clock. 

```
import { useState, useEffect } from "react";
import ReactDOM from "react-dom";

function Timer() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    setTimeout(() => {
      setCount((count) => count + 1);
    }, 1000);
  });

  return <h1>I've rendered {count} times!</h1>;
}

ReactDOM.render(<Timer />, document.getElementById('root'));
```

Here, it runs on every render, when the count changes the render hsppens which then triggers another effect. 

For sometime this is good but for some time except the clock this is not good and we only need to run it once, as a matter of fact the second array parameter is optional. 


1. No dependency passed:

useEffect(() => {
  //Runs on every render
});

2. An empty array:

useEffect(() => {
  //Runs only on the first render
}, []);

3. Props or state values:

useEffect(() => {
  //Runs on the first render
  //And any time any dependency value changes
}, [prop, state]);

So, to avoid the running of the render everytime. 
add and empty bracket. 

```
import { useState, useEffect } from "react";
import ReactDOM from "react-dom";

function Timer() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    setTimeout(() => {
      setCount((count) => count + 1);
    }, 1000);
  }, []); // <- add empty brackets here

  return <h1>I've rendered {count} times!</h1>;
}

ReactDOM.render(<Timer />, document.getElementById('root'));
```

If there are multiple dependencies, they should be included in the useEffect dependency array.

Cleaning up the effect: 

Some effects require cleanup to reduce memory leaks.

Timeouts, subscriptions, event listeners, and other effects that are no longer needed should be disposed.

We do this by including a return function at the end of the useEffect Hook.

```
useEffect(() => {
    let timer = setTimeout(() => {
    setCount((count) => count + 1);
  }, 1000);

  return () => clearTimeout(timer)
  }, []);
```

### useContext Hook:

This is a way to manage state globally. 

It can be used together with the useState Hook to share state between deeply nested components more easily than with useState alone.

The problem it solves: 

State should be held by the highest parent component in the stack that requires access to the state.

To illustrate, we have many nested components. The component at the top and bottom of the stack need access to the state.

To do this without Context, we will need to pass the state as "props" through each nested component. This is called "prop drilling".


```
import { useState } from "react";
import ReactDOM from "react-dom";

function Component1() {
  const [user, setUser] = useState("Jesse Hall");

  return (
    <>
      <h1>{`Hello ${user}!`}</h1>
      <Component2 user={user} />
    </>
  );
}

function Component2({ user }) {
  return (
    <>
      <h1>Component 2</h1>
      <Component3 user={user} />
    </>
  );
}

function Component3({ user }) {
  return (
    <>
      <h1>Component 3</h1>
      <Component4 user={user} />
    </>
  );
}

function Component4({ user }) {
  return (
    <>
      <h1>Component 4</h1>
      <Component5 user={user} />
    </>
  );
}

function Component5({ user }) {
  return (
    <>
      <h1>Component 5</h1>
      <h2>{`Hello ${user} again!`}</h2>
    </>
  );
}

ReactDOM.render(<Component1 />, document.getElementById("root"));
```

Even though components 2-4 did not need the state, they had to pass the state along so that it could reach component 5.

Solution: 

1. Create Context:

```
import { useState, createContext } from "react";
import ReactDOM from "react-dom";

const UserContext = createContext()
```


2. Context Provider

Wrap child components in the Context Provider and supply the state value.
```
function Component1() {
  const [user, setUser] = useState("Jesse Hall");

  return (
    <UserContext.Provider value={user}>
      <h1>{`Hello ${user}!`}</h1>
      <Component2 user={user} />
    </UserContext.Provider>
  );
}
```

In order use it: 

```
function Component5() {
  const user = useContext(UserContext);

  return (
    <>
      <h1>Component 5</h1>
      <h2>{`Hello ${user} again!`}</h2>
    </>
  );
}
```


Full senario: 

```
import { useState, createContext, useContext } from "react";
import ReactDOM from "react-dom";

const UserContext = createContext();

function Component1() {
  const [user, setUser] = useState("Jesse Hall");

  return (
    <UserContext.Provider value={user}>
      <h1>{`Hello ${user}!`}</h1>
      <Component2 user={user} />
    </UserContext.Provider>
  );
}

function Component2() {
  return (
    <>
      <h1>Component 2</h1>
      <Component3 />
    </>
  );
}

function Component3() {
  return (
    <>
      <h1>Component 3</h1>
      <Component4 />
    </>
  );
}

function Component4() {
  return (
    <>
      <h1>Component 4</h1>
      <Component5 />
    </>
  );
}

function Component5() {
  const user = useContext(UserContext);

  return (
    <>
      <h1>Component 5</h1>
      <h2>{`Hello ${user} again!`}</h2>
    </>
  );
}

ReactDOM.render(<Component1 />, document.getElementById("root"));
```

### The useRef Hook: 

The useRef Hook allows you to persist values between renders.

It can be used to store a mutable value that does not cause a re-render when updated.

It can be used to access a DOM element directly.

Preventing from Re-renders: 

If we tried to count how many times our application renders using the useState Hook, we would be caught in an infinite loop since this Hook itself causes a re-render.

To avoid this, we can use the useRef Hook.

```
import { useState, useEffect, useRef } from "react";
import ReactDOM from "react-dom";

function App() {
  const [inputValue, setInputValue] = useState("");
  const count = useRef(0);

  useEffect(() => {
    count.current = count.current + 1;
  });

  return (
    <>
      <input
        type="text"
        value={inputValue}
        onChange={(e) => setInputValue(e.target.value)}
      />
      <h1>Render Count: {count.current}</h1>
    </>
  );
}

ReactDOM.render(<App />, document.getElementById('root'));
```

useRef() only returns one item. It returns an Object called current.

When we initialize useRef we set the initial value: useRef(0).

#### Acessing DOM Elements with Ref: 

Most of the DOM is handled is by React.

Sometimes to access we add ref attribute to an element to access it directly in the DOM.

```
import { useRef } from "react";
import ReactDOM from "react-dom";

function App() {
  const inputElement = useRef();

  const focusInput = () => {
    inputElement.current.focus();
  };

  return (
    <>
      <input type="text" ref={inputElement} />
      <button onClick={focusInput}>Focus Input</button>
    </>
  );
}

ReactDOM.render(<App />, document.getElementById('root'));
```

It can also be used to track the state changes: 

The useRef Hook can also be used to keep track of previous state values.

```
import { useState, useEffect, useRef } from "react";
import ReactDOM from "react-dom";

function App() {
  const [inputValue, setInputValue] = useState("");
  const previousInputValue = useRef("");

  useEffect(() => {
    previousInputValue.current = inputValue;
  }, [inputValue]);

  return (
    <>
      <input
        type="text"
        value={inputValue}
        onChange={(e) => setInputValue(e.target.value)}
      />
      <h2>Current Value: {inputValue}</h2>
      <h2>Previous Value: {previousInputValue.current}</h2>
    </>
  );
}

ReactDOM.render(<App />, document.getElementById('root'));
```
This time we use a combination of useState, useEffect, and useRef to keep track of the previous state.

In the useEffect, we are updating the useRef current value each time the inputValue is updated by entering text into the input field.

### userReducer Hook: 
This is the similar hook as useState Hook. 

It allows for custom state logic.

If you find yourself keeping track of multiple pieces of state that rely on complex logic, useReducer may be useful.

The useReducer Hook accepts two arguments.

useReducer(<reducer>, <initialState>)


The reducer function contains your custom state logic and the initialStatecan be a simple value but generally will contain an object.

The useReducer Hook returns the current stateand a dispatchmethod.

Here is an example of useReducer in a counter app:
Example:
```
import { useReducer } from "react";
import ReactDOM from "react-dom";

const initialTodos = [
  {
    id: 1,
    title: "Todo 1",
    complete: false,
  },
  {
    id: 2,
    title: "Todo 2",
    complete: false,
  },
];

const reducer = (state, action) => {
  switch (action.type) {
    case "COMPLETE":
      return state.map((todo) => {
        if (todo.id === action.id) {
          return { ...todo, complete: !todo.complete };
        } else {
          return todo;
        }
      });
    default:
      return state;
  }
};

function Todos() {
  const [todos, dispatch] = useReducer(reducer, initialTodos);

  const handleComplete = (todo) => {
    dispatch({ type: "COMPLETE", id: todo.id });
  };

  return (
    <>
      {todos.map((todo) => (
        <div key={todo.id}>
          <label>
            <input
              type="checkbox"
              checked={todo.complete}
              onChange={() => handleComplete(todo)}
            />
            {todo.title}
          </label>
        </div>
      ))}
    </>
  );
}

ReactDOM.render(<Todos />, document.getElementById('root'));
```
This is just the logic to keep track of the todo complete status.

All of the logic to add, delete, and complete a todo could be contained within a single useReducer Hook by adding more actions.

### useCallback Hook: 

The React useCallback Hook returns a memoized callback function.

Think of memoization as caching a value so that it does not need to be recalculated.

This allows us to isolate resource intensive functions so that they will not automatically run on every render.

The useCallback Hook only runs when one of its dependencies update.

This can improve performance.

Problem:

One reason to use useCallback is to prevent a component from re-rendering unless its props have changed.

In this example, you might think that the Todos component will not re-render unless the todos change:

```
index.js

import { useState } from "react";
import ReactDOM from "react-dom";
import Todos from "./Todos";

const App = () => {
  const [count, setCount] = useState(0);
  const [todos, setTodos] = useState([]);

  const increment = () => {
    setCount((c) => c + 1);
  };
  const addTodo = () => {
    setTodos((t) => [...t, "New Todo"]);
  };

  return (
    <>
      <Todos todos={todos} addTodo={addTodo} />
      <hr />
      <div>
        Count: {count}
        <button onClick={increment}>+</button>
      </div>
    </>
  );
};

ReactDOM.render(<App />, document.getElementById('root'));

Todos.js

import { memo } from "react";

const Todos = ({ todos, addTodo }) => {
  console.log("child render");
  return (
    <>
      <h2>My Todos</h2>
      {todos.map((todo, index) => {
        return <p key={index}>{todo}</p>;
      })}
      <button onClick={addTodo}>Add Todo</button>
    </>
  );
};

export default memo(Todos);
```

Try running this and click the count increment button.

You will notice that the Todos component re-renders even when the todos do not change.

Why does this not work? We are using memo, so the Todos component should not re-render since neither the todos state nor the addTodo function are changing when the count is incremented.

This is because of something called "referential equality".

Every time a component re-renders, its functions get recreated. Because of this, the addTodo function has actually changed.


To fix this, we can use the useCallback hook

```
Replace addtodo with this
const addTodo = useCallback(() => {
    setTodos((t) => [...t, "New Todo"]);
  }, [todos]);
```

### useMemo Hook:

The React useMemo Hook returns a memoized value.

Think of memoization as caching a value so that it does not need to be recalculated.

The useMemo Hook only runs when one of its dependencies update.

This can improve performance.
Use useMemo

To fix this performance issue, we can use the useMemo Hook to memoize the expensiveCalculation function. This will cause the function to only run when needed.

We can wrap the expensive function call with useMemo.

The useMemoHook accepts a second parameter to declare dependencies. The expensive function will only run when its dependencies have changed.

In the following example, the expensive function will only run when count is changed and not when todo's are added.
Example:

Performance example using the useMemo Hook:
```
import { useState, useMemo } from "react";
import ReactDOM from "react-dom";

const App = () => {
  const [count, setCount] = useState(0);
  const [todos, setTodos] = useState([]);
  const calculation = useMemo(() => expensiveCalculation(count), [count]);

  const increment = () => {
    setCount((c) => c + 1);
  };
  const addTodo = () => {
    setTodos((t) => [...t, "New Todo"]);
  };

  return (
    <div>
      <div>
        <h2>My Todos</h2>
        {todos.map((todo, index) => {
          return <p key={index}>{todo}</p>;
        })}
        <button onClick={addTodo}>Add Todo</button>
      </div>
      <hr />
      <div>
        Count: {count}
        <button onClick={increment}>+</button>
        <h2>Expensive Calculation</h2>
        {calculation}
      </div>
    </div>
  );
};

const expensiveCalculation = (num) => {
  console.log("Calculating...");
  for (let i = 0; i < 1000000000; i++) {
    num += 1;
  }
  return num;
};

ReactDOM.render(<App />, document.getElementById('root'));
```
