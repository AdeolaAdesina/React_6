# props

When thinking in the frame of a React application, components are small pieces of a whole. Together, they make up the interface that users will see.

With each component playing a role in the interface, there are times when components must be able to communicate with other components.

In this lesson, you will learn another way that components can interact: a component passing information to another component.

Information that gets passed from one component to another is known as props.

Props can be used to customize the output of each component depending on the information that is passed in.

By allowing components to communicate with each other, we can add a level of flexibility that was not possible before.

By the end of this lesson, you should be able to:

- Pass, access, and display props.
- Use props to create conditional statements.
- Define event handlers in a component and pass them to other components.
- Work with a component’s children.
- Assign default values to props.
- Let’s get started!



## Access a Component's props

Every component has something called props.

A component’s props is an object. It holds information about that component.

You’ve seen this before, but you might not have realized it! Let’s take a look at the HTML button tag. There are several pieces of information we can pass to the button tag, such as the type of the button.

```
<button type="submit" value="Submit"> Submit </button> 
```

In this example, we’ve passed two pieces of information to the button tag, a type and a value. Depending on what type attribute we give to the <button> element, it will treat the form differently. In the same way, we can pass information to our own components to specify how they behave!

Props serve the same purpose for components as arguments do for functions.

To access a component’s props object, you can reference the props object and the dot notation for its properties. Here’s an example:

```
props.name
```


Instructions:

1.

Look at PropsDisplayer.js.

This component has props as a part of its parameter.

Inside the function body, there is a stringProps variable which contains the string data of props.

Let’s display it on the screen and see what’s inside by injecting the stringProps variable between the <h2></h2> tags.

This would retrieve the name property from the props object.

2.

Now that we’ve finished the PropsDisplayer component, let’s use it in our top-level component, App, and have it render to the screen.

Open up App.js. Take a look at the App component definition, and have it return the PropsDisplayer component.

As always, App is exported to index.js and rendered.


3. 

3.
Click Run and think about what you see. If you’re seeing an empty object, you’re on the right track. The props object isn’t really empty. It has some properties that JSON.stringify() doesn’t detect. But even if you could see those properties, the props object still wouldn’t have much to show you right now.


![Screenshot 2023-11-17 at 06 21 59](https://github.com/AdeolaAdesina/React_6/assets/29931071/59f79201-b17c-4a65-a1f1-338dbbf65a4f)

![Screenshot 2023-11-17 at 06 22 04](https://github.com/AdeolaAdesina/React_6/assets/29931071/dbc1bd7b-0914-490a-8ece-a87c83c68d51)




## Pass props to a Component

To take advantage of props, we need to pass information to a React component. In the previous exercise, we rendered an empty props object because we did not pass any props to our PropsDisplayer component.

How do we pass props? By giving the component an attribute:

```
<Greeting name="Jamel" />
```

Let’s say that you want to pass a component the message, "We're great!". Here’s how you can do it:

```
<SloganDisplay message="We're great!" />
```

As you can see, to pass information to a component, you need a name for the information that you want to pass.

In the above example, we used the name message. You can use any name you want.

If you want to pass information that isn’t a string, then wrap that information in curly braces. Here’s how you would pass an array:

```
<Greeting myInfo={["Astronaut", "Narek", "43"]} />
```

In this next example, we pass several pieces of information to ```<Greeting />```. The values that aren’t strings are wrapped in curly braces:

```
<Greeting name="The Queen Mary" city="Long Beach, California" age={56} haunted={true} />
```

Instruction:

Inside the App top-level component, find the line where we call the PropsDisplayer component.

Modify this line so that PropsDisplayer is called with a prop named myProp and the string value "Hello".


![Screenshot 2023-11-17 at 06 22 04](https://github.com/AdeolaAdesina/React_6/assets/29931071/15bd1777-28e1-4feb-8307-f7ca4bc3895b)

![Screenshot 2023-11-17 at 06 27 06](https://github.com/AdeolaAdesina/React_6/assets/29931071/07c76ac2-49e7-45c5-b56b-b0a1f7eda75a)


## Render a Component's props

Props allow us to customize the component by passing it information.

We’ve learned how to pass information to a component’s props object. You will often want a component to display the information that you pass.

To make sure that a function component can use the props object, define your function component with props as the parameter:

```
function Button(props) {
  return <button>{props.displayText}</button>;
}
```

In the example, props is accepted as a parameter, and the object values are accessed with the dot notation accessors pattern (object.propertyName).

Alternatively, since props is an object, you can also use destructuring syntax like so:

```
function Button({displayText}) {
  return <button>{displayText}</button>;
}
```


Example:

![Screenshot 2023-11-17 at 06 33 06](https://github.com/AdeolaAdesina/React_6/assets/29931071/d292a328-efd9-4d82-89cc-8729eca585db)

![Screenshot 2023-11-17 at 06 33 10](https://github.com/AdeolaAdesina/React_6/assets/29931071/20a4e800-e833-4a56-937c-b4031984cef0)



## Pass props From Component To Component
You have learned how to pass a prop to a component:

```
<Greeting firstName="Esmerelda" />
```

You have also learned how to access and display a passed-in prop:

```
return <h1>{props.firstName}</h1>;
```

The most common use of props is to pass information to a component from a different component.

Props in React travel in a one-way direction, from the top to bottom, parent to child.

Let’s explore the parent-child relationship of passing props a bit further.

```
function App() {
    return <Product name="Apple Watch" price = {399} rating = "4.5/5.0" />;
}
```

In this example, App is the parent and Product is the child. App passes three props to Product (name, price, and rating), which can then be read inside the child component.

Props passed down are immutable, meaning they cannot be changed. If a component wants new values for its props, it needs to rely on the parent component to pass it new ones.

Let’s practice this!


Example:

![Screenshot 2023-11-17 at 06 42 21](https://github.com/AdeolaAdesina/React_6/assets/29931071/b575d3cb-557a-4165-8958-fc9e86aaddd0)

![Screenshot 2023-11-17 at 06 42 24](https://github.com/AdeolaAdesina/React_6/assets/29931071/c6e9ba5e-7ffd-4e42-9f51-4562be92f1b4)



## Render Different UI Based on props

You can do more with props than just display them. You can also use props to make decisions.

```
function LoginMsg(props) {
  if (props.password === 'a-tough-password') {
    return <h2>Sign In Successful.</h2>
  } else {
    return <h2>Sign In Failed..</h2>
  }
}
```

In this example, we use the props passed in to make a decision rather than rendering the value to the screen.

If the password received is equal to 'a-tough-password', the resulting message in <h2></h2> will be different!

The passed-in password is not displayed in either case! The prop is used to decide what will be displayed. This is a common technique.



Example:

![Screenshot 2023-11-17 at 06 48 53](https://github.com/AdeolaAdesina/React_6/assets/29931071/bff865b4-924d-4f68-84a1-3db1f3f010d1)

![Screenshot 2023-11-17 at 06 48 58](https://github.com/AdeolaAdesina/React_6/assets/29931071/bd7f093d-f12d-4f83-8da4-60b726282d11)




## Put an Event Handler in a Function Component

You can, and often will, pass functions as props. It is especially common to pass event handler functions.

In the next exercise, we will pass an event handler function as a prop. However, we have to define an event handler before we can pass one anywhere. In this exercise, we will define an event handler function.

How do we define an event handler in React?

We define an event handler as a method on the function component!

Take a look at the Example.js file in the code editor. On lines 4 through 8, an event handler method is defined. On line 10, that event handler method is attached to an event (a click event, in this case).


![Screenshot 2023-11-17 at 06 56 17](https://github.com/AdeolaAdesina/React_6/assets/29931071/4ed57ac9-566f-4fd2-ae79-fcb74208725a)

![Screenshot 2023-11-17 at 06 56 20](https://github.com/AdeolaAdesina/React_6/assets/29931071/b1ce9b0f-fdac-4863-a72c-9787e782aa89)




## Receive an Event Handler as a prop

Great! You just passed a function from ```<Talker />``` to ```<Button />```.

Take a look at Button.js in the code editor. Notice that Button returns a <button> element.

If a user clicks on this <button> element, you want your passed-in talk() function to get called. This means that you need to attach talk() to the <button> element as an event handler.

How do you do that? In the same way that you attach any event handler to a JSX element: you give that JSX element a special attribute. The attribute’s name should be an event name like onClick or onHover. The attribute’s value should be the event handler that you want to attach.


![Screenshot 2023-11-17 at 07 04 43](https://github.com/AdeolaAdesina/React_6/assets/29931071/91adc2e8-dc27-426b-bf40-565676fe2c77)

![Screenshot 2023-11-17 at 07 04 47](https://github.com/AdeolaAdesina/React_6/assets/29931071/1bcae52e-c085-45a6-9ef1-63abf01f6428)




## handleEvent, onEvent, and props.onEvent

Let’s talk about naming things.

When you pass an event handler as a prop, as you just did, there are two names that you have to choose. Both naming choices occur in the parent component, the component that defines the event handler and passes it.

The first name that you have to choose is the name of the event handler itself.

Look at Talker.js, lines 5 through 11. This is our event handler. We chose to name it talk.

The second name that you have to choose is the name of the prop that you will use to pass the event handler. This is the same thing as the attribute name.

For our prop name, we also chose talk, as shown on line 12:

```
return <Button talk={talk} />;
```

These two names can be whatever we want. However, there is a naming convention that is commonly used.

Here’s how the naming convention works: first, think about what type of event you are listening for. In our example, the event type was “click”. If you are listening for a “click” event, then you name your event handler handleClick. If you are listening for a “hover” event, then you name your event handler handleHover:

```
function myClass() {
  function handleHover() {
    alert('I am an event handler.');
    alert('I will be called in response to "hover" events.');
  }
}
```

Your prop name should be the word on, plus your event type. If you are listening for a “click” event, then you name your prop onClick. If you are listening for a “hover” event, then you name your prop onHover:

```
function myClass(){
  function handleHover() {
    alert('I am an event handler.');
    alert('I will listen for a "hover" event.');
  }
   return <Child onHover={handleHover} />;
}
```


![Screenshot 2023-11-17 at 07 10 41](https://github.com/AdeolaAdesina/React_6/assets/29931071/aa99fdf4-2733-4bda-a181-d9e5b02fc2c1)

![Screenshot 2023-11-17 at 07 10 45](https://github.com/AdeolaAdesina/React_6/assets/29931071/b8fdb827-2263-4ef6-aa16-faf1f98c5095)


