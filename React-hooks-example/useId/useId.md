--> The useId is a new hook introduced in React 18. The useId hook helps generate a unique Id on both the client-side and server-side.

-->useId returns string

--> Accoriding to react documentation: " useId is a React Hook for generating unique IDs that can be passed to accessibility attributes."

--> the useId hook generates a unique id for the app. We join two HTML elements with help Id in HTML most of the time. But now, we can use the useId hook to join two elements in React.

import { useId } from 'react';

function PasswordField() {
  const passwordHintId = useId();
  // ...
}

--> While using this hook make sure you do not target id in CSS because its unique id generates different ids every time for you.

import { useId } from "react";
import "./styles.css";
export default function Example2() {
     let prefix1 = useId();
return (
<div className="card">
    <div>
       <label htmlFor={prefix1 + "-fullName"}>Full Name</label>
       <input type="text" id={prefix1 + "-fullName"} name="Full Name" />  
     </div>
    
     <input type="submit" value="Submit" />
</div>
);
}