# ![React Components - Destructring Props](./assets/hero.png)

tktk Hunter, could you update this hero?

**Learning objective:** By the end of this lesson, learners will be able to understand how and why to destructure props in React.

## Destructuring

The work we've done so far is great, but you'll notice that whenever we want to access a property on the `founder` object we have to navigate through `props` over and over to get the data we need. There's nothing necessarily ***wrong*** with this, but you can imagine how this might become tedious, especially if we had even more objects nested inside of the `founder` object.

This is where [object destructuring](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment#object_destructuring) comes into play.

At its simplest, object destructuring allows you to assign a property of an object to a variable of the same name. Let's see it in action. Here's our existing `FounderListItem` component:

```jsx
// src/components/FounderListItem/FounderListItem.jsx

const FounderListItem = (props) => {
  return (
    <li>
      <h3>Hello, I'm {props.founder.name} the {props.founder.title}!</h3>
      <p>{props.founder.credential}</p>
    </li>
  );
};

export default FounderListItem;
```

We'll start with the destructuring itself, which happens in the first line. Change it to:

```jsx
const FounderListItem = ({founder}) => {
```

This syntax means: find the `founder` property on the first argument, and assign it to `founder`. `founder` now has all the properties that `props.founder` previously had. Note that there is no longer a `props` parameter available to use in this component, which means we need to do a slight refactor in this component:

```jsx
// src/components/FounderListItem/FounderListItem.jsx

const FounderListItem = ({founder}) => {
  return (
    <li>
      <h3>Hello, I'm {founder.name} the {founder.title}!</h3>
      <p>{founder.credential}</p>
    </li>
  );
};

export default FounderListItem;
```

All better! Again, destructring isn't something you're required to do, but it's a common pattern used in documentation

## Retaining access to `props`

It's not uncommon to want to retain access to everything passed on `props`, but still destructure some things from it. The below syntax can accomplish this:

```jsx
// src/components/FounderListItem/FounderListItem.jsx

const FounderListItem = (props) => {
  const { founder } = props
  return (
    <li>
      <h3>Hello, I'm {founder.name} the {founder.title}!</h3>
      <p>{founder.credential}</p>
    </li>
  );
};

export default FounderListItem;
```

`props` is now available to use throughout the `FounderListItem` component, but `founder` has been destructured as well so that it's still easy to access its properties.

> 🧠 Destructuring isn't just for React applications! This syntax is built into JavaScript, and you can use it in any modern JavaScript app.
