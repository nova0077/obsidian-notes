- Redux is a global state manager for react.
- It provides a store, access and update the state of your application in a consistent way, making it easier to manage complex states.
- Redux Store and Redux both stands for a container for javascript apps and it stores the whole state of the app.
- Store is similar to context api, but here instead of having a value we have store.
- A store is just a place where we group all our different global state applications.
- configure store creates store for Redux Tool Kit.
- Other state management libraries are MobX & Recoil

#### Step1: Setting up Redux
```jsx
npm install redux
```

#### Step2: Creating Actions
Actions => are simple JS objects that describes what happened in our app.
Here counter app, we have 2 actions, (increment and decrement).
```jsx
// actions.js
export const increment = () => {
    return {
        type: 'INCREMENT'
    };
};

export const decrement = () => {
    return {
        type: 'DECREMENT'
    };
};

```

#### Step3: Creating Reducers
Reducers => Reducers specify how the state of your app changes in response to actions. 
They are functions that take the current state and an action, and return the next state.
```jsx
// counter.js
const counterReducer = (state = 0, action) => {
    switch (action.type) {
        case 'INCREMENT':
            return state + 1;
        case 'DECREMENT':
            return state - 1;
        default:
            return state;
    }
};

export default counterReducer;
```

#### Step4: Creating a Redux Store
Redux Store => A Redux store holds the state of your application. 
Its created using the 'createStore' function, which takes a reducer as an argument.

```jsx
// store.js
import { createStore } from 'redux';
import counterReducer from './counter';

const store = createStore(counterReducer);

export default store;

```

#### Step5: Using Redux with React

```jsx
// Counter.js
import React from 'react';
import { connect } from 'react-redux';
import { increment, decrement } from './actions';

function Counter(props) {
    return (
        <div>
            <p>Count: {props.count}</p>
            <button onClick={props.increment}>Increment</button>
            <button onClick={props.decrement}>Decrement</button>
        </div>
    );
}

const mapStateToProps = (state) => {
    return {
        count: state
    };
};

const mapDispatchToProps = {
    increment,
    decrement
};

export default connect(mapStateToProps, mapDispatchToProps)(Counter);
```

#### Step6: Connecting Redux Store to App
```jsx
// App.js
import React from 'react';
import { Provider } from 'react-redux';
import store from './store';
import Counter from './Counter';

function App() {
    return (
        <Provider store={store}>
            <Counter />
        </Provider>
    );
}

export default App;
```

Whenever you click the "Increment" or "Decrement" buttons in the 'Counter' component, Redux handles the state updates and re-renders the component accordingly.