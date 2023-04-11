---
title: Communicating between Independent Components
---

<Intro>

One of the best features of React is that it helps us build a componentized app. We can build smaller components, each with its own responsibility, and then combine them to create a complete app. Often these components need to communicate with each other to pass data around the app.

[We've learnt that React uses props to communicate between dependent components](/learn/passing-props-to-a-component). There are instances, however, when we might want to communicate between two independent components that don't have a common functionality to share data. In this guide, we will learn how to communicate between independent components using an event bus.

</Intro>

<YouWillLearn>

* How to create a native event bus
* How to use the event bus for communication

</YouWillLearn>

## Creating an Event Bus {/*creating-an-event-bus*/}

To communicate between two independent components in React, we have the flexibility to set up a global event-driven system, or a **PubSub** system. An **event bus** implements the PubSub pattern, allows us to listen and dispatch events from components, and so helps us to decouple our components and pass data using events fired from other components so that they don't have direct dependencies between each other.

An event bus has three methods:

1. **on**
2. **dispatch**
3. **remove**

```js
const eventBus = {
  on(event, callback) {
    // ...
  },
  
  dispatch(event, data) {
    // ...
  },
  
  remove(event, callback) {
    // ...
  },
};
```

In the `on()` method, attach an event listener to the **document** object. The `on` method will have two arguments: the event and the callback function. The callback function will be called when the event gets fired.

```js
// ...

on(event, callback) {
    document.addEventListener(event, (e) => callback(e.detail));
},

// ...
```

The `dispatch()` method will fire an event using the
[CustomEvent API](https://developer.mozilla.org/en-US/docs/Web/API/CustomEvent) along with some data.

```js
// ...

dispatch(event, data) {
    document.dispatchEvent(new CustomEvent(event, { detail: data }));
},

// ...
```

Lastly, the `remove()` method will remove the attached event from the document object to prevent memory leakage in app.

```js
// ...

remove(event, callback) {
  document.removeEventListener(event, callback);
},

// ...
```

## Using the Event Bus for Communication {/*using-the-event-bus-for-communication*/}

Now that we have created a custom event bus, it's time to use it to pass data between the components.

Let's say that we have two components: a **Coupon component** and a **Message component**. The Coupon component has a text field and a submit button. When the submit button is clicked, the component triggers a `couponApply` event along with a custom message. The Message component listens for the `couponApply` event and displays the message that is passed in the event.

<Pitfall>

We are using class components here. It is suggested to implement functional components instead.

</Pitfall>

```js
// Coupon Component

import eventBus from "./EventBus";

class Coupon extends Component {
  constructor(props) {
    super(props);
    this.state = {
      couponCode: "",
    };
  }

  applyCoupon = () => {
    console.log("applying");
    eventBus.dispatch("couponApply", { message: "coupone applied" });
  };

  render() {
    return (
      <div>
        <input
          value={this.state.couponCode}
          onChange={(e) => this.setState({ couponCode: e.target.value })}
        />
        <button onClick={this.applyCoupon}>Apply Coupon</button>
      </div>
    );
  }
}
```

The Message component listens to the event inside the `componentDidMount()` lifecycle method and use the `remove()` method inside the `componentWillUnmount()` method of the component. When the component unmounts from the DOM, React will clean up the event listener and avoid memory leakage, which can cause performance issues in the app.

```js
// Message Component

import eventBus from "./EventBus";

class Message extends Component {
  constructor(props) {
    super(props);
    this.state = {
      message: "",
    };
  }

  componentDidMount() {
    eventBus.on("couponApply", (data) =>
      this.setState({ message: data.message })
    );
  }

  componentWillUnmount() {
    eventBus.remove("couponApply");
  }

  render() {
    return <div>{this.state.message}</div>;
  }
}
```

<Recap>

Using an event bus to communicate between React components is not conventional, but it is useful when it comes to communication between _decoupled_ or _independent_ components. When working on extensive apps, we won't want to use a custom event bus, but instead rely on other libraries like **PubSub.js**, **[react-suber](https://www.npmjs.com/package/react-suber)** or **Redux**. Context API can also be used to pass data between components, but that requires additional wrapper components, which might make the component challenging to maintain.

</Recap>
