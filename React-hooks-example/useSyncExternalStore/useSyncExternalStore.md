--> This hook is introduced in react 18 to properly subscribe to values in stores.

--> External store is something which we can subscribe to. Examples of the external store include Redux store, Zustand store, global variables, module scope variables, DOM state, etc.

--> Internal stores include props, context, useState, useReducer.

-->useSyncExternalStore is a React Hook that lets you subscribe to an external store.

-->import {useSyncExternalStore} from 'react';

//Basic usage. getSnapshot must return a cached/memoized result
useSyncExternalStore(
  subscribe: (callback) => Unsubscribe
  getSnapshot: () => State
) => State

// Selecting a specific field using an inline getSnapshot
const selectedField = useSyncExternalStore(store.subscribe, () => store.getSnapshot().selectedField);

--> useSyncExternalStore hook takes two functions

‘subscribe’ function to register a callback function
‘getSnapshot’ is used to check if the subscribed value has changed since the last time, it was rendered, It either needs to be an immutable value like a string or number, or it needs to be a cached/memoized object. The immutable value is then returned by the hook.

--> This hook is used in :
    :: Libraries that have components and custom hooks which don’t access external mutable data while rendering and only pass information using React props, state or context, are not affected.

    :: The libraries which deal with data fetching, state management, or styling (Redux, MobX, Relay) are affected. It is because these libraries store their state outside of React. With concurrent rendering, those data stores can be updated in the middle of rendering, without React knowing about it.