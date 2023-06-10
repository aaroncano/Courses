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
---
## Use Default Props
You can assign default props to a component as a property on the component itself and React assigns the default prop if necessary. This allows you to specify what a prop value should be if no value is explicitly provided.

```JSX
const ShoppingCart = (props) => {
  return (
    <div>
      <h1>Shopping Cart Component</h1>
    </div>
  )
};
ShoppingCart.defaultProps = { items: 0}
```

---
## Override Default Props
The way to override the default props is to explicitly set the prop values for a component.

```JSX
const Items = (props) => {
  return <h1>Current Quantity of Items in Cart: {props.quantity}</h1>
}

Items.defaultProps = {
  quantity: 0
}

class ShoppingCart extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {

    return <Items quantity={10}/>
  }
};
```

---
## Use PropTypes to Define the Props You Expect
It's considered a best practice to set propTypes when you know the type of a prop ahead of time. You can define a propTypes property for a component in the same way you defined defaultProps. Doing this will check that props of a given key are present with a given type.
  
```JSX
const Items = (props) => {
  return <h1>Current Quantity of Items in Cart: {props.quantity}</h1>
};

Items.propTypes = { quantity: PropTypes.number.isRequired}

Items.defaultProps = {
  quantity: 0
};

class ShoppingCart extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return <Items />
  }
};
```

---
## Access Props Using this.props
The ES6 class component uses a slightly different convention to access props.

Anytime you refer to a class component within itself, you use the this keyword. To access props within a class component, you preface the code that you use to access it with this. For example, if an ES6 class component has a prop called data, you write {this.props.data} in JSX.
  
```JSX
class App extends React.Component {
  constructor(props) {
    super(props);

  }
  render() {
    return (
        <div>

            <Welcome name='Elisa'/>

        </div>
    );
  }
};

class Welcome extends React.Component {
  constructor(props) {
    super(props);

  }
  render() {
    return (
        <div>

          <p>Hello, <strong>{this.props.name}</strong>!</p>

        </div>
    );
  }
};
```

---
## Review Using Props with Stateless Functional Components
A stateless functional component is any function you write which accepts props and returns JSX.

A stateless component, on the other hand, is a class that extends React.Component, but does not use internal state. 

A stateful component is a class component that does maintain its own internal state. You may see stateful components referred to simply as components or React components.

---
## Create a Stateful Component
State consists of any data your application needs to know about, that can change over time. You want your apps to respond to state changes and present an updated UI when necessary. React offers a nice solution for the state management of modern web applications.

You create state in a React component by declaring a state property on the component class in its constructor. This initializes the component with state when it is created. The state property must be set to a JavaScript object.
  
```JSX
class StatefulComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      firstName: 'aaron'
    }
  }
  render() {
    return (
      <div>
        <h1>{this.state.firstName}</h1>
      </div>
    );
  }
};
```
You have access to the state object throughout the life of your component. You can update it, render it in your UI, and pass it as props to child components.

---
## Render State in the User Interface
f a component is stateful, it will always have access to the data in state in its render() method. You can access the data with this.state.

If you want to access a state value within the return of the render method, you have to enclose the value in curly braces.

React updates the actual DOM, but only where necessary. This means you don't have to worry about changing the DOM.

State is completely encapsulated, or local to that component, unless you pass state data to a child component as props.

---
## Render State in the User Interface Another Way
In the render() method, before the return statement, you can write JavaScript directly. For example, you could declare functions, access data from state or props, perform computations on this data, and so on. Then, you can assign any data to variables, which you have access to in the return statement.
  
```JSX
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: 'freeCodeCamp'
    }
  }
  render() {
    const name = this.state.name;
    return (
      <div>
        <h1>{name}</h1>
      </div>
    );
  }
};
```

---
## Set State with this.setState
React provides a method for updating component state called setState. You call the setState method within your component class like so: this.setState(), passing in an object with key-value pairs. The keys are your state properties and the values are the updated state data.

```JSX
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: 'Initial State'
    };
    this.handleClick = this.handleClick.bind(this);
  }
  handleClick() {
    this.setState({name :'React Rocks!'});
  }
  render() {
    return (
      <div>
        <button onClick={this.handleClick}>Click Me</button>
        <h1>{this.state.name}</h1>
      </div>
    );
  }
};
```

---
## Bind 'this' to a Class Method
A class method typically needs to use the this keyword so it can access properties on the class (such as state and props) inside the scope of the method.

One common way is to explicitly bind this in the constructor so this becomes bound to the class methods when the component is initialized. Then, when you call a function like this.setState() within your class method, this refers to the class and will not be undefined.

```JSX
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      text: "Hello"
    };
    this.handleClick = this.handleClick.bind(this);
  }
  handleClick() {
    this.setState({
      text: "You clicked!"
    });
  }
  render() {
    return (
      <div>
        <button onClick={this.handleClick}>Click Me</button>
        <h1>{this.state.text}</h1>
      </div>
    );
  }
};
```

---
## Use State to Toggle an Element
Instead, you should pass setState a function that allows you to access state and props. Using a function with setState guarantees you are working with the most current values of state and props. 

```JSX
this.setState((state, props) => ({
  counter: state.counter + props.increment
}));

//You can also use a form without props if you need only the state
this.setState(state => ({
  counter: state.counter + 1
}));

class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      visibility: false
    };
    this.toggleVisibility =  this.toggleVisibility.bind(this);
  }
  toggleVisibility(){
    this.setState(state => ({
      visibility: !state.visibility
    }));
  }
  render() {
    if (this.state.visibility) {
      return (
        <div>
          <button onClick={this.toggleVisibility}>Click Me</button>
          <h1>Now you see me!</h1>
        </div>
      );
    } else {
      return (
        <div>
          <button onClick={this.toggleVisibility}>Click Me</button>
        </div>
      );
    }
  }
}
```

---
## Simple Counter
```JSX
class Counter extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0
    };
    this.increment = this.increment.bind(this);
    this.decrement = this.decrement.bind(this);
    this.reset = this.reset.bind(this);
  }
  increment(){
    this.setState(state => ({
      count: state.count + 1
    }));
  }
  decrement(){
    this.setState(state => ({
      count: state.count - 1
    }));
  }
  reset(){
    this.setState(state =>({
      count: 0
    }));
  }

  render() {
    return (
      <div>
        <button className='inc' onClick={this.increment}>Increment!</button>
        <button className='dec' onClick={this.decrement}>Decrement!</button>
        <button className='reset' onClick={this.reset}>Reset</button>
        <h1>Current Count: {this.state.count}</h1>
      </div>
    );
  }
};
```

---
## Controlled Input
```JSX
class ControlledInput extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      input: ''
    };
    this.handleChange = this.handleChange.bind(this);
  }
  handleChange(event){
    this.setState(state => ({
      input: event.target.value
    }));
  }
  render() {
    return (
      <div>
        <input value={this.state.input} onChange={this.handleChange}></input>
        <h4>Controlled Input:</h4>
        <p>{this.state.input}</p>
      </div>
    );
  }
};
```

---
## Controlled Form
```JSX
class MyForm extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      input: '',
      submit: ''
    };
    this.handleChange = this.handleChange.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
  }
  handleChange(event) {
    this.setState({
      input: event.target.value
    });
  }
  handleSubmit(event) {
    event.preventDefault();
    this.setState(state => ({
      submit: state.input
    }));
  }
  render() {
    return (
      <div>
        <form onSubmit={this.handleSubmit}>
          <input value={this.state.input} onChange={this.handleChange}></input>
          <button type='submit'>Submit!</button>
        </form>
        <h1>{this.state.submit}</h1>
      </div>
    );
  }
}
```

---
## Pass State as Props to Child Components
You can pass state as props to child components.
```JSX
class MyApp extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: 'CamperBot'
    }
  }
  render() {
    return (
       <div>
         <Navbar name={this.state.name}/>
       </div>
    );
  }
};

class Navbar extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
    <div>
      <h1>Hello, my name is: {this.props.name}</h1>
    </div>
    );
  }
};
```

---
## Pass a Callback as Props
You can also pass handler functions or any method that's defined on a React component to a child component.
```JSX
class MyApp extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      inputValue: ''
    }
    this.handleChange = this.handleChange.bind(this);
  }
  handleChange(event) {
    this.setState({
      inputValue: event.target.value
    });
  }
  render() {
    return (
       <div>
        <GetInput input={this.state.inputValue} handleChange={this.handleChange}/>
        <RenderInput input={this.state.inputValue}/>
       </div>
    );
  }
};

class GetInput extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h3>Get Input:</h3>
        <input
          value={this.props.input}
          onChange={this.props.handleChange}/>
      </div>
    );
  }
};

class RenderInput extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h3>Input Render:</h3>
        <p>{this.props.input}</p>
      </div>
    );
  }
};
```
```
```
