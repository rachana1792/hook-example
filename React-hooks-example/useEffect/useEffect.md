--> Most React components are pure functions, meaning they receive an input and produce a predictable output of JSX.

--> UseEffects() provide a way to handle performing these side effects in what are otherwise pure React components.

--> In react documentation they defined useEffect() as: "useEffect is a React Hook that lets you synchronize a component with an external system."

--> useEffect is mainly used while:
    :: Fetching data
    :: Reading from local storage
    :: Registering and deregistering event listeners

--> UseEffect Syntax:

import { useEffect } from 'react';

function MyComponent() {
  // 2. call it above the returned JSX  
  // 3. pass two arguments to it: a function and an array
  useEffect(() => {}, []);
  
  // return ...
}

--> If you do not provide the dependencies array at all and only provide a function to useEffect, it will run after every render.

--> If you forget to provide your dependencies correctly and you are setting a piece of local state when the state is updated, the default behavior of React is to re-render the component. And therefore, since useEffect runs after every single render without the dependencies array, we will have an infinite loop.

--> A common example of a component being unmounted is going to a new page or a new route in our application where the component is no longer rendered.

--> The side effect cleanup is not required in every case. It is only required in a few cases, such as when you need to stop a repeated side effect when your component unmounts.