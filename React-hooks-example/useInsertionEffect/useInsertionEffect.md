-->Introduced in react 18.
--> useInsertionEffect is for CSS-in-JS library authors. 

--> Assume we have some components that insert styles and some components that read layout. If we use the useLayoutEffect hook to insert styles, it causes the layout to be computed multiple times in a single pass. Additionally, if one hook tries to read the layout before the CSS has been inserted, it would read the incorrect layout.

So, to handle this use-case, a new hook was introduced - useInsertionEffect.

--> Accoreding to react documentation :"useInsertionEffect is a version of useEffect that fires before any DOM mutations."

useInsertionEffect(setup, dependencies?)

--> The signature of useInsertionEffect is identical to useEffect. But it fires synchronously before all DOM mutations.

--> It should be used for inserting global DOM nodes like <style> or SVG <defs> before reading layout in useLayoutEffect. It is not really meant to be used by anything else other than these CSS libraries.

T--> his hook is limited in scope, so it does not have access to refs and cannot schedule updates.