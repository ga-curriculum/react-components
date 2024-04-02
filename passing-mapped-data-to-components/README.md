# ![React Components - Passing Data Between Components](./assets/hero.png)

**Learning objective:** By the end of this lesson, learners will be able to understand and implement the concept of passing data between components in React using `props` inside of a `map()`.

## Dynamically rendering components with props

We have three founders to list on our site, so passing individual `props` values does not allow us to programmatically render the data from our `extremelyImpressiveFounders` array. For this, we'll need to create a loop in our JSX to dynamically render data from our list.

Let's refactor `App.jsx` to include a mapped list of `FounderListItem` components:

```jsx
// src/App.jsx

const App = () => {
  return (
    <>
      <Navbar />
      <main>
        <h1>Welcome to Hyperbo.ly</h1>
        <h2>The future is firmly in front of us!</h2>
        <p>If you can't explain it to a fifth-grader, our product does it.</p>
      </main>
      <h2>Our Founders</h2>
      <ul>
        {extremelyImpressiveFounders.map((founder, index) => (
          <FounderListItem
            key={index}
            name={founder.name}
            title={founder.title}
            credential={founder.credential}
          />
        ))}
      </ul>
    </>
  );
};
```

> Reminder: When we use the `.map()` method in React to create a list of components, like our `FounderListItem` components, it's essential to give each one a unique `key` prop. This `key` helps React keep track of each item in the list. Specifically, it's used for identifying which items have changed, been added, or been removed. This is crucial for performance, especially when dealing with dynamic lists that might get updated or reordered.

We should now see our founders rendered to the page dynamically from our array. Great work!

## Consolidating our `props`

Currently, there are only three properties listed for each object of the `extremelyImpressiveFounders` array- `name`, `title` and `credential`. We are passing these down individually as `props` to each `FounderListItem` component. Three is a manageable number, but imagine if there were 20 or more, how does this scale?

Our list of `props` passed to `FounderListItem` would soon become unmanageably large in our JSX.

```jsx
<FounderListItem
  key={index}
  name={founder.name}
  title={founder.title}
  credential={founder.credential}
  // probably many more!
/>
```

Let's refactor our `.map()` function one more time for a more scalable `prop` structure:

```jsx
// src/App.jsx

<ul>
  {extremelyImpressiveFounders.map((founder, index) => (
    <FounderListItem key={index} founder={founder} />
  ))}
</ul>
```

This requires one more change to the `FounderListItem` component:

```jsx
// src/FounderListItem.jsx

const FounderListItem = ({ founder }) => {
  return (
    <li>
      <h3>
        {founder.name} : {founder.title}
      </h3>
      <p>{founder.credential}</p>
    </li>
  );
};
```

Much better!

## 🚀 Level Up: JS spread syntax

If you want to avoid refactoring `FounderListItem` and prefer not having to access properties as `founder.something`, JavaScript has one more tool to simplify passing multiple `props` as a bundle - the spread operator  `...`.

The spread operator `...` in JavaScript is a convenient way to pass ***all the properties*** of an object as `props` to a React component.

```jsx
const App = () => {
  return (
    <>
      <Navbar />
      <main>
        <h1>Welcome to Hyperbo.ly</h1>
        <h2>The future is firmly in front of us!</h2>
        <p>If you can't explain it to a fifth-grader, our product does it.</p>
      </main>
      <h2>Our Founders</h2>
      <ul>
        {extremelyImpressiveFounders.map((founder, index) => (
          <FounderListItem key={index} {...founder} />
        ))}
      </ul>
    </>
  );
};
```

In the `App` component, when you use the spread operator for `{...founder}`, what you're doing is essentially taking each key-value pair from the founder object and passing them as separate props to the `FounderListItem` component.

When used with a component like `FounderListItem`, it allows us to maintain a clean and concise syntax while still being able to individually access each property within the component.

```jsx
const FounderListItem = ({name, title, credential}) => {
  return (
    <li>
      <h3>
        {name}: {title}
      </h3>
      <p>{credential}</p>
    </li>
  );
};
```

In the `FounderListItem` component, you are able to define concise parameters like `{name, title, credential}`. These directly correspond to the keys in the founder object. By using object destructuring, you're able to extract each of these properties from the `props` object.
