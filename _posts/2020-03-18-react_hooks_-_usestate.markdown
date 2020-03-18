---
layout: post
title:      "React Hooks - useState"
date:       2020-03-18 20:37:28 +0000
permalink:  react_hooks_-_usestate
---



What is a hook? Hook is a function that lets us use state or lifecycle methods.
React Hooks where available from version 16.8.0. It helps simplify our code.
In stateless functional components as the name suggests, there was no way to handle local state 
or lifecycle methods, as opposed to class components.
Previously state could only be an object. With useState state can now be a number, string or a boolean.

```
import React, { useState } from 'react';
const [state, setState] = useState(initialState);
```

So how does useState differ from setState; useState is not merging the objects, but 
is completely replacing the old state with the new state.
Here is an example of changing a class component into a functional component using useState.

```
class Header extends React.Component
{
  state = {
    modalOpen: false
  };

  handleModalOpen = () => {
   this.setState({modalOpen:true});
  }

 handleModalClose = () => {
  this.setState({modalOpen:false});

 }
 
 ...
```

Here we have a Header component that uses local state to handle Modal being active or not.
So first we import useState 

```
import React, { useState } from 'react';

const Header = props =>
{
  const [modalOpen, setModalState] = useState(false)
 
  const handleModalOpen = () => {
   setModalState(true)
  }

 const handleModalClose = () => {
   setModalState(false)
 }

 ...

```

We can now change class component to functional one and instead of using this.setState, we now use a function we defined called setModalState.

```
<LoginModal modalOpen={this.state.modalOpen} handleModalOpen={this.handleModalOpen}
handleModalClose={this.handleModalClose}/>

<LoginModal modalOpen={modalOpen} handleModalOpen={handleModalOpen}
handleModalClose={handleModalClose}/>

```

We also do not have to use this.state anymore.
