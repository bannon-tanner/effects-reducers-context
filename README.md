# Handling Side Effects, Using Reducers, & Using the Context API - React Complete Guide

[React - The Complete Guide (incl Hooks, React Router, Redux)](https://www.udemy.com/course/react-the-complete-guide-incl-redux/)

Advanced and essential features for working with more complex projects

## Things Learned from this project

### useEffect()
- Effects (useEffect()) are useful to mitigate infinite render loops
  - e.g., If an https request was made upon a component render, then some piece of state was updated, the cycle would continue forever
  ```js
  useEffect(() => { ... }, [ dependencies ])
  ```
  - First argument of `useEffect` is a function that gets executed after every component evaluation IF the specified dependencies changed
  - Second argument is the dependencies
    - NOTE: provide an empty array `[]` as dependencies for the Effect to only run on component FIRST render
    - State updating functions never change, so they do not need to be in dependencies
  - SEE:
    - App.js for useEffect with no dependencies (only runs on first component render)
    - Login.js for useEffect with dependencies that updates on input change
  - Cleanup with useEffect
    - Can do a rigged debouncing (I have only ever used lodash) with setTimeout
      - Put timer in useEffect hook
      - Clear timer every time a new one runs, so there is only ever one timer at any given moment/render
      - can clear timer before the next one is called
    - useEffect can return a function (and only a function) - called a cleanup function
    - SEE: Login.js for useEffect cleanup function

### useReducer()
- useReducer - "more powerful state management" - useful when state becomes complex
  - when you have state updates that depend on other states
  - when you have multiple related states
  - could have problem such as:
    ```js
    setFormIsValid(
      event.target.value.includes('@') && enteredPassword.trim().length > 6
    )
    ```
    - which could cause problems based on it updating from 2 other states, so the function form can't be used because it doesn't depend on it's own previous state, but on the previous state of the 2 others


## Other things to note

- 

## To run this project
Clone this repo and cd into the project folder
```bash
npm install
npm start
```