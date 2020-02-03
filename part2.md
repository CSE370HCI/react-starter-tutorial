# Part 2
## Understanding The Starter Code

The code produced in the previous section provides us with a fully functioning webpage. However, it's important for us to understand what is happening so we can expand on our website!

Let's start by looking inside the `src` directory that was generated, we see a few files. We'll be paying the most attention to `App.js`, `App.css`, `index.js`, and `index.css`.

Now let's open up `index.js` and look at the content inside.

**index.js:**
```
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';
import App from './App';
import * as serviceWorker from './serviceWorker';

ReactDOM.render(<App />, document.getElementById('root'));

// If you want your app to work offline and load faster, you can change
// unregister() to register() below. Note this comes with some pitfalls.
// Learn more about service workers: https://bit.ly/CRA-PWA
serviceWorker.unregister();
```

The first five lines import various things.
- `React` and `ReactDOM` are essential for running and rendering React.
- `index.css` is the stylesheet that contains some of our page's styles. 
- `App` is a React component we declare in the file `App.js` (more about this later).
- `serviceWorker` we won't be looking at this file at all. However you're welcome to learn more about it on your own!

The line containing `ReactDOM.render` takes our React component and renders it into our HTML. This is the line of code that connects all of our React components to our HTML.

Next let's take a look at the `App.js` file.

**App.js**
```
import React from 'react';
import logo from './logo.svg';
import './App.css';

function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p>
          Edit <code>src/App.js</code> and save to reload.
        </p>
        <a
          className="App-link"
          href="https://reactjs.org"
          target="_blank"
          rel="noopener noreferrer"
        >
          Learn React
        </a>
      </header>
    </div>
  );
}

export default App;
```

This is our first look at a React Component! We'll go over these more in detail shortly. If you're familiar with HTML or JavaScript, you can see that this is a weird combination of the two. This is called JSX (JavaScript XML) and is how we will be writing React Components.

[*GO TO PART 3 ->*](part3.html)
