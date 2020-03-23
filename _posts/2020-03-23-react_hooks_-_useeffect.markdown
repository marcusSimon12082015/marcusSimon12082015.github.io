---
layout: post
title:      "React Hooks - useEffect"
date:       2020-03-23 20:55:34 +0000
permalink:  react_hooks_-_useeffect
---


useEffect is kind of a replacement for lifecycle methods in our class based components.

```
import React, { useState, useEffect } from 'react';
```

We pass a function to useEffect that is a mixture of lifecycle methods componentDidMount and componentDidUpdate.
So it runs after the first render and on every component state or props change.

We can specify useEffect dependencies as the second argument an array, but it is not required. We can specify if a part of our state changes useEffect is called.

```
useEffect(() => {

},[comics]);
```


We can define multiple useEffects in a functional component and they can all have their own set of dependencies. If we specify no dependencies it will only run once.

```
useEffect(() => {

},[]);
```

We can also catch when component unmounts and gets removed from the screen.

```
useEffect(() => {
 return = () => {
     console.log("Clean up!");
 }
},[]);
```

We do this by returning a function from useEffect and getting a similar behaviour as componentDidUnmount.
This is just some basic pointers to get you started. 



