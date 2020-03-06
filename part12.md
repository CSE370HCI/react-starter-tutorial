# Login and Signup

## Actual react stuff!!

Our registration form looks really good from a stylistic perspective. We need to actually make it work! We will capture the data inputted into the form fields by adding it to the Register Component's state. To initialize state, we will override the component's constructor method and add a state object to our class. Add this code to your Register class:

```
constructor(props){
    super(props);
    this.state = {
        username: '',
        email: '',
        password: '',
        password2: ''
    }
}

```
If you don't know what's going on here, you may want to look back at previous parts of the tutorial. We're basically adding state for each field in our form, and we're going to update them as necessary.


 Next, we'll create a method that will be called every time the user inputs data into the form. Add the following method to your class:

```
 handleChange(e){
        this.setState({
            ... this.state,
            [e.target.name]: e.target.value
            
        });
    }

```

I chose the arbitrary name handleChange for this method; the name here doesn't matter. The method takes in an event object. You can [read more about event objects here.](https://www.w3schools.com/jsref/obj_event.asp). The event object will contain data about the element that triggered the function call. Specifically, e.target.name will contain the name of the element (something we have to add!), as well as the value that the element contains (whatever the user inputs).  

So now we have a function, but nobody is calling it. We can type whatever we want into our form, but we're not going to be able to do what we want with it yet. Let's call the handleChange function from each input. We're also going to need to add a name attribute, so that the event object passed into the function knows how to refer to the input.

```
            <div className="form">
            <h1>Register</h1>
            <form>
            <label> Username</label>
            <input name='username' type='text'onChange={e => this.handleChange(e)} required></input>
            <label> Email</label>
            <input name='email' type='email' onChange={e => this.handleChange(e)} required></input>
            <label> Password</label>
            <input name='password' type='password' onChange={e => this.handleChange(e)} required></input>
            <label> Verify Password</label>
            <input name ='password2' type='password' onChange={e => this.handleChange(e)} required></input>
            <button>Submit</button>
            </form>
        </div>
```

At this point, things are going pretty well. Our input elements are listening for changes, and will call our handleChange method every time. In turn, the state is updated each time the user inputs characters into the field. 


Before we start sending data to the backend, we should probably do some frontend validation. In the next section we'll discuss how to accomplish this.