---
layout: post
title:  "Gun.js: The Best Solution for React State Management"
date:   2021-9-27 01:37:00 +0000
tags: software
published: true
description: "Better alternative to Redux"
image: https://siriusbusiness.fi/assets/images/posts/cheesecake.jpg
---

Fed up with writing a ton of Redux boilerplate just to make a form input editable?

There’s a better alternative: Gun.js. It makes state synchronization and persistence super easy.

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
class CommentForm extends React.Component {
    constructor() {
        super();
        this.state = {comment:''};
    }
    componentDidMount() {
        State.get('comment').on(comment => this.setState({comment}));
    }
    
    onInput(e) {
        State.get('comment').put(e.target.value);
    }
    
    render() {
        return (
            <form class="box">
                <input placeholder="Type something" type="text" value={this.state.comment} onChange={e => this.onInput(e)} />
            </form>
        );
    }
}
```

Now you have a comment form that syncs its content across component instances and persists it in localStorage.

See the working example on [Codepen](https://codepen.io/mmalmi/pen/VwWVdKG).