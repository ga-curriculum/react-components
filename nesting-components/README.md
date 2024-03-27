# ![React Components - Nesting Components](./assets/hero.png)

**Learning objective:** By the end of this lesson, learners will be able to understand and implement the concept of component nesting in React. 

## Nesting our first component

Now that we have identified two parts of our sample markup to refactor, let's move it into our React app and start nesting some components. We'll start with the nav bar. It's a common UI element found on almost every web page, perfectly illustrating the concept of a reusable and distinct component.

### Examining the `nav` code

Let's look at some of the sample website markup again, but as JSX code in our main `App` component.
Add the following in `App.jsx`:

```jsx
// scr/App.jsx

const App = () => {
  return (
    <>
      <nav id="top-navbar">
        <a href="/">Home</a>
        <a href="/about-us">About Us</a>
        <a href="/money-pit">Investment Opportunities</a>
        <a href="/the-fine-print">Terms of Service</a>
      </nav>
      <main>
        <h1>Welcome to Hyperbo.ly</h1>
        <h2>The future is firmly in front of us!</h2>
        <p>
          If you can't explain it to a fifth-grader, then our product does it.
        </p>
      </main>
    </>
  );
};
```

Here we have nested a `<nav>` JSX element and some default navbar items.

### Clear default css

Next, let's delete the contents of both `App.css` and `index.css`. This removes the default styling and gives us a clean slate.

Add the following back to `index.css`:

```css
/* src/index.css */

#top-navbar {
  display: flex;
  justify-content: space-around;
}
```

This will give our links some breathing room. You should see the following in your browser when you run the app:

![Starter Code Screenshot](./assets/starter-code-screenshot.png)

Now that we have some starting markup, we can begin the process of splitting it into components.

## Splitting the Navbar

The code we want to split off is bundled up nicely inside the single `<nav>` element. This makes modularizing it into a separate component a quick operation.

First, let's create a new `Navbar.jsx` file for this component. We'll create this file in the `src` folder of the project as a sibling to `App.jsx`:

```bash
touch src/Navbar.jsx
```

Next, we'll add our React component and export it from inside the `Navbar.jsx` file.

> Though it might seem unconventional in JavaScript to capitalize file names, React follows the practice of capitalizing both _file_ and _function_ names of components.

Remember, React components are essentially just functions that return HTML. Let's begin by creating a basic function:

```jsx
// src/Navbar.jsx

const Navbar = () => {};
```

Initially, this function doesn't return anything. Our objective is to make the `Navbar` component return the `<nav>` element, which is currently in the `App.jsx` file. We'll achieve this by transferring the entire `<nav>` element into the `Navbar` component as its return value:

```jsx
// src/Navbar.jsx

const Navbar = () => {
return (
<nav id="top-navbar">
  <a href="/">Home</a>
  <a href="/about-us">About Us</a>
  <a href="/money-pit">Investment Opportunities</a>
  <a href="/the-fine-print">Terms of Service</a>
</nav>
);
};
```

The final step is adding the `export` statement. This enables the component to be used in other parts of the application through the `import` statement.

To complete our `Navbar.jsx` file, add the following code at the bottom:

```jsx
// src/Navbar.jsx

export default Navbar;
```

## Importing the Navbar into the App

Now that we've created a Navbar component, let's import it into our `App.jsx` file. Add the following statement to the top of `App.jsx`:

```jsx
// src/App.jsx

import Navbar from "./Navbar.jsx";
```

To include the `Navbar` component in our JSX, we can insert it into the markup like a standard HTML element `<Navbar></Navbar>`, or simply `<NavBar/>`. 

> React components rarely need any content between their opening and closing tags, so a common React convention is to use the self-closing tag shortcut: `<Navbar/>`

Let's place our new component above the `<h1>` where the `nav` element used to be:

```jsx
// src/App.jsx

const App = () => {
  return (
    <>
      <Navbar />
      <main>
        <h1>Welcome to Hyperbo.ly</h1>
        <h2>The future is firmly in front of us!</h2>
        <p>
          If you can't explain it to a fifth-grader, then our product does it.
        </p>
      </main>
    </>
  );
};
```

Nice! Check back in the browser, and you should see the site restored to its original look, only now with components working together to make it happen.

## Component-specific CSS

As you dive deeper into React, you'll encounter more advanced techniques for styling components. But for now, let’s keep things simple: create a separate `.css` file for each component. Treating components as modular units isn’t just about the JavaScript code – it extends to their styling too. This approach means giving each component its very own `.css` file.

Go ahead and move the CSS code for the navbar from `index.css` to a new file, `Navbar.css`. This file should be placed right next to `Navbar.jsx` in your project’s structure.

Now, add an import statement to the top of your `Navbar.jsx` file that imports the `Navbar.css` style sheet:

```jsx
// src/Navbar.jsx

import "./Navbar.css";
```

Now, you might be hoping that this setup means your styles are locked down to just the Navbar component. That would be helpful, but actually, the CSS here is still global. That means styles in `Navbar.css` could affect other parts of your app where similar css selectors are used.

To keep things tidy, make sure your CSS rules are targeted specifically at the Navbar. For example, use an `id` or `class` that’s unique to the Navbar. That’s a good practice to ensure your styles don’t wander off and start affecting other elements unexpectedly.
