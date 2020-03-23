---
layout: post
title:      "React Redux Project "
date:       2020-03-23 11:40:41 -0400
permalink:  react_redux_project
---


For my React project I decided to use my previous Rails project Comic Book Review Corner as an API, 
and completely redo the view part in React while comunication with the server is done through Redux 
actions and state manipulation with reducers.

The client side routing is done with React-router and we incorporate a few additional concepts into the Route component.

```
const AppRouter = () => (
  <BrowserRouter>
    <div>
      <Switch>
        <PublicRoute path="/" component={ComicsHomePage} layout={MainLayout} exact={true} />
        <PublicRoute path="/signup" component={SignUpPage} layout={SignUpLayout} />
        <PublicRoute path="/reviews" component={ReviewsPage} layout={MainLayout} />
        <PrivateRoute path="/profile/:id" component={ProfilePage} layout={MainLayout} />
        <PublicRoute path="/comics/:comicId" component={ComicShowPage} layout={MainLayout} />
        <PublicRoute component={NotFoundPage} layout={MainLayout}/>
      </Switch>
    </div>
  </BrowserRouter>
);

const PublicRoute = ({
  component: Component, layout: Layout, ...rest
}) => (
  <Route {...rest} render={props => (
    <Layout>
      <Component {...props} />
    </Layout>
  )}
  />
);

export default PublicRoute;
```

We define PublicRoute and PrivateRoute components which help us execute a few actions that determine if the component will display or not. We also add a layout option so we can include different layouts in our application. 
Below is the MainLayout component.

```
export default ({children}) => (
  <>
    <Header />
    {children}
  </>
)
```

To help us with structuring our application react-bootstrap was used. Here is an example of a few components that were used in the application, like Container, Row and Column components.

```
import Container from 'react-bootstrap/Container';
import Row from 'react-bootstrap/Row';
...

  <Container fluid style={{ backgroundColor: '#fbeec1' }}>
	<Row>
	  <div className="profile-header">
		<div className="profile-header__item_username">
		  User Profile - {user.email}
		</div>
		<div className="profile-header__item_credits">
		  Remaning Credits: {user.credits}
		</div>
	  </div>
	  <div className="comic-page">
		<h2>My Comics:</h2>
		<ComicsList comics={user.comicsofUser}/>
	  </div>
   </Row>
  </Container>
```

As mentioned above Redux was used for communicating with the server. 
Here is an example of fetching comics from the server to display to the user.

```
export const setComics = (comics) => ({
  type:'SET_COMICS',
  comics
});

export const startSetComics = () => {
  return (dispatch) => {
    return fetch("http://localhost:3001/comics",{
      method:'GET',
      headers:{
        'Content-Type': 'application/json',
        Accept: 'application/json'
      }
    })
    .then((response) => response.json())
    .then((data) => {
      if (data.comics) {
        dispatch(setComics(data.comics))
      }
    })
  }
}
```

And here is the reducer that changes the state.

```
const comicsReducerInitialState = [];

export default(state=comicsReducerInitialState,action) => {
  switch(action.type){
    case 'SET_COMICS':
      return action.comics;
    default:
      return state;
  }
}
```

Login and SignUp components handle their own local state and validation.

```
class SignUpPage extends React.Component {
  state = {
    email:"",
    password:"",
    password_confirmation:"",
    registrationError:""
  }
  componentWillUnmount(){
    this.props.cleanRegistrationMessages();
  }
...
```


For flash messages a new component called FlashMessage was created that displays messages to the user based on 
server's responses.

This was a challenging project and I learned a lot. In the future I intend to add new functionalities to the project as I gain 
a deeper understanding of React and Redux best practices.

