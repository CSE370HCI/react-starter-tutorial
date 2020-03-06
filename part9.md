# Routing and Navigation


## React Routing Setup

Now that our navbar is all set stylistically, we need to set up react router. In order to do that, you're going to need to head over to your console and type in the following in the directory of your project.

```
npm install react-router-dom
```

Now that the router package is installed , we need to create some components that we can set our navbar to navigate to. Create 3 files, `login.js`, `register.js`, and `landing.js`. Throw some boiler code into these files to build basic components. Below is the boiler code for `register.js` to create the register component. Replace Register with Login and Landing for `login.js` and `register.js`, respectively.

```
import React from 'react';


export default Register = () => (<div> Register</div>)
```

 To do that, head over to your `App.js` file. Go ahead and import `Router`, `Route` and `Switch` from `react-router-dom`.

```
import {BrowserRouter as Route, Switch} from 'react-router-dom';
```
We're going to use these to tell React what component to render based on a URL inputted. The code below will render different components base on what is entered into the url bar. For example, if you enter `localhost:3000/register` you should see text that says register, because that's what your Register component registers. Below is some code that's going to do exactly what we want.

```
                <Router>
                <NavBar/>
                <Switch>
                    <Route exact path='/' component={Landing}/>
                    <Route exact path ='/register' component={Register}/>
                    <Route exact path ='/login' component={Login}/>
                </Switch>
                </Router>
```
So let's break this down. The Router tag is just a wrapper tag that Route tags must be contained inside of. The Switch tag tells react-router to redirect to the first URL that matches the inputted URL. It's like a switch statement that you're familiar with in your favorite programming language. Route tags specify exactly which component should be rendered based on the inputted path. We use the exact tag to tell react-router that we only want to redirect based on the exact url specified in path. If we didn't have *exact*, any path that starts with */* would cause the landing component to be rendered.

> Note: Make sure that the NavBar tag goes inside the router tag. We're going to add things to NavBar in the next section that need to be inside the Router tag.

In the next section, we're going to look at how we can connect the navbar to the URLs, so that the menu items act as links.

[Part 10 ->](part10.html)