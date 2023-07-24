--> This hook is introduced in react 18.

-->Before React 18, rendering was synchronous. This meant that once React started rendering, nothing could stop it until it completed rendering the component.

-->According to react documentation:" useTransition is a React Hook that lets you update the state without blocking the UI."

--> When we call the useTransition hook, we get an array with two elements. The first element is a boolean value that specifies if the rendering is pending or not. The second element is the startTransition method.

--> This method accepts a callback function. Any state update we perform within this callback function will be considered a transition update.

--> We can use the useTransition hook to tell React that a certain state change will result in an expensive rendering. React will then deprioritize this state change allowing other renderings to take place faster providing a very responsive UI. 

--> Example:
import './App.css'
import { useState, useMemo, useTransition } from "react";

const numbers = [...new Array(20000).keys()];

export default function App() {
    const [query, setQuery] = useState("");
    const [text, setText] = useState("");
    const [isPending, startTransition] = useTransition();

    const handleChange = (e) => {
        setText(e.target.value);
        startTransition(() => {
            setQuery(e.target.value);
        });
    };

    const list = useMemo(() => (
        numbers.map((i, index) => (
            query
                ? i.toString().startsWith(query)
                && <p key={index}>{i}</p>
                : <p key={index}>{i}</p>
        ))
    ), [query]);

    return (
        <div>
            <input type="number" onChange={handleChange} value={text} />
            <div>
                {
                    isPending
                        ? "Loading..."
                        : list
                }
            </div>
        </div>
    );
}

when I first enter a key, React will update the first state, perform a render and then update the second state and start the more expensive render. Now, if I enter another key, since React knows that this is a transition update, it will abort the transition rendering, perform the urgent render, and then start a new transition render. This means that the user will not experience any lag while typing into the textbox.

--> We use the useTransition hook to tell React that a certain setState method will trigger a transition update, we use the useDeferredValue hook to tell React that a received prop value will trigger a transition update.