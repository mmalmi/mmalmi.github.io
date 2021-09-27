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

There’s a better alternative: Gun.js. It makes state synchronization and persistence super easy:

```js
// Initialize Gun with options to make sure that the state is synced only locally
const State = new Gun({multicast: false, peers: [], localStorage: true, file: ‘State.local’});

class CommentForm {
    componentDidMount {
        State.get(‘comment’).on(comment => this.setState({comment}));
    }
    
    onInput(e) {
        State.get(‘comment’).put(e.target.value);
    }
    
    render() {
        return {
            <form>
                <input type=”text” value={{this.state.comment}} onInput={e => this.onInput(e)} />
            </form>
        }
    }
}
```

Now you have a comment form that automatically persists its content.