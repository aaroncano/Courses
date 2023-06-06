# React

React is an open-source JavaScript library for building user interfaces or UI components. It is maintained by Facebook and a community of individual developers and companies.

React uses a syntax extension of JavaScript called JSX that allows you to write HTML directly within JavaScript. This has several benefits. It lets you use the full programmatic power of JavaScript within HTML, and helps to keep your code readable.

Because JSX is a syntactic extension of JavaScript, you can actually write JavaScript directly within JSX. To do this, you simply include the code you want to be treated as JavaScript within curly braces:

```JSX
{ 'this is treated as JavaScript code' }
```

---
## Create a Complex JSX Element
JSX elements can be nested, just like HTML elements can be nested. Here's an example of a nested JSX element:

```JSX
const JSX = 
<div>
  <h1>q</h1>
  <p>q</p>
  <ul>
    <li>a</li>
    <li>a</li>
    <li>a</li>
  </ul>
</div>;
```

One important thing to know about nested JSX is that it must return a single element.

This one parent element would wrap all of the other levels of nested elements.

For instance, several JSX elements written as siblings with no parent wrapper element will not transpile.
```JSX
//invalid JSX
<p>Paragraph One</p>
<p>Paragraph Two</p>
<p>Paragraph Three</p>
```

---
## Add Comments in JSX
JSX is a syntax that gets compiled into valid JavaScript. Sometimes, for readability, you might need to add comments to your code. Like most programming languages, JSX has its own way to do this.
```JSX
const JSX = (
  <div>
    <h1>This is a block of JSX</h1>
    <p>Here's a subtitle</p>
    {/*Hola*/}
  </div>
);
```

---
## Render HTML Elements to the DOM
ReactDOM offers a simple method to render React elements to the DOM which looks like this: `ReactDOM.render(componentToRender, targetNode)`, where the first argument is the React element or component that you want to render, and the second argument is the DOM node that you want to render the component to.

```JSX
const JSX = (
  <div>
    <h1>Hello World</h1>
    <p>Lets render this to the DOM</p>
  </div>
);

const node = document.getElementById('challenge-node');
ReactDOM.render(JSX, node);
```

---
## Define an HTML Class in JSX
In JSX, you can use the word class but you have to use className instead.
```JSX
const JSX = (
  <div className="myDiv">
    <h1>Add a class to this div</h1>
  </div>
);
```
The naming convention for all HTML attributes and event references in JSX become camelCase. For example, a click event in JSX is onClick, instead of onclick.

---
## Self-Closing JSX Tags
Any JSX element can be written with a self-closing tag, and every element must be closed. The line-break tag, for example, must always be written as `<br />` in order to be valid JSX that can be transpiled. A `<div>`, on the other hand, can be written as `<div />` or `<div></div>`. The difference is that in the first syntax version there is no way to include anything in the `<div />`
```JSX
const JSX = (
  <div>
    <h2>Welcome to React!</h2> <br />
    <p>Be sure to close all tags!</p>
    <hr />
  </div>
);
```

---
## Create a Stateless Functional Component
To create a component with a function, you simply write a JavaScript function that returns either JSX or null. One important thing to note is that React requires your function name to begin with a capital letter.

Defining a component in this way creates a stateless functional component.

```JSX
const DemoComponent = function() {
  return (
    <div className='customClass' />
  );
};
```
After being transpiled, the `<div>` will have a CSS class of customClass.

---
## Create a React Component
The other way to define a React component is with the ES6 class syntax.

```JSX
class Kitten extends React.Component {
  constructor(props) {
    super(props);
  }

  render() {
    return (
      <h1>Hi</h1>
    );
  }
}
```

---
## Create a Component with Composition
 To render a component as a child in a React component, you include the component name written as a custom HTML tag in the JSX.

When React encounters a custom HTML tag that references another component (a component name wrapped in < /> like in this example), it renders the markup for that component in the location of the tag.
    
```JSX
const ChildComponent = () => {
  return (
    <div>
      <p>I am the child</p>
    </div>
  );
};

class ParentComponent extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h1>I am the parent</h1>
        <ChildComponent/>
      </div>
    );
  }
};
```

---
## Use React to Render Nested Components
Component composition is one of React's powerful features. When you work with React, it is important to start thinking about your user interface in terms of components like the App example in the last challenge. You break down your UI into its basic building blocks, and those pieces become the components. This helps to separate the code responsible for the UI from the code responsible for handling your application logic. It can greatly simplify the development and maintenance of complex projects.

```JSX
const TypesOfFruit = () => {
  return (
    <div>
      <h2>Fruits:</h2>
      <ul>
        <li>Apples</li>
        <li>Blueberries</li>
        <li>Strawberries</li>
        <li>Bananas</li>
      </ul>
    </div>
  );
};

const Fruits = () => {
  return (
    <div>
    <TypesOfFruit/>
    </div>
  );
};

class TypesOfFood extends React.Component {
  constructor(props) {
    super(props);
  }

  render() {
    return (
      <div>
        <h1>Types of Food:</h1>
        <Fruits/>
      </div>
    );
  }
};
```

---
## Render a Class Component to the DOM
React components are passed into ReactDOM.render() a little differently than JSX elements. For JSX elements, you pass in the name of the element that you want to render. However, for React components, you need to use the same syntax as if you were rendering a nested component, for example `ReactDOM.render(<ComponentToRender />, targetNode)`. You use this syntax for both ES6 class components and functional components.

```JSX
class TypesOfFood extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h1>Types of Food:</h1>
        <Fruits/>
        <Vegetables/>
      </div>
    );
  }
};

ReactDOM.render(<TypesOfFood/>, document.getElementById('challenge-node'));
```

---
## Pass props to a Stateless Functional Component
Say you have an App component which renders a child component called Welcome which is a stateless functional component. You can pass Welcome a user property by writing:
```JSX
<App>
  <Welcome user='Mark' />
</App>
```

Since Welcome is a stateless functional component, it has access to this value like so:
```JSX
const Welcome = (props) => <h1>Hello, {props.user}!</h1>
```

Example
```JSX
const CurrentDate = (props) => {
  return (
    <div>
      <p>The current date is: {props.date}</p>

    </div>
  );
};

class Calendar extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h3>What date is it?</h3>
    
        <CurrentDate date={Date()}/>
      </div>
    );
  }
};
```
Note: For prop values to be evaluated as JavaScript, they must be enclosed in curly brackets, for instance date={Date()}.

---
## Pass an Array as Props
To pass an array to a JSX element, it must be treated as JavaScript and wrapped in curly braces.

The child component then has access to the array property colors. Array methods such as join() can be used when accessing the property.

```JSX
const List = (props) => {

  return <p>{props.tasks.join(', ')}</p>

};

class ToDo extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h1>To Do Lists</h1>
        <h2>Today</h2>

        <List tasks={["walk", "homework", "make dinner"]}/>
        <h2>Tomorrow</h2>
        <List tasks={["study", "watch the godfather", "play btf"]}/>

      </div>
    );
  }
};
```



```
```
```
```
```
```
```
```
```
```
