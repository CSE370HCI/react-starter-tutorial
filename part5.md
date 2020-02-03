# Part 5
## Making API Requests

Now that we have the basics of creating a Component, we can take that and make a more interactive component. Let's start by getting a list of users and displaying them on our screen. Once we've made this call, we can display all the users on the screen.

First, let's create a component for our new Users List.

```
import React from "react";

export default class UsersList extends React.Component {
  constructor(props) {
    super(props);
  }

  render() {
    return (
      <div>
      </div>
    );
  }
}
```

We start with an empty component, next we can add in the initial state to our `constructor`. It now becomes
```
constructor(props) {
  super(props);

  this.state = {
    allUsers: [],
  };
}
```

This initalizes an empty array to hold our user objects. Now we need to make the API call to get all users. We want to make this request once our component has mounted. We can use React's `componentDidMount` to run some code once our component is all ready and rendered. Let's add this right below our `constructor`.

```
componentDidMount() {
  // make a request to our API and get all of the users
  fetch("http://stark.cse.buffalo.edu/hci/usercontroller.php", {
    method: "POST",
    body: JSON.stringify({
      action: "getUsers"
    })
  })
    .then(response => response.json())
    .then(json => {
      // when we recieve a response, set the users state to our return value.
      this.setState({
        allUsers: json.users
      })
    });
}
```

Now all that needs to be done is display our users. We will do this in our `render` method. For our tutorial, we'll simply display the user's name and username.

```
render() {
  // get all users from our state
  const allUsers = this.state.allUsers;

  // We map all users to React elements for displaying them on the page.
  return (
    <div>
      {allUsers.map(user => {
        return (
          <div className="user" key={user.user_id}>
            <p>Username: {user.username}</p>
            <p>Name: {user.name}</p>
            <hr />
          </div>
        )
      })}
    </div>
  );
}

```

For this component's complete code, visit [this GitHub Gist](https://gist.github.com/TristanWiley/e05c5063a76ae0256724cbf8622f0796)

[*GO TO PART 6 ->*](part6.html)