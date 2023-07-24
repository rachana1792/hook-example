--> useReducer is a React Hook that lets you add a reducer to your component.

--> Stores are used to store data globally in a react application.

--> For rendering and state management react provides the hook useReducer(). The hook does so by extracting the state management out of the component.

--> The useReducer(reducer, initialState) hook accepts 2 arguments: the reducer function and the initial state. The hook then returns an array of 2 items: the current state and the dispatch function.

import { useReducer } from 'react';

function MyComponent() {
  const [state, dispatch] = useReducer(reducer, initialState);

  const action = {
    type: 'ActionType'
  };

  return (
    <button onClick={() => dispatch(action)}>
      Click me
    </button>
  );
}

--> Initial state to initalize the value of store.
// initial state
const initialState = { 
  counter: 0 
};

--> Action objects describes how to update the state. Action object has a property "type" — a string describing what kind of state update the reducer must do.
const action = {
  type: 'increase'
};

--> The reducer is a pure function that accepts 2 parameters: the current state and an action object. Depending on the action object, the reducer function must update the state in an immutable manner, and return the new state.
function reducer(state, action) {
  let newState;
  switch (action.type) {
    case 'increase':
      newState = { counter: state.counter + 1 };
      break;
    case 'decrease':
      newState = { counter: state.counter - 1 };
      break;
    default:
      throw new Error();
  }
  return newState;
}

--> Dispatch function dispaches the action objects.Whenever you want to update the state you simply call the dispatch function with the appropriate action object: dispatch(actionObject).Dispatching means a request to update the state.

const [state, dispatch] = useReducer(reducer, initialState)
 Accepts 2 arguments: the reducer function and the initial state. Also, the reducer returns an array of 2 items: the current state and the dispatch function.

 To update the state call dispatch(action) with the appropriate action object. The action object is then forwarded to the reducer() function that updates the state. If the state has been updated by the reducer, then the component re-renders, and [state, ...] = useReducer(...) hook returns the new state value.
 
-->  useReducer() hook lets you separate the state management from the rendering logic of the component. It fits great to deal with complex state management





