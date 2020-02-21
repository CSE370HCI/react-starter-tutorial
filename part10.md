#Routing and Navigation

##Connecting the router to your navbar

You might be familiar with the classic &lt; a &gt;  tag from standard html. *react-router* uses something called a link tag to do exactly what an <a> tag does. In order to finish our navbar, we're going to need to add some link tags to the NavBar component. Head over to navbar.js and replace the stuff inside your <ul> tags to render the following:

```
          <nav>
            <ul>
                <li><Link to="/">Home</Link></li>
                <li><Link to='/register'>Register</Link></li>
                <li><Link to='/login'>Log In</Link></li>
            </ul>
            </nav>
```

Now, each list item will serve as a link. When the user clicks on a menu-item, a request will be made to render the component tied to the path specified.

Now your navigation bar works as expected!! The next step to this app is building login and signup, so that's what we're going to build in the next section.