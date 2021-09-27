---
layout: post
title:  "Gun.js: Painless React State Management"
date:   2021-9-27 01:37:00 +0000
tags: software
published: true
description: "Better alternative to Redux"
image: https://siriusbusiness.fi/assets/images/posts/painless.jpg
---

![I feel no pain](/assets/images/posts/painless.jpg)

Fed up with writing a ton of Redux boilerplate just to handle form input changes?

There’s a better alternative: [Gun.js](https://github.com/amark/gun). It makes state synchronization and persistence a breeze.

First, initialize Gun with options that make sure the state is synced with localStorage only (not with peers).
```jsx
const State = new Gun({
    localStorage: true,
    file: 'State.local', // localStorage key
    multicast: false, // on Node.js, Gun would sync with local area network peers over multicast :)
    peers: [] // this time we don't want to sync with other users
}).get('state');
```

Then create a React component that uses the state:

```jsx
class TextInput extends React.Component {
    state = {text:''};
    
    componentDidMount() {
        State.get('text').on(text => this.setState({text}));
    }
    
    onInput(e) {
        State.get('text').put(e.target.value);
    }
    
    render() {
        return (
            <form class="box">
                <input placeholder="Type something" type="text" value={this.state.text} onChange={e => this.onInput(e)} />
            </form>
        );
    }
}
```

Now you have a text form that syncs its content across component instances and persists it in localStorage.

See the working example on [Codepen](https://codepen.io/mmalmi/pen/VwWVdKG).

However, if we now unmount the component and write to `State.get('text')` elsewhere, we'll get the warning: `Can't call setState on an unmounted component. This is a no-op, but it indicates a memory leak in your application.`

We can avoid that by saving our state subscriptions and unsubscribing them in `componentWillUnmount()`. Here's a helper class for that:

```jsx
class BaseComponent extends React.Component {
    subscriptions = {};
    
    subscribe(callback, path) {
        return (value, key, x, subscription, f) => {
            if (this.unmounted) {
                subscription && subscription.off();
                return;
            }
            this.subscriptions[path || key] = subscription;
            callback(value, key, x, subscription, f);
        }
    }
    
    inject(name, path) {
        return this.subscribe((v,k) => {
            const newState = {};
            newState[name || k] = v;
            this.setState(newState);
        }, path);
    }
    
    componentWillUnmount() {
        this.unmounted = true;
        Object.keys(this.subscriptions).forEach(k => {
            const subscription = this.subscriptions[k];
            subscription && subscription.off();
            delete this.subscriptions[k];
        });
    }
}
```

Now we can extend BaseComponent, which takes care of injecting values to the component's state and unsubscribing on unmount.

```jsx
class TextInput extends BaseComponent {
    // ...
    componentDidMount() {
        State.get('text').on(this.inject());
    }
    // ...
}
```

[Codepen](https://codepen.io/mmalmi/pen/MWozPZE)

Upcoming: How to sync your application state with the world.