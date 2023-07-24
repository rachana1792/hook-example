--> According to react documentation "useRef is a React Hook that lets you reference a value that’s not needed for rendering."

--> useRef(initialValue) accepts one argument as the initial value and returns a reference. 
A reference is an object having a special property current.

import { useRef } from 'react';

function MyComponent() {
  const initialValue = 0;
  const reference = useRef(initialValue);

  const someHandler = () => {
    // Access reference value:
    const value = reference.current;

    // Update reference value:
    reference.current = newValue;
  };

  // ...
}

reference.current accesses the reference value, and reference.current = newValue updates the reference value. Pretty simple.

--> The value of the reference is persisted (remains unchanged) between component re-renderings;
--> Updating a reference doesn't trigger a component re-rendering.

--> Example:
import { useRef } from 'react';

export default function Counter() {
  let ref = useRef(0);

  function handleClick() {
    ref.current = ref.current + 1;
    alert('You clicked ' + ref.current + ' times!');
  }

  return (
    <button onClick={handleClick}>
      Click me!
    </button>
  );
}

-->By default, your own components don’t expose refs to the DOM nodes inside them. To fix this, find the component that you want to get a ref to, then wrap it in forwardRef.