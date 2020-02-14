# Routing and Navigation

## Styling our navbar

Right now, our navbar is nothing more than a boring list. 

![basiclist](/assets/img/basiclist.png)

We need to add some css to make this look more user-friendly. Create a stylesheet called navbar.css, and import the stylesheet into navbar.js using the following code:

```
import './navbar.css'

```

 First, we're going to change the style of the list elements. We're going to make the display inline block, so that the elements are side by side and can have top padding and margins. If we just made them inline, we wouldn't be able to give the list elements padding on the bottom or top. We're also going to add some padding and change the font size.

 ```
li{
    display: inline-block;
    padding: 10px 20px 10px 20px;
    font-size: 18px;
}

 ```

 Now we're starting to see something that looks a little bit more like a navbar. Next, we can add a background to our navbar by styling the ul tag. In this demo, I'm going to make it black. We can then remove the underlines from the list items, as well as set the color to white for some good contrast.

 ```
 ul {
     background-color: black;
 }

 li a{
     text-decoration: none;
     color: white;
 }

 ```

When you see one type of hmtl tag after another in a css document (like * li a *), that means that the style rules will apply to all tags of the second type which are children of tags of the first type. More concretely, in this example, the style will apply to all anchor tags inside list-item tags.


![Advanced List](/assets/img/advancedlist.png)
Now our navbar is looking a little bit more appealing. The only problem is, when a user hovers over a navbar item, they expect to be able to see some feedback indicating that the link is clickable. We're going to need to add some styling to fix that.

```
li:hover{
    background-color: green;
}
```

:hover is an example of something called a selector. It allows you to selectively style elements only under certain conditions. In this case, we want to apply the background color only when the user hovers over the element with their cursor.

Now our navbar is looking production ready stylistically, but it doesn't do anything. In the next section we're going to look at how to leverage react routing to create a working navbar.