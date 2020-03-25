---
layout: post
title:      "Promises, Async Await"
date:       2020-03-25 12:58:03 -0400
permalink:  promises_async_await
---


**Promises** allows us to do something after a long task completes.

```
const promise = new Promise((resolve,reject) => {
		resolve('...Resolved')
});

promise.then((data) => {
	console.log(data);
});
```

then lets us register a callback. A callback is going to fire when and if the promise is resolved. We have access
to any data that is passed on.

You can only reject or resolve a promise, and can only do so a single time. So everything after resolve call is ignored. We can also pass just a single argument to resolve or reject.

```
const promise = new Promise((resolve,reject) => {
		reject('...Rejected')
});

promise.then((data) => {
	console.log(data);
}).catch((error) => {
	console.log(error);
});
```

If a promise is rejected we deal with it in a catch handlerer. We can also remove the catch part and add it 
as a second argument to a then

```
promise.then((data) => {
	console.log(data);
}, (error) => {

});
```

Promises can also be chained as we can see with fetch example:

```
const promise = fetch("...");

promise
	.then(res => res.json())
	.then(data => console.log(data.title));
```



**Async Await**


Its syntactic sugar that lets us read  asynchronous code as synchronous code.

```
const getComic = async(title) => {
	... get comic with title 
	return comic;
}
```

async keyword means that when we return something it automatically returns a resolved promise.
So without the async keyword:

```
const getComic = (title) => {
	... get comic with title 
	return Promise.resolve(comic);
}
```

so if we combine async and await:

```
const getComic = async(title) => {
	... get comic with title 
	const comic = await promise;
}
```

waits until a promise is resolved. If we have multiple promises we can use
```
Promise.all([promise1,promise2]); 
```


Of course this is just a starting point. Now it is time to use this in a project.


