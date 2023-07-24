--> In javascript functions if we need to pass something to a child function we provide it as props. so if we have nested childs it will make pop-drilling.

--> useContext is a way in react to pass data through a component tree without the need to prop-dril.
--> In react documentation terms: "useContext is a React Hook that lets you read and subscribe to context from your component."

--> import { createContext, useContext } from 'react';

const ThemeContext = createContext(null);

export default function MyApp() {
  return (
    <ThemeContext.Provider >
      <Form />
    </ThemeContext.Provider>
  )
}

function Form() {
  return (
    <Panel title="Welcome">
      <Button>Sign up</Button>
      <Button>Log in</Button>
    </Panel>
  );
}

function Panel({ title, children }) {
  const theme = useContext(ThemeContext);
  const className = 'panel-' + theme;
  return (
    <section className={className}>
      <h1>{title}</h1>
      {children}
    </section>
  )
}

function Button({ children }) {
  const theme = useContext(ThemeContext);
  const className = 'button-' + theme;
  return (
    <button className={className}>
      {children}
    </button>
  );
}



1st we want to create context and use the created context in return jsx code. Using this we can fetch data and update them as well. 

--> You can hold inside the context:

global state
theme
application configuration
authenticated user name
user settings
preferred language
a collection of services

--> There are some drawbacks for useContext, they are :
    :: integrating the context adds complexity. Creating a context, wrapping everything in a provider, and using the useContext() in every consumer — increases complexity.
    ::  adding context complicates unit testing of components. During testing, you'll have to wrap the consumer components into a context provider. Including the components that are indirectly affected by the context