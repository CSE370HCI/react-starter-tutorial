# Part 3
## React Components

> Components are independent and reusable bits of code. They serve the same purpose as JavaScript functions, but work in isolation and returns HTML via a render function. (w3schools)

There are two types of React components, **Function** components, and **Class** components. The `App.js` we saw in the previous section was a Function component.

### Function Components
A function component is the simplest way of writing a React Component, however it is limited in some ways. A function component can accept "props" (properties), and will return a React Element.

**Example:**
For instance, the below React Component will take in properties as an Object. It then returns a `<h1></h1>` header saying hello!
```
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```

we can use this component with the following syntax
```
<Welcome name="Tristan">
```
> Not only can we hardcode a string for a name, but we can use any sort of variable here.

### Class Components
Class components use [JavaScript Classes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes) that were introduced in 2015. These components are much more powerful as they allow us to have stateful components.

For a basic Class component's syntax, we can recreate the above Function component as a Class component.

```
class Welcome extends React.Component {
    // Render is called when the Component is created, and any time the state updates.
    render() {
        return <h1>Hello, {this.props.name}</h1>;
    }
}
```

### React Props
All React components have "props" passed into them. Props are different properties that can take the form of any JavaScript type. For instance you can pass a function into a Component to handle when it is clicked, or pass in an object to populate certain user data. You can even pass in other React Components to your component!

Here is an example of a component with different prop types.

```
<MyExampleComponent
    myStringProp="Some String"
    myNumberProp={5}
    myBooleanProp={true}
    myFunctionProp={function() {
        console.log("I was called!");
    }}
>
    <p>Child component</p>
</MyExampleComponent>
```

[*React State: Part 4 ->*](part4.html)