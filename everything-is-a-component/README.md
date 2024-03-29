# ![React Components - Everything is a Component](./assets/hero.png)

**Learning objective:** By the end of this lesson, learners will be able to break down a React component into smaller parts and understand the concept of passing `props` from a parent component to a grandchild component.

## Breaking the `App` into smaller components

The most modular, reusable, parts of our web page have now been turned into components. Could we do more?

In this section, we'll explore how to refine our React components even further. We'll take our `Navbar` component and break it down into smaller components - specifically, individual `NavLink` components. This exercise will help us understand how to pass data through multiple levels of components in React.

## Refactor the `Navbar` list

While the items in the navbar are unlikely to change and are typically okay to hard-code, let's use the opportunity to practice this pattern of refactoring lists into separate components. The goal is to refactor the list of links in the `Navbar` to use the same mapping pattern as our list of founders.

Add the following array to `App.jsx` and practice passing it down as props into `NavBar`. Each object will represent a link with an `href` and `text`:

```jsx
// src/App.jsx

const navLinks = [
  { href: "/", text: "Home" },
  { href: "/about-us", text: "About Us" },
  { href: "/money-pit", text: "Investment Opportunities" },
  { href: "/the-fine-print", text: "Terms of Service" },
];

const App = () => {
  return (
    <>
      <Navbar links={navLinks} />
      {/* rest of the App components */}
    </>
  );
};
```

## 🎓 You Do : Create a `NavLink` component

Let's create a new component, `NavLink`, which will be responsible for rendering a single navigation link. This component will receive the props `{href, text}` from our `NavBar` component.


## Render the `NavLink` components

Now, let's modify the `Navbar` component to accept the links `prop` and use it to render the individual `NavLink` components:

```jsx
// src/Navbar.jsx

const Navbar = ({ links }) => {
  return (
    <nav id="top-navbar">
      {links.map((link, index) => (
        <NavLink key={index} href={link.href} text={link.text} />
      ))}
    </nav>
  );
};
```

Great Work! We've successfully passed our link data from the `App` component to the `Navbar` component, and then to each `NavLink` component. This demonstrates a two-level `prop` passing pattern in React, where data flows from a parent component to a child, and then to a grandchild component.

## How many is too many?

Was it necessary to refactor the static navbar list items into their components? Probably not! Just because you can make something into its own component doesn't mean you need to. If repeated elements are based on dynamic, user-generated data, they should be separate components that accept `props`. If those elements are just static links, as in the `Navbar` example, they likely don't need separate components.

However, you'll find professional developer teams creating component libraries that do precisely this sort of thing: every button in the app is a separate component that carries its own `props`, styling, and functionality with it. This keeps things consistent no matter how large the app becomes. Suppose every developer uses the team's custom `<ResponsiveButton>` component instead of generic `<button>` elements. In that case, the team can benefit from modularized React components. When joining a React dev team, you should expect to inherit a custom component library that the team uses throughout the application.
