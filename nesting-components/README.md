# ![React Components - Nesting Components](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to modularize a react application across multiple components.

When thinking about where to  split up pieces of a front-end application into separate components, you should think about where the lines would be drawn on a wireframe sketch of the site. You should also think about which pieces might be re-usable across different pages. One particular piece of UI, present on nearly every web page, comes to mind when thinking of both of these requirements: navigation bars!

Navbars are a perfect use case for our first modularized component: re-usable, not generally impacting the rest of the site, and perfect to give to a member of the team to work on in isolation. The other developers know a navbar will be at the top of the application, but otherwise, they don't have to worry much about how the navbar will interact with their part of the application. So, let's send a navbar into its own file.

First, let's start with a reasonable home page and paste the following into our App.jsx file:

```jsx
// TODO ADD THE STARTER CODE
```

Additionally, let's delete the contents of `index.css` and add some sensible styling relevant to our navbar:

```css
/* TODO ADD THE STARTER CODE */
```

You should see the following in your browser when you run the app:

TODO: ADD SCREENSHOT OF STARTER CODE

## Splitting the Navbar

Conviently, the code we want to split off is all bundled up nicely inside the single `<nav>` element. This should make modularizing it into a separate component a pretty quick operation.

Let's start by creating a new file for this component, named `Navbar.jsx`. It should be created at the root level of the project, as a sibling to `App.jsx`

```bash
touch Navbar.jsx
```

We'll create a React component inside this file, and export it from `Navbar.jsx` so it can be imported into `App.jsx` and any other future components that want the main navbar at the top. It may seem odd to capitalize the names of these files, since they're written in camelCase-loving JavaScript, but React convention is to capitalize the file names and the function names of our components, so we do that here.

Remember, React components are nothing but functions that return HTML, so let's start with a function:

```jsx
const Navbar = () => {
}
```

Okay, a function that returns nothing. Pretty lame. Fortunately, what we want to return is that big `<nav>` element from the `App.jsx` file, so we can perform a major cut-and-paste operation and paste the entirety of the `<nav>` element as the return value for `Navbar`:

```jsx
const Navbar = () => {
    return //TODO: ADD STARTER CODE
}
```

The last piece of the puzzle for modularizing components is the critical `export` statement, which allows it to be pulled in to other components that require it with an `import` statement.

Add the following to the bottom of our `Navbar.jsx` file:

```jsx
export default Navbar;
```

## Importing the Navbar into the App

Now that the Navbar lives on its own, we're ready to bring it back into the application and import it in the `App.jsx` file. We can add the following statement to the top of our `App.jsx` file:

```jsx
import Navbar from './Navbar.jsx'
```

To actually use the Navbar component in our rendered App component, we can add it using the same HTML syntax as any other element, only using the proper name we gave the component: in this case, `<Navbar></Navbar>`. Components typically don't need or want any content between the opening and closing tags, so React components typically use the self-closing tag shortcut: `<Navbar/>`

Right above the `<h1>` where the nav element used to be, we can now add the component back in:

```jsx
const App = () => {
    <Navbar/>
    <h1> //TODO: ADD STARTER CODE
}
```

Check back in the browser and you should see the site restored to its original look, only now with 100% more components working together to make it happen. Go team!

## Component-Specific CSS. Kind of.

While you'll learn more sophisticated methods of creating component-specific CSS styles later in your react journey, for now, we should create a separate .css file for each component. After all, components should be treated as their own separate project, and that includes the styling necessary to make them complete. So, they should get their own .css file. 

Move the navbar's CSS code from App.css into a new file called `Navbar.css`, created as a sibling file to `Navbar.jsx` at the root level.

Now, add an import statement to the top of your `Navbar.jsx` file that imports the `Navbar.css` style sheet:

```jsx
import './Navbar.css'
```

You might think this means the style will only be applied within the Navbar component, and while that would be amazing (and there are tools to create actual, component-specific CSS), sadly the styles will be applied globally to any page the Navbar component shows up on. So, you should still write your rules specific to the scope of the component, such as using an id, as in our example Navbar component's style.