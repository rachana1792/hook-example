--> A useLayoutEffect hook is a React hook that can be passed through in a component's render method to cause the react library to consider the page’s layout and change its calculations for things like spacing and overflow.

--> According to react documentation: "useLayoutEffect is a version of useEffect that fires before the browser repaints the screen."

-->The React useLayoutEffect hook takes two arguments. The first argument is a function called effect, and the second argument is an array of dependents. Generally, the first argument, effect, is either undefined or yields a cleanup function. The useLayoutEffect function code is shown below:

import React, { useLayoutEffect } from "react";
const APP = props => {
  useLayoutEffect(() => {
    //Do something and either return undefined or a cleanup function
    return () => {
    //Do some cleanup here
    };
  }, [dependencies]);
};  