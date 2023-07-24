--> This hook is intriduced in react 18 to deal with concurrency and rendering slow content.

--> The useDeferredValue hook allows us to fix the slow render problem by implementing a delay before some information is calculated. This works in a very similar way to debouncing and throttling since our deferred value will only be calculated after the important state updates have finished running. 

-->According to react documentation: "useDeferredValue is a React Hook that lets you defer updating a part of the UI."

 --> function App() {
  const [name, setName] = useState("")
  const deferredName = useDeferredValue(name)
  const list = useMemo(() => {
    return largeList.filter(item => item.name.includes(deferredName))
  }, [deferredName])

  function handleChange(e) {
    setName(e.target.value)
  }

  return (
    <>
      <input type="text" value={name} onChange={handleChange} />
      {list.map(item => (
        <ListComponent key={item.id} item={item} />
      ))}
    </>
  )
}

  useDeferredValue takes a single parameter which is the value you want setup your throttle/debounce on. This hook will then return a value which will be the deferred version of the value you pass in. This means that when our name variable changes the deferredName will still stay the same since useDeferredValue will not immediately update the value of the deferredName. This allows time for our component to completely rerender with the new name value since our list will not try to update itself as it is waiting for the deferredName to change. This makes the app feel more responsive since the input will update immediately while the list will be delayed in its update.

  --> This hook is not ideal to use all the time. If you use this hook all the time you will actually make your app less performant since React will be forced to do extra rerenders of your app. This is because it will do the initial rerender and the deferred rerender when it could have done them both in one update without useDeferredValue.

  --> The useDeferredValue hook makes working with slow, computationally intense rerenders so much easier since now we can tell React to defer those updates until later which makes your application seem much more performant to users.
