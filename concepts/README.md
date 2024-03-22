# ![React Components - Concepts](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to explain the value of modularizing components in React.

## Modularization in React

Ask any React developer what the primary feature of React is, and there's a decent chance they'll answer "components."

Splitting up front-end code into separate, smaller pieces may not seem revolutionary at first. Still, the practices and design principles that follow from using React components can change how you look at building and maintaining front-end applications.

Let's compare a more traditional HTML, CSS, and JavaScript application to how a React application modularizes its code.

### Traditional Web Application

- **HTML** - HTML is the page structure for our web application. Most, if not all, HTML code is kept in a file commonly named `index.html`. If there is a need in the application to have HTML living outside of `index.html`, that code is contained in a separate `.html` file.
- **CSS** - CSS allows us to transform our applications from plain, black-and-white blobs of text to visually appealing applications. Though CSS can be written inline inside our HTML file or files, by convention we keep those styles in a separate file `.css` file. Our CSS files are then read from our HTML files via a `link` element in the HTML header.
- **JavaScript** - JavaScript provides interactivity and behavior to our web applications, giving our buttons and forms a way to be handled meaningfully. Like with the CSS, we could code our JavaScript in a `script` element in our HTML; however, by convention, we keep all the JavaScript in a separate file and connect it to the HTML.


### React Application

Instead of breaking our code apart by language, React's approach to modularization involves breaking our code apart into components:

- **Components** - Components are defined using JSX, and each component can have its own HTML structure, CSS styles (often still in a separate file), and JavaScript logic. A component encapsulates a single element on the page, such as a button or a form.
- **Component Hierarchy** - Component hierarchy is encouraged by React. We can nest one component inside another to build elements - from a card to a form, all the way up to entire applications.
- **Component Reusability** - Components can be made to be reusable. You can easily import components when needed, reducing code duplication.
- **State and Props** - React components can have internal data called state and - if nested - can be passed data (called props) from a parent component. State and props allow the component to contain their own logic.

> 🧠 State and props will not be the focus of this lesson, but are essential concepts when working with React applications.

In React, we think in terms of **components** as we build. Each component is responsible for its own structure, style, and behavior.

## Components-First Mindset

Thinking in a component-first way lets us reliably track down and preserve pieces of our programs. If something breaks in a component, we can fix that component without having to touch the rest of our app. 

This isolation of components is baked into React's state-render cycle. When a variable in state gets updated, only the components that rely on that state need to re-render, and the rest of the page stays unaffected.

A component-first mindset has a lot of benefits for developers.Collaboration is more easily manageable when team members can work within specific components rather than needing to all make changes to larger codebase. In addition, incremental updates are easier when changes are limited to a small piece of the overall project. Finally, components help reduce repetitive code; you can more easily re-use standard components across multiple projects, like sign-in and sign-up pages or navbars.

### Refactoring in React

Developing a React app with many components can often lead to constantly changing your mind about how many components a given feature should use, how those components should be arranged, which components should have state, and so on. Don't be discouraged if you've made the wrong decision on splitting up components. Get comfortable refactoring your component architecture as you go. There's rarely one "right" answer to exactly how a site should be split up into React components, but paying attention to the most common and productive patterns will pay off.

In this lesson, we'll start splitting our applications into separate components stored in separate files. We'll pass data from parent to child components, using components inside of `.map` statements to create a list displaying data from an array.