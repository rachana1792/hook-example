--> This hook is maily used in situations where re-rendering of same object is done.

--> For inline functions reendering is chaeaper but for complex functions it will affect the performance in that case we use useCallback()

-->Any function you define inside of useCallback() is re-created whenever the component rebuilds

--> Accrding to the react documentation they defiend useCallBack as: " React Hook that lets you cache a function definition between re-renders."

There are 2 examples here. 

example 1:

import useSearch from './fetch-items';

function MyList({ term, onItemClick }) {
  const items = useSearch(term);

  const map = item => <div onClick={onItemClick}>{item}</div>;

  return <div>{items.map(map)}</div>;
}

export default React.memo(MyBigList);


import { useCallback } from 'react';

export function MyParent({ term }) {
  const onItemClick = useCallback(event => {
    console.log('You clicked ', event.currentTarget);
  }, [term]);

  return (
    <MyList
      term={term}
      onItemClick={onItemClick}
    />
  );
}

--> 1st example is the example of good use of useCallback(). Because, there is a big list of itmes and re-rendering of that list is a complex.To prevent useless list re-renderings, you wrap it into React.memo(). The parent component of MyList provides a handler function to know when an item is clicked.onItemClick callback is memoized by useCallback(). As long as term is the same, useCallback() returns the same function object.
When MyParent component re-renders, onItemClick function object remains the same and doesn't break the memoization of MyBigList.

example 2:

 import { useCallback } from 'react';

function MyComponent() {
  // handleClick is the same function object
  const handleClick = useCallback(() => {
    console.log('Clicked!');
  }, []);


-->In example 2, The usecallback() hook is called every time MyComponent renders. This reduces the render performance and increses the complexity of the code since each time it is being memorized.

--> UseCallback() only if the function is expensive. else we can go with the simple functions because usecallback makes the functions complex because each time it is to be memorized, so calling every function inside useCallback() is not a good technique.
