# MAIN CONCEPTS

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

In React, you can create distinct components that encapsulate behavior you need. Then, you can render only some of them, depending on the state of your application.

Conditional rendering in React works the same way conditions work in JavaScript. Use JavaScript operators like if or the conditional operator to create elements representing the current state, and let React update the UI to match them:

```jsx
function UserGreeting(props) {
  return <h1>Welcome back!</h1>;
}

function GuestGreeting(props) {
  return <h1>Please sign up.</h1>;
}

// Conditional
function Greeting(props) {
  const isLoggedIn = props.isLoggedIn;
  if (isLoggedIn) {
    return <UserGreeting />;
  }
  return <GuestGreeting />;
}

ReactDOM.render(
  // Try changing to isLoggedIn={true}:
  <Greeting isLoggedIn={false} />,
  document.getElementById("root")
);
```

## Lists and Keys

Link: https://reactjs.org/docs/lists-and-keys.html

How you transform lists in JavaScript: Given the code below, we use the `map()` function to take an array of _numbers_ and double their values. We assign the new array returned by `map()` to the variable _doubled_ and log it:

```jsx
const numbers = [1, 2, 3, 4, 5];
const doubled = numbers.map(number => number * 2);
console.log(doubled); // [2, 4, 6, 8, 10]
```

In React, transforming arrays into lists of elements is nearly identical. You can build collections of elements and include them in JSX using curly braces {}. Below, we loop through the numbers array using the JavaScript map() function. We return a <li> element for each item. Finally, we assign the resulting array of elements to listItems:

```jsx
<div id="root"></div>;
const numbers = [1, 2, 3, 4, 5];
const listItems = numbers.map(number => <li>{number}</li>);
ReactDOM.render(<ul>{listItems}</ul>, document.getElementById("root"));
```

Codepen settings for their version

- JavaScript Preprocessor: Babel
- Add External Scripts/Pens: https://unpkg.com/react/umd/react.development.js and https://unpkg.com/react-dom/umd/react-dom.development.js

### Basic List Component

Usually you would render lists inside a component. We can refactor the previous example into a component that accepts an array of numbers and outputs a list of elements.

```jsx
function NumberList(props) {
  const numbers = props.numbers;
  const listItems = numbers.map(number => <li key={number.toString()}>{number}</li>);
  return <ul>{listItems}</ul>;
}

const numbers = [1, 2, 3, 4, 5];
const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(<NumberList numbers={numbers} />);
```

A `key` is a special string attribute you need to include when creating lists of elements.

### Keys

Keys help React identify which items have changed, are added, or are removed. Keys should be given to the elements inside the array to give the elements a stable identity:

```jsx
const numbers = [1, 2, 3, 4, 5];
const listItems = numbers.map(number => <li key={number.toString()}>{number}</li>);
```

The best way to pick a key is to use a string that uniquely identifies a list item among its siblings. Most often you would use IDs from your data as keys:

```js
const todoItems = todos.map(todo => <li key={todo.id}>{todo.text}</li>);
```

When you don’t have stable IDs for rendered items, you may use the item index as a key as a last resort:

```jsx
const todoItems = todos.map((todo, index) => <li key={index}>{todo.text}</li>);
```

We don’t recommend using indexes for keys if the order of items may change. This can negatively impact performance and may cause issues with component state.

### Extracting Components with Keys

Keys only make sense in the context of the surrounding array. For example, if you extract a ListItem component, you should keep the key on the `<ListItem />` elements in the array rather than on the `<li>` element in the `ListItem` itself.

```jsx
function ListItem(props) {
  // There is no need to specify the key here:
  return <li>{props.value}</li>;
}

function NumberList(props) {
  const numbers = props.numbers;
  const listItems = numbers.map(number => (
    // Key should be specified inside the array.
    <ListItem key={number.toString()} value={number} />
  ));
  return <ul>{listItems}</ul>;
}
```

Keys used within arrays should be unique among their siblings. However, they don’t need to be globally unique. We can use the same keys when we produce two different arrays.

## Forms

Link: https://reactjs.org/docs/forms.html

HTML form elements work a bit differently from other DOM elements in React, because form elements naturally keep some internal state.

### Controlled Components

Form elements such as `<input>`, `<textarea>`, and `<select>` typically maintain their own state and update it based on user input. In React, mutable state is typically kept in the state property of components, and only updated with `setState()`.

NOTE: This is another example leading to classes - SKIP!

...the React component that renders a form also controls what happens in that form on subsequent user input. An input form element whose value is controlled by React in this way is called a _controlled component_.

Notes on `input`, `textarea`, `select`, and `input type="file"`.

### Handling Multiple Inputs

When you need to handle multiple controlled `input` elements, you can add a `name` attribute to each element and let the handler function choose what to do based on the value of `event.target.name`.

## Lifting State Up

Link: https://reactjs.org/docs/lifting-state-up.html

Often, several components need to reflect the same changing data. We recommend lifting the shared state up to their closest common ancestor. [READ LATER]

## Composition vs Inheritance

Link: https://reactjs.org/docs/composition-vs-inheritance.html [READ LATER]

## Thinking in React

Link: https://reactjs.org/docs/thinking-in-react.html

- Step 1: Break The UI Into A Component Hierarchy
- Step 2: Build A Static Version in React
- Step 3: Identify The Minimal (but complete) Representation Of UI State
- Step 4: Identify Where Your State Should Live
- Step 5: Add Inverse Data Flow

# ADVANCED GUIDES

## Accessibility

Link: https://reactjs.org/docs/accessibility.html

## Code Splitting

Link: https://reactjs.org/docs/code-splitting.html

## Context

Link: https://reactjs.org/docs/context.html

## Error Boundaries

Link: https://reactjs.org/docs/error-boundaries.html

## Forwarding Refs

Link: https://reactjs.org/docs/forwarding-refs.html

## Fragments

Link: https://reactjs.org/docs/fragments.html

## Higher-Order Components

Link: https://reactjs.org/docs/higher-order-components.html

15 more sections: Integrating with Other Libraries, JSX In Depth (see below), Optimizing Performance, Portals, Profiler API, React Without ES6, React Without JSX, Reconciliation, Refs and the DOM, Render Props (see below), Static Type Checking, Strict Mode, Typechecking With PropTypes (see below), Uncontrolled Components, and Web Components.

## JSX In Depth

Link: https://reactjs.org/docs/jsx-in-depth.html

`React.createElement(component, props, ...children)`

```JSX
// This:
<MyButton color="blue" shadowSize={2}>
  Click Me
</MyButton>
// Compiles into:
React.createElement(
  MyButton,
  {color: 'blue', shadowSize: 2},
  'Click Me'
)

// And this:
<div className="sidebar" />
// Compiles into:
React.createElement(
  'div',
  {className: 'sidebar'}
)
```

### Specifying The React Element Type

The first part of a JSX tag determines the type of the React element. Capitalized types indicate that the JSX tag is referring to a React component.

Since JSX compiles into calls to `React.createElement`, the **React** library must also always be in scope from your JSX code. For example, both of the imports are necessary in this code, even though `React` and `CustomButton` are not directly referenced from JavaScript:

```jsx
import React from "react";
import CustomButton from "./CustomButton";

function WarningButton() {
  // return React.createElement(CustomButton, {color: 'red'}, null);
  return <CustomButton color="red" />;
}
```

If you don’t use a JavaScript bundler and loaded React from a `<script>` tag, it is already in scope as the React global.

- Using Dot Notation for JSX Type: if you have a single module that exports many React components

### User-Defined Components Must Be Capitalized

When an element type starts with a lowercase letter, it refers to a built-in component like `<div>` or `<span>` and results in a string 'div' or 'span' passed to React.createElement. Types that start with a capital letter like `<Foo />` compile to `React.createElement(Foo)` and correspond to a component defined or imported in your JavaScript file.

You cannot use a general expression as the React element type. If you do want to use a general expression to indicate the type of the element, just assign it to a capitalized variable first. This often comes up when you want to render a different component based on a prop:

```jsx
import React from "react";
import { PhotoStory, VideoStory } from "./stories";

const components = {
  photo: PhotoStory,
  video: VideoStory
};

function Story(props) {
  const SpecificStory = components[props.storyType];
  return <SpecificStory story={props.story} />;
}
```

### Props in JSX

There are several different ways to specify props in JSX.

#### JavaScript Expressions as Props

You can pass any JavaScript expression as a prop, by surrounding it with {}. For example, in this JSX: `<MyComponent foo={1 + 2 + 3 + 4} />`

`if` statements and `for` loops are not expressions in JavaScript, so they can’t be used in JSX directly.

**String Literals**: You can pass a string literal as a prop

### Spread Attributes

stopped here https://reactjs.org/docs/jsx-in-depth.html#spread-attributes

## Render Props

Link: https://reactjs.org/docs/render-props.html

## Typechecking With PropTypes

Link: https://reactjs.org/docs/typechecking-with-proptypes.html

# API REFERENCE

Link: https://reactjs.org/docs/react-api.html

## React Component

Link: https://reactjs.org/docs/react-component.html

# HOOKS

Link:

# TESTING

Link:
