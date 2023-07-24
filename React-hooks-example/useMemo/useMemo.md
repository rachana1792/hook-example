--> useMemo is a React Hook that lets you cache the result of a calculation between re-renders.

--> const cachedValue = useMemo(compute, dependencies)
useMemo() accepts 2 arguments — a function compute that computes a result, and the depedencies array.

--> During initial rendering, useMemo(compute, dependencies) invokes compute, memoizes the calculation result, and returns it to the component.

--> If the dependencies don't change during the next renderings, then useMemo() doesn't invoke compute, but returns the memoized value.

--> But if the dependencies change during re-rendering, then useMemo() invokes compute, memoizes the new value, and returns it.

--> useMemo(() => computation(a, b), [a, b]) is the hook that lets you memoize expensive computations. Given the same [a, b] dependencies, once memoized, the hook is going to return the memoized value without invoking computation(a, b).

--> Example:
import { useMemo } from 'react';

function TodoList({ todos, tab }) {
  const visibleTodos = useMemo(
    () => filterTodos(todos, tab),
    [todos, tab]
  );
  // ...
}
--> useMemo is used in circumstances like:
    :: Skipping expensive recalculations
    :: Skipping re-rendering of components
    :: Memoizing a dependency of another Hook
    :: Memoizing a function