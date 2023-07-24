--> The useDebugValue hook is simply used to print out debug information for custom hooks.

--> We can refer the values in react dev tools.

-->According to react documentation: "useDebugValue is a React Hook that lets you add a label to a custom Hook in React DevTools."

--> This hook is mainly useful if you are creating a library for others to use since they can easily see information about your hook, but it also is useful for your own hooks since you can quickly see detailed information about your hooks.

--> Example for useDebugValue is:

export default function useUser() {
  const [user, setUser] = useState(getUser())

  useDebugValue(user == null ? "No User" : user.name)

  return [user, setUser]
}

In useUser hook we have a useDebugValue hook that takes a string as its only argument. Passing a single string to useDebugValue.