---
title: "Getting Started With React Hooks For Beginner"
datePublished: Fri Mar 31 2023 21:24:47 GMT+0000 (Coordinated Universal Time)
cuid: clfx1z7vs000f09idbq4p2rja
slug: getting-started-with-react-hooks-for-beginner
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1680327817660/96f83f1e-cdd6-4c9a-b26d-34b39ba5dbf0.png
tags: tutorial, reactjs, hooks

---

If you are reading this article you already know what is React and you have a basic understanding of how React works. Even if you don't know about React don't worry. You can read my article of [React for absolute begineers](https://blog.rijusougata13.com/get-started-with-react-beginners-guide).

So in one line, you can say

```plaintext
React.js is an open-source JavaScript-based user interface library. It is hugely popular for web and mobile app development.
```

Before React 16.8 most of the developers used class-based components for handling states and managing life cycles. But React 16.8 introduces "Hooks" to us for functional-based components.

### What are the React Hooks?

Reacts hooks are built-in function which allows developers to manage state and use lifecycle in a functional component. Before hooks, we can manage those only in class components. But hooks made our life much easier and uses of class-based components decreased day by day from then.

So if we can manage state and lifecycle in class-based components, why do we need React hooks?

1. **Easy to reuse**: Every developer wants to reuse components. They don't want to write the same code again and again. Hooks allow you to reuse state logic without changing your component hierarchy. So it can be shared among other components.
    
2. **Makes coding easier**: Writing code in react js is very easy. But when you will be working on a big project and you have to play with too much logic. Class-based components may get hard to understand and debug at this level. Hooks solve this problem but separating singular components into various small functions. So it makes the codebase more understandable.
    
3. **Less coding:** In class-based components, you have to write many unnecessary codes to make your code run. But with hooks you don't have to bind methods, skip using "this" and many more.
    

### Rules of Using React Hooks:

There are mainly two rules which you have to follow when using react hooks. Otherwise, it will not work. They are

1. **Only Call Hooks at the Top Level**: You shouldn't call hooks in nested functions, conditions or any loops. It should be declared at the top level of react functions.
    
2. **Only Call Hooks from React Functions**: You should always call hooks from react functions or any custom hooks ( We will be discussing it later).
    

### Basic React hooks:

There are many types of react hooks. In this article, I will be discussing some. But you can read more about react hooks [here](https://legacy.reactjs.org/docs/hooks-intro.html).

1. **useState**: It will help you manage states in functional components. It returns a state value and a function to update the value.
    
2. **useEffect**: It helps you to manage side effects in functional components, like subscriptions, timers, mutations, etc.
    
3. **useContext**: It accepts a context object (the value returned from `React.createContext`) and returns the current context value for that context.
    
4. **useReducer**: Its an alternative to useState. It accepts a reducer of type `(state, action) => newState`, and returns the current state paired with a `dispatch` method.
    
5. **useCallback**: It will return a memoized version of the callback that only changes if one of the dependencies has changed.
    
6. **useMemo**: It will only recompute the memoized value when one of the dependencies has changed.
    
7. **useRef**: It returns a mutable ref object whose `.current` property is initialized to the passed argument (`initialValue`).
    

and there are many more.

### Custom Hooks

A custom Hook is a JavaScript function whose name starts with **”**`use`” and that may call other Hooks.

So you can use multiple hooks and other logic inside that custom hooks and reuse it.

Let's see an example.

```javascript
import { useState, useEffect } from "react";

const useFetch = (url) => {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch(url)
      .then((res) => res.json())
      .then((data) => setData(data));
  }, [url]);

  return [data];
};

export default useFetch;
```

Here you can see I have created a custom function named `useFetch`. Inside it I am using both `useState` and `useEffect` hooks and combining my logic. Similarly wise you can also create your custom hooks at the global level and call it whenever you required.

### Conclusion

Before we end I hope I have given you a clear idea of what hooks are and how to work with them. Now you can shift from old class-based components to modern functional components and enjoy their beauty.  
If you enjoyed this article you can support me by [**buying me a coffee**](https://www.buymeacoffee.com/rijusougata13) and following me on [**twitter**](https://twitter.com/rijusougata13).