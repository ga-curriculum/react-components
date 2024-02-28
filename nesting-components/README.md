# ![React Components - Nesting Components](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to modularize a react application across multiple components.

## Modularize Components

In this lesson, we'll explore modularizing components as we build the landing page for Hyperbo.ly, a super-hot tech start-up making unbelievable progress in every field you can name: AI, VR, Crypto, NFTs...if it's confusing and exciting, it's Hyperbo.ly!

### Navbar Modulazation

When considering where to split up pieces of a front-end application into separate components, you should think about where the lines would be drawn on a wireframe sketch of the site. You should also think about which pieces might be reusable across different pages. One particular UI piece on nearly every web page comes to mind when considering both requirements: navigation bars!

Navbars are a perfect use case for our first modularized component: reusable and not generally impacting the rest of the site. They usually are kept at the top of the page, and there are specific interactions we can assume a navbar would have. Let's look at some React code where we have nested a `<nav>` JSX element and some default navbar items. 

```jsx
const App = () => {
    return  <>
            <nav id="top-navbar">
                <ul>
                    <li>
                        <a href="/">Home</a>
                    </li>
                    <li>
                        <a href="/about-us">About Us</a>
                    </li>
                    <li>
                        <a href="/money-pit">Investment Opportunities</a>
                    </li>
                        <li>
                        <a href="/the-fine-print">Legal Disclosures</a>
                    </li>
                </ul>
            </nav>
            <main>
                <h1>Welcome to Hyperbo.ly</h1>
                <h3>The future is firmly in front of us!</h3>
                <p>If you can't explain it to a fifth-grader, then our product does it.</p>
            </main>
            </>
}
```

Additionally, let's delete the contents of `index.css` and add some sensible styling relevant to our navbar:

```css
#top-navbar ul {
    display: flex;
    list-style-type: none;
    justify-content: space-between;
}
```

You should see the following in your browser when you run the app:

![Starter Code Screenshot](./assets/starter-code-screenshot.png)

### Splitting the Navbar

The code we want to split off is bundled up nicely inside the single `<nav>` element. This makes modularizing it into a separate component a quick operation.

Create a new `Navbar.jsx` file for this component. It should be created at the root level of the project as a sibling to `App.jsx`

```bash
touch Navbar.jsx
```

We'll create a React component inside this file and export it from `Navbar.jsx` to import it into `App.jsx` and any other future components that want the main navbar at the top. It may seem odd to capitalize the names of these files since they're written in camelCase-loving JavaScript. Still, the React convention is to capitalize our components' file and function names, so we do that here.

Remember, React components are nothing but functions that return HTML, so let's start with a function:

```jsx
const Navbar = () => {
}
```

Okay, a function that returns nothing. Pretty lame. Fortunately, what we want to return is that big `<nav>` element from the `App.jsx` file, so we can perform a significant cut-and-paste operation and paste the entirety of the `<nav>` element as the return value for `Navbar`:

```jsx
const Navbar = () => {
    return (
        <nav id="top-navbar">
            <ul>
                <li>
                    <a href="/">Home</a>
                </li>
                <li>
                    <a href="/about-us">About Us</a>
                </li>
                <li>
                    <a href="/money-pit">Investment Opportunities</a>
                </li>
                    <li>
                    <a href="/the-fine-print">Legal Disclosures</a>
                </li>
            </ul>
        </nav>
    )
}
```

The last piece of the puzzle for modularizing components is the critical `export` statement, which allows it to be pulled into other components that require it with an `import` statement.

Add the following to the bottom of our `Navbar.jsx` file:

```jsx
export default Navbar;
```

### Importing the Navbar into the App

Now that the Navbar lives independently, we can bring it back into the application and import it into the `App.jsx` file. We can add the following statement to the top of our `App.jsx` file:

```jsx
import Navbar from './Navbar.jsx'
```

To actually use the Navbar component in our rendered App component, we can add it using the same HTML syntax as any other element, only using the proper name we gave the component: in this case, `<Navbar></Navbar>`. Components typically don't need or want any content between the opening and closing tags, so React components typically use the self-closing tag shortcut: `<Navbar/>`

Right above the `<h1>` where the nav element used to be, we can now add the component back in:

```jsx
const App = () => {
    <Navbar/>
    <main>
        <h1>Welcome to Hyperbo.ly</h1>
        <h3>The future is firmly in front of us!</h3>
        <p>If you can't explain it to a fifth-grader, then our product does it.</p>
    </main>
}
```

Check back in the browser, and you should see the site restored to its original look, only now with 100% more components working together to make it happen. Go team! tktk tado emoji

## Component-Specific CSS. Kind of.

While you'll learn more sophisticated methods of creating component-specific CSS styles later in your react journey, we should create a separate .css file for each component. After all, components should be treated as a separate project, including the styling necessary to complete them. So, they should get their own .css file. 

Move the navbar's CSS code from App.css into a new file called `Navbar.css`, created as a sibling file to `Navbar.jsx` at the root level.

Now, add an import statement to the top of your `Navbar.jsx` file that imports the `Navbar.css` style sheet:

```jsx
import './Navbar.css'
```

You might think this means the style will only be applied within the Navbar component. While that would be amazing (and there are tools to create actual, component-specific CSS), sadly, the styles will be applied globally to any page the Navbar component shows up on. So, you should still write your rules specific to the scope of the component, such as using an id, as in our example Navbar component's style.
