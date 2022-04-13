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
