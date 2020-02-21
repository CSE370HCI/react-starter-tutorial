# Login and Signup

## Using the API

This is an exciting part of the tutorial, because we're going to use an API to contact the backend where authentication happens. The backend has been built for you, [you just need to learn how to use it!](https://docs.google.com/document/d/1kpNsYlPprNRpA7CbBTJ89_MLdDaKVMXt2BQIWPqazjA/edit#). There are a couple ways to send http requests in javascript, but we're going to use the ```fetch()``` method to accomplish this. In your ```submitForm()``` method, go ahead and add the following code underneath your validation. Make sure that if there are issues with the way the user filled out the form, the ```fetch()``` code doesn't execute.

```
        fetch("http://stark.cse.buffalo.edu/hci/SocialAuth.php", {
        method: "post",
        body: JSON.stringify({
            action: "register",
            username: this.state.username,
            email: this.state.email,
            password: this.state.password,

        })
        }).then(response => response.json())
        .then(json => {
            console.log(json);
        })

```

There is a lot going on here, but don't get overwhelmed. Its not as complicated as it looks. We're basically making a POST request to the endpoint located at the specified URL, and printing the response after we get one. Fetch takes in a URL and an object specifying what we want inside our request. Fetch returns a promise ([read about them here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)). They're a little bit tricky, so don't worry if they don't make sense right now. All you need to know is that we take the value returned from fetch and convert it to json. We then print it just to see what it looks like. Here's what you'd see if the response returns with a 200 ok status.

```
{message: "Account created.  A confirmation email has been sent."}
```

This is exciting news! We're gonna want to tell the user about it. There is no better way to accomplish this than with a modal. 