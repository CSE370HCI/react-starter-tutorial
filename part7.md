# Routing and Navigation
## Creating the navbar

In previous sections of this tutorial, we discussed what a functional component was. We're going to create a navbar component as a functional component in this section of the tutorial. 

Let's start by creating a new file called 'navbar.js'. Inside this file, add the following skeleton code for our navbar component. Most of what you see should be familiar, so make sure to review earlier parts of the tutorial if anything here looks foreign to you.

```
import React from 'react';


const NavBar = () => {
    return (
            <nav>
            <ul>
                <li>List item 1</li>
                <li>List item 2</li>
                <li>List item 3</li>
            </ul>
            </nav>
    );
}
export default NavBar;
```

Let's go ahead and see what this looks like. Head over to your App.js file to get the ball rolling. Make sure to import the component first. Next, replace the child elements of the parent div tag with the newly-created Navbar component. Your app.js code should look like this:

```
// We need to import React so we can create a React component
import React from 'react';
import NavBar from './navbar';

// Here is how we will create a new Class component. Named App.
class App extends React.Component {
 

    render() {
        return (
            <div>
                <NavBar/>
            </div>
        );
    }
}

export default App;
```

For now, you will just see a simple list. That's fine. We're going to use CSS in the next section to make that look a lot prettier.
