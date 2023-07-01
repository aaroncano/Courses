# Redux


Redux is a state management framework that can be used with a number of different web technologies, including React.

In Redux, there is a single state object that's responsible for the entire state of your application. This means if you had a React app with ten components, and each component had its own local state, the entire state of your app would be defined by a single state object housed in the Redux store.

---
## Create a Redux Store
The Redux store is an object which holds and manages application state. There is a method called createStore() on the Redux object, which you use to create the Redux store. This method takes a reducer function as a required argument. The reducer function is covered in a later challenge, and is already defined for you in the code editor. It simply takes state as an argument and returns state.

```js
const reducer = (state = 5) => {
  return state;
}

// Redux methods are available from a Redux object
// For example: Redux.createStore()

const store = Redux.createStore(reducer);
```

---
## Get State from the Redux Store
```js
const store = Redux.createStore(
  (state = 5) => state
);

let currentState = store.getState();
```

---
## Define a Redux Action
An action is simply a JavaScript object that contains information about an action event that has occurred. The Redux store receives these action objects, then updates its state accordingly. Sometimes a Redux action also carries some data.
```js
let action = {
  type : 'LOGIN'
}
```

---
## Define an Action Creator
An action creator is simply a JavaScript function that returns an action. In other words, action creators create objects that represent action events.
```js
const action = {
  type: 'LOGIN'
}

function actionCreator(){
  return action;
}
```

---
## Dispatch an Action Event
dispatch method is what you use to envío actions to the Redux store. Calling store.dispatch() and passing the value returned from an action creator sends an action back to the store.
```js
const store = Redux.createStore(
  (state = {login: false}) => state
);

const loginAction = () => {
  return {
    type: 'LOGIN'
  }
};

store.dispatch(loginAction());
```

---
## Handle an Action in the Store
Reducers in Redux are responsible for the state modifications that take place in response to actions. A reducer takes state and action as arguments, and it always returns a new state. It is important to see that this is the only role of the reducer. It has no side effects — it never calls an API endpoint and it never has any hidden surprises. The reducer is simply a pure function that takes state and action, then returns new state.
```js
const defaultState = {
  login: false
};

const reducer = (state = defaultState, action) => {
  if(action.type == 'LOGIN'){
    return {
      login: true
    }
  }else{
    return defaultState;
  }
};

const store = Redux.createStore(reducer);

const loginAction = () => {
  return {
    type: 'LOGIN'
  }
};
```

---
## Use a Switch Statement to Handle Multiple Actions
```js
const defaultState = {
  authenticated: false
};

const authReducer = (state = defaultState, action) => {
  // Change code below this line

  // Change code above this line
};

const store = Redux.createStore(authReducer);

const loginUser = () => {
  return {
    type: 'LOGIN'
  }
};

const logoutUser = () => {
  return {
    type: 'LOGOUT'
  }
};
```

---
## Use const for Action Types
```js
const LOGIN = 'LOGIN';
const LOGOUT = 'LOGOUT';

const defaultState = {
  authenticated: false
};

const authReducer = (state = defaultState, action) => {

  switch (action.type) {
    case LOGIN: 
      return {
        authenticated: true
      }
    case LOGOUT: 
      return {
        authenticated: false
      }

    default:
      return state;

  }

};

const store = Redux.createStore(authReducer);

const loginUser = () => {
  return {
    type: LOGIN
  }
};

const logoutUser = () => {
  return {
    type: LOGOUT
  }
};
```

---
## Register a Store Listener
Another method you have access to on the Redux store object is store.subscribe(). This allows you to subscribe listener functions to the store, which are called whenever an action is dispatched against the store. One simple use for this method is to subscribe a function to your store that simply logs a message every time an action is received and the store is updated.
```js
const ADD = 'ADD';

const reducer = (state = 0, action) => {
  switch(action.type) {
    case ADD:
      return state + 1;
    default:
      return state;
  }
};

const store = Redux.createStore(reducer);

// Global count variable:
let count = 0;

function incrementCount(){
  count++;
}
store.subscribe(incrementCount);

store.dispatch({type: ADD});
console.log(count);
store.dispatch({type: ADD});
console.log(count);
store.dispatch({type: ADD});
console.log(count);
```

---
## Combine Multiple Reducers
In order to let us combine multiple reducers together, Redux provides the combineReducers() method. This method accepts an object as an argument in which you define properties which associate keys to specific reducer functions. The name you give to the keys will be used by Redux as the name for the associated piece of state.
```js
const INCREMENT = 'INCREMENT';
const DECREMENT = 'DECREMENT';

const counterReducer = (state = 0, action) => {
  switch(action.type) {
    case INCREMENT:
      return state + 1;
    case DECREMENT:
      return state - 1;
    default:
      return state;
  }
};

const LOGIN = 'LOGIN';
const LOGOUT = 'LOGOUT';

const authReducer = (state = {authenticated: false}, action) => {
  switch(action.type) {
    case LOGIN:
      return {
        authenticated: true
      }
    case LOGOUT:
      return {
        authenticated: false
      }
    default:
      return state;
  }
};

const rootReducer = Redux.combineReducers({
  count: counterReducer,
  auth: authReducer
});

const store = Redux.createStore(rootReducer);
```

---
## Send Action Data to the Store
You can also send specific data along with your actions. In fact, this is very common because actions usually originate from some user interaction and tend to carry some data with them. The Redux store often needs to know about this data.
```js
const ADD_NOTE = 'ADD_NOTE';

const notesReducer = (state = 'Initial State', action) => {
  switch(action.type) {
    case ADD_NOTE:
      return action.text;
    default:
      return state;
  }
};

const addNoteText = (note) => {
  return {
    type: ADD_NOTE,
    text: note
  }
};

const store = Redux.createStore(notesReducer);

console.log(store.getState());
store.dispatch(addNoteText('Hello!'));
console.log(store.getState());
```

---
## Use Middleware to Handle Asynchronous Actions
To include Redux Thunk middleware, you pass it as an argument to Redux.applyMiddleware(). This statement is then provided as a second optional parameter to the createStore() function. Take a look at the code at the bottom of the editor to see this. Then, to create an asynchronous action, you return a function in the action creator that takes dispatch as an argument. Within this function, you can dispatch actions and perform asynchronous requests.
```js
const REQUESTING_DATA = 'REQUESTING_DATA'
const RECEIVED_DATA = 'RECEIVED_DATA'

const requestingData = () => { return {type: REQUESTING_DATA} }
const receivedData = (data) => { return {type: RECEIVED_DATA, users: data.users} }

const handleAsync = () => {
  return function(dispatch) {
    dispatch(requestingData());

    setTimeout(function() {
      let data = {
        users: ['Jeff', 'William', 'Alice']
      }
      
    dispatch(receivedData(data));

    }, 2500);
  }
};

const defaultState = {
  fetching: false,
  users: []
};

const asyncDataReducer = (state = defaultState, action) => {
  switch(action.type) {
    case REQUESTING_DATA:
      return {
        fetching: true,
        users: []
      }
    case RECEIVED_DATA:
      return {
        fetching: false,
        users: action.users
      }
    default:
      return state;
  }
};

const store = Redux.createStore(
  asyncDataReducer,
  Redux.applyMiddleware(ReduxThunk.default)
);
```

---
## Write a Counter with Redux
```js
const INCREMENT = 'INCREMENT';
const DECREMENT = 'DECREMENT';

const counterReducer = (state = 0, action) => {
  switch(action.type){
    case INCREMENT:
      return state + 1;
    case DECREMENT:
      return state - 1;
    default:
      return state;
  }
};

const incAction = () => {
  return {
    type: INCREMENT
  }
}

const decAction = () => {
  return {
    type: DECREMENT
  }
}

const store = Redux.createStore(counterReducer);
```

---


# Ejercicios sobre inmutabilidad

## Never Mutate State
```js
const ADD_TO_DO = 'ADD_TO_DO';

// A list of strings representing tasks to do:
const todos = [
  'Go to the store',
  'Clean the house',
  'Cook dinner',
  'Learn to code',
];

const immutableReducer = (state = todos, action) => {
  switch(action.type) {
    case ADD_TO_DO:
      return [...todos, action.todo]
    default:
      return state;
  }
};

const addToDo = (todo) => {
  return {
    type: ADD_TO_DO,
    todo
  }
}

const store = Redux.createStore(immutableReducer);
```

---
## Use the Spread Operator on Arrays
```js
const immutableReducer = (state = ['Do not mutate state!'], action) => {
  switch(action.type) {
    case 'ADD_TO_DO':
      let arr = [...state, action.todo];
      return arr;
    default:
      return state;
  }
};

const addToDo = (todo) => {
  return {
    type: 'ADD_TO_DO',
    todo
  }
}

const store = Redux.createStore(immutableReducer);
```

---
## Remove an Item from an Array
```js
const immutableReducer = (state = [0,1,2,3,4,5], action) => {
  switch(action.type) {
    case 'REMOVE_ITEM':
      return [...state.slice(0, action.index), ...state.slice(action.index + 1, state.length)]
    default:
      return state;
  }
};

const removeItem = (index) => {
  return {
    type: 'REMOVE_ITEM',
    index
  }
}

const store = Redux.createStore(immutableReducer);
```

---
## Copy an Object with Object.assign
```js
const defaultState = {
  user: 'CamperBot',
  status: 'offline',
  friends: '732,982',
  community: 'freeCodeCamp'
};

const immutableReducer = (state = defaultState, action) => {
  switch(action.type) {
    case 'ONLINE':
      return Object.assign({}, state, {status: 'online'});
    default:
      return state;
  }
};

const wakeUp = () => {
  return {
    type: 'ONLINE'
  }
};

const store = Redux.createStore(immutableReducer);
```
```