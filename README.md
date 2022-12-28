##### A simple example of React-Redux for beginners.
##### It's really an awesome thing for managing global state.

```

import React from 'react';
import { createStore } from 'redux';
import { Provider } from 'react-redux';

// The reducer function updates the state based on the action that is dispatched
function reducer(state, action) {
  switch (action.type) {
    case 'INCREMENT':
      return { count: state.count + 1 };
    case 'DECREMENT':
      return { count: state.count - 1 };
    default:
      return state;
  }
}

// Create a Redux store with an initial state of { count: 0 }
const store = createStore(reducer, { count: 0 });

// The Counter component reads the count from the Redux store and dispatches actions to update it
function Counter() {
  return (
    <div>
      <button onClick={() => store.dispatch({ type: 'DECREMENT' })}>-</button>
      <span>{store.getState().count}</span>
      <button onClick={() => store.dispatch({ type: 'INCREMENT' })}>+</button>
    </div>
  );
}

// The App component wraps the Counter in a Provider to make the store available to the Counter
function App() {
  return (
    <Provider store={store}>
      <Counter />
    </Provider>
  );
}

export default App;

```
