# Login and Signup

## Frontend validation

There are a couple of things that we need to do to make sure the user has a good experience filling out this form. In order to do any sort of validation, we have to create a method that handles submission. Add the following to your react component.

```
 submitForm(e){
        e.preventDefault();

        return False;
    }
```
Just like with the ```handleChange()``` method, ```submitForm()``` accepts an event object. Here we call ```preventDefault``` in order to prevent the page from refreshing, which happens by default when a form is submitted. 

The first thing we want to check is whether or not the passwords that were entered by the user match eachother. If they don't, we want to display a message to the user telling them to correct their behavior. The first thing we need to do to accomplish this is add some code in ```submitForm()``` to make this check. Add the following code between ```e.preventDefault()``` and the return statement.

```
if(this.state.password!=this.state.password2){
            this.setState({
                passwordError: true
            })
        }

```
Here, we're checking to see if the passwords in our Register component's state are equal, and if they are not, setting passwordError to true. speaking of password error, make sure to add passwordError to the initial state object that you created in the constructor. Set the value to false, because by default there are no password errors. 

So now we have a variable that knows when we want to render an error message, but we don't have anything to render based on that variable. Hopefully you're seeing that we need a way to conditionally render an html element based on a component's state. There are a ton of ways to do this ( [Check this documentation if you're curious.](https://reactjs.org/docs/conditional-rendering.html) ), but unfortunately we're going to have to pick one. 

Remember that JSX can be used to insert many (if not any) javascript expression into your pre-rendered html-ish code. We're going to use a nifty javascript trick to conditionally render an element. Add the following code to the return value of your render function.

```
   {this.state.PasswordError &&
                <label style={{color: 'red'}}>Error, passwords don't match</label>
    }

```

First of all, just note that I didn't put much effort into the styling here, I just added inline styling to make the text red because HCI. Anyway, here we have some JSX containing what is essentially a boolean expression. In javascript, if we have two expressions, a && b, javascript will not evaluate b if a is falsy. This means that the label element will not be rendered unless the passwordError variable evaluates to false.

Now you should be able to test your code. Enter in two mismatched passwords and see what happens. Hopefully, you'll see your error message appear. As an exercise, try to make error messages for other things that the user might want to know when he or she doesn't fill out the form correctly.

In the next section, we're going to make the API call that will register a user. Successful registration will cause a modal to pop up (something that might be useful to know when developing in react.)

[Part 14 ->](part14.html)