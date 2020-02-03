# Part 6
## Styling Your Components

There are multiple ways to style your components. If you are familiar with web development, you might may at first think about inline-styling your components. While this is possible, it's slightly different in React.

For instance, if we wanted to set the background color of a `div` to #0090C1, we can do this by setting the `style` prop for the element.

```
<div style={
  {
    backgroundColor: "0090C1"
  }
}></div>
```
> Notice: The `style` prop takes in an Object with all of the element's styles. Rather than the CSS property being `background-color` as you might be familiar in CSS, it is written in camel case as `backgroundColor`.

Another way to style components is by using traditional CSS files. For instance, if we created a CSS file called `UsersList.css` and entered the following CSS:

```
.user {
  background-color: #0090C1;
  color: white;
  padding: 10px 25px;
  border-radius: 15px;
  width: fit-content;
  margin-top: 1rem;
}

.user * {
  margin: 0;
}
```

then import our stylesheet with the following code:

```
import './UsersList.css'
```

> Note when using classes in React. There is no `class` attribute for elements, to set the class of an element you'll need to use `className`.

Our users should now have a slightly more appealing style to them.

[A more in depth discussion of component styling](https://www.w3schools.com/REACT/react_css.asp)

[Head to the Conclusion ->](conclusion.html)