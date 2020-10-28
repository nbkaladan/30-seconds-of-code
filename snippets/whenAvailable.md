---
title: whenAvailable
tags: function, browser, recursion, intermediate
---

Wait for a global variable to be available and call a function when it is.

- Every 10 milliseconds it checks for the existence of the variable, to call the callback function when it is.
- It will run indifenitely if the variable is never set.

```js
const whenAvailable = (name, callback) => {
  const interval = 10;
  const checker = () => {
    if (window[name]) {
      callback(window[name]);
    } else {
      window.setTimeout(checker, interval);
    }
  };
  window.setTimeout(checker, interval);
};
```

```js
whenAvailable('customLibrary', onCustomLibraryAvailableFunction); // Will call onCustomLibraryAvailableFunction when arrive
```
