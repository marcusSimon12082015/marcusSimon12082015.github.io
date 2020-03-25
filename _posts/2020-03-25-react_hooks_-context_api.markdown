---
layout: post
title:      "React Hooks -Context API"
date:       2020-03-25 23:16:41 +0000
permalink:  react_hooks_-context_api
---



Context provides a way to pass data through the component tree without having to
pass props down manually at every level.

Creating a new context

```
import React from 'react';

const ComicsContext = React.createContext();

export { ComicsContext as default  }
```

We can provide a default value for the context as an argument or leave it empty. 
Now we can import the new Context were we need it.

We use it in our JSX 

```
return(
	<ComicsContext.Provider value={{ comics, dispatch }}>
		<h1>Latest Comics</h1>
		<ComicsList comics={comics} />
	</ComicsContext.Provider>
)
```

We specify the things we want to share between componets in a value property on a Provider.
So now we dont need comics property on ComicsList anymore.

```
return(
	<ComicsContext.Provider value={{ comics, dispatch }}>
		<h1>Latest Comics</h1>
		<ComicsList  />
	</ComicsContext.Provider>
)
```

Inside a component we now have to use the useContext to get access to values.

```
import React, { useContext } from 'react';
import ComicsContext from '../context/comics-context';

const ComicsList = () => {
	const { comics } = useContext(ComicsContext)
	
	return comics.map((comic) => (
		...
	))
}
```

This is just a small sample of what we can do with Context API. I will further explore the topic and try to 
use it in my future projects to get a better understanding of the whole React ecosystem.
