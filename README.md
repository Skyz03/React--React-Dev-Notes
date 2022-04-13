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

1. 	Props are read-only. 	State changes can be asynchronous.
2. 	Props are immutable. 	State is mutable.
3. 	Props allow you to pass data from one component to other components as an argument. 	State holds information about the components.
4. 	Props can be accessed by the child component. 	State cannot be accessed by child components.
5. 	Props are used to communicate between components. 	States can be used for rendering dynamic changes with the component.
6. 	Stateless component can have Props. 	Stateless components cannot have State.
7. 	Props make components reusable. 	State cannot make components reusable.
8. 	Props are external and controlled by whatever renders the component. 	The State is internal and controlled by the React Component itself.

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
 
  

