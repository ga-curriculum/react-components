# ![React Components - Concepts](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to articulate the value of modularizing components in React.

## Modulization in React

Ask any React developer what the main idea of React is, and there's a decent chance they'll answer "components."

Splitting up front-end code into separate, smaller pieces may not seem revolutionary at first. Still, the practices and design principles that follow from using React components can change how you look at building and maintaining front-end applications.

Let's compare a more traditional HTML, CSS, and JavaScript application to how a React application modulizes its code.

### Traditional Web Application

- **HTML** - HTML is the page structure for our web application. Most, if not all, HTML code is kept in a file commonly named `index.html`. If there is a need in the application to have HTML living outside of `index.html`, that code is contained in a `.html` file.
- **CSS** - CSS allows us to transform our applications from plain, black-and-white blobs of text to visually appealing applications. Even though CSS can be written inline inside our HTML file or files by convention, we keep those styles in a separate file that is a `.css` file. Our HTML files are then read from our CSS files via a `link` element in the HTML.
- **JavaScript** - JavaScript provides interactivity and behavior to our web applications, giving our buttons and forms a way to be handled meaningfully. Like with the CSS, we could code our JavaScript in a `script` element in our HTML; however, by convention, we keep all the JavaScript in a separate file and connect it to the HMTL.

There are various ways to break down the CSS and JavaScript into smaller pieces that give our traditional web application some modulization. Still, overall, we keep our HTML with our HTML in `.html` file, we keep our CSS with our CSS in `.css` files, and lastly, we keep our JavaScript with our JavaScript in `.js` files.

### React Application

Instead of breaking our code apart by the language, we are working on React approach modulization by breaking our code apart by functionality called components.

In a React application, we take a different approach:

- **Components** - Components are defined using JSX, and each component can have its own HTML structure, CSS styles (often still in a separate file), and JavaScript logic. A component encapsulates a single element on the page, such as a button or a form.
- **Component Hierarchy** - Component hierarchy is encouraged by React. We can nest one component inside another to build more minor elements like a form to entire applications.
- **Component Reusability** - Components can be made to be reusable. You can easily import components when needed, reducing code duplication.
- **State and Props** - React components can have internal data called state and be passed data from their parent if nested called props. State and props allow the component to contain their own logic.

> 🧠 State and props will not be the focus of this module, but it is essential to know that they are there and are part of a React application.

In React, we think of **components** as we build. Each component is responsible for its own structure, style, and behavior.

## Components-First Mindset

With Reacts heavy reliance on JSX and the free mixing of HTML/CSS/JS within the same file while maintaining an easy way to answer the question: 

**"Where is this functionality coming from?"**

Thinking in a component-first way lets us reliably track down and preserve pieces of our programs in an isolated way. If the component's broken, fix that component and leave the rest alone. 

This isolation of components is baked into React's state-render cycle. When a variable in state gets updated, only the components that rely on that state need to re-render, and the rest of the page stays unaffected.

The component-first mindset gives developers the same benefits as any modularization project. Collaboration is more manageable when team members stay in their component, and incremental updates are easier when the changes are limited to as small a piece of the overall project as possible. You can more easily re-use standard components across multiple projects, like sign-in and sign-up pages or navbars.

### Refactoring in React

Developing a React app with many components can often mean constantly changing your mind about how many components a given feature should use, how those components should be arranged, which components should have state, and so on. Don't be discouraged if you've made the wrong decision on splitting up components. Get comfortable refactoring your component architecture as you go. There's rarely one "right" answer to exactly how a site should be split up into React components, but paying attention to the most common and productive patterns will pay off.

In this lesson, we'll start splitting our applications into separate components stored in separate files. We'll pass data from parent to child components, paying particular attention to using components inside of `.map` statements to create a list displaying data from an array.