# Part 4
## React State

React Component's have a built in state. This state can be updated by using `this.setState()`. Whenever a component's state is updated, it will re-render the component. This ensures your component is always up-to-date with it's current state.

Let's create a simple component that allows the user to click a button to increment a number, then let's display that number on the page. Because we are going to be using a state, we'll want to have a Class component.

Let's start by replacing our `App.js` with a new component. We can start with the following code in `App.js`.

```
// We need to import React so we can create a React component
import React from 'react';

// Here is how we will create a new Class component. Named App.
class App extends React.Component {
    // The constructor is run when the component is first created
    constructor() {
        super();

        // This is our initial state for our component. Notice `count` is defaulted to 0.
        this.state = {
            count: 0
        };

        this.incrementCounter.bind(this);
    }

    // here we create a new method to add one to our state
    incrementCounter() {
        // get the old count
        const count = this.state.count;

        // set the count in our state to count+1
        this.setState({
            count: count+1
        });
    }

    // `render` is called every time our state changes. So every time we update it
    render() {
        const count = this.state.count;

        // return the current count in JSX to be displayed on the page
        // also display a button that will call incrementCounter()
        return (
            <div>
                <h1>The current count is {count}</h1>
                <button onClick={() => this.incrementCounter()}>Increment Counter</button>
            </div>
        );
    }
}

export default App;
```


[*GO TO PART 5 ->*](part5.html)