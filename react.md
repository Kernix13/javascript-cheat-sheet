# All things React

### JSX

Introducing JSX: https://reactjs.org/docs/introducing-jsx.html

You can put any valid JavaScript expression inside the curly braces { } in JSX: `{ ternary }`, `{ FxName(param) }`, `{ obj.prop; }`

You may use quotes to specify string literals as attributes:

```jsx
const element = <a href="https://www.reactjs.org"> React </a>;
```

Use curly braces to embed a JavaScript expression in an attribute:

```jsx
const element = <img src={user.avatarUrl}></img>;
```

JSX Prevents Injection Attacks: It is safe to embed user input in JSX:

```jsx
const title = response.potentiallyMaliciousInput;
// This is safe:
const element = <h1>{title}</h1>;
```

## Rendering elements

Link: https://reactjs.org/docs/rendering-elements.html

Elements are the smallest building blocks of React apps. An element describes what you want to see on the screen:

```jsx
const element = <h1>Hire me!</h1>;
```

## Components and props

Link: https://reactjs.org/docs/components-and-props.html

Components let you split the UI into independent, reusable pieces. Conceptually, components are like JavaScript functions. They accept arbitrary inputs (called `props`) and return React elements describing what should appear on the screen.

The simplest way to define a component is to write a JavaScript function (function components):

```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```

You can also use an ES6 class to define a component: (skip)

Elements can also represent user-defined components:

```jsx
const element = <Welcome name="Jim" />;
```

When React sees an element representing a user-defined component, it passes JSX attributes and children to this component as a single object. We call this object `props`

```jsx
<div id="root"></div>;

function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

const element = <Welcome name="Jim" />;
const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(element);
```

Recap of above:

1. We call `root.render()` with the `<Welcome name="Jim" />` element.
1. React calls the Welcome component with `{name: 'Jim'}` as the props.
1. Our Welcome component returns a `<h1>Hello, Jim</h1>` element as the result.
1. React DOM efficiently updates the DOM to match `<h1>Hello, Jim</h1>`.

**Note**: Always start component names with a capital letter. React treats components starting with lowercase letters as DOM tags.

### Extracting Components

Split components into smaller components:

```jsx
function Comment(props) {
  return (
    <div className="Comment">
      <div className="UserInfo">
        <img className="Avatar" src={props.author.avatarUrl} alt={props.author.name} />
        <div className="UserInfo-name">{props.author.name}</div>
      </div>
      <div className="Comment-text">{props.text}</div>
      <div className="Comment-date">{formatDate(props.date)}</div>
    </div>
  );
}
// Better:
function Comment(props) {
  return (
    <div className="Comment">
      <UserInfo user={props.author} />
      <div className="Comment-text">{props.text}</div>
      <div className="Comment-date">{formatDate(props.date)}</div>
    </div>
  );
}
```

It accepts `author` (an object), `text` (a string), and `date` (a date) as props, and describes a comment on a social media website. This component can be tricky to change because of all the nesting, and it is also hard to reuse individual parts of it. Let’s extract a few components from it.

A good rule of thumb is that if a part of your UI is used several times (`Button`, `Panel`, `Avatar`), or is complex enough on its own (`App`, `FeedStory`, `Comment`), it is a good candidate to be extracted to a separate component.

### Props are Read-Only

A component must never modify its own props. **All React components must act like pure functions with respect to their props.**

## State and Lifecycle

Link: https://reactjs.org/docs/state-and-lifecycle.html

## Handling Events

Link: https://reactjs.org/docs/handling-events.html

Handling events with React elements is very similar to handling events on DOM elements. There are some syntax differences:

- React events are named using camelCase, rather than lowercase.
- With JSX you pass a function as the event handler, rather than a string.

```jsx
// this:
<button onclick="activateLasers()">Activate Lasers</button>

// vs this
<button onClick={activateLasers}>Activate Lasers</button>
```

Another difference is that you cannot return false to prevent default behavior in React. You must call preventDefault explicitly:

```jsx
function Form() {
  function handleSubmit(e) {
    e.preventDefault();
    console.log("You clicked submit.");
  }

  return (
    <form onSubmit={handleSubmit}>
      <button type="submit">Submit</button>
    </form>
  );
}
```

When using React, you generally don’t need to call `addEventListener` to add listeners to a DOM element after it is created. Instead, just provide a listener when the element is initially rendered.

## Conditional Rendering

Link: https://reactjs.org/docs/conditional-rendering.html

## React Component

Link: https://reactjs.org/docs/react-component.html
