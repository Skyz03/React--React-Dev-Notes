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

1.                         Props are read-only. 	State changes can be asynchronous.
2.                         Props are immutable. 	State is mutable.
3.                         Props allow you to pass data from one component to other components as an argument. 	State holds information about the components.
4.                         Props can be accessed by the child component. 	State cannot be accessed by child components.
5.                         Props are used to communicate between components. 	States can be used for rendering dynamic changes with the component.
6.                         Stateless component can have Props. 	Stateless components cannot have State.
7.                         Props make components reusable. 	State cannot make components reusable.
8.                         Props are external and controlled by whatever renders the component. 	The State is internal and controlled by the React Component itself.

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


