# ![React Components - Concepts](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to articulate the value of modularizing components in React.

Ask any React developer what the main idea of React is, and there's a decent chance they'll answer "components." 

Splitting up front-end code into separate, smaller pieces may not seem revolutionary at first. Still, the practices and design principles that follow from using react components can change how you look at building and maintaining front-end applications.

Part of this is due to React's unique decision to bundle HTML/CSS/JS together within the little micro-project of each component rather than following the more traditional practice of keeping the three domains separate. Traditional front-end development practice is to avoid using inline styles in HTML, avoid script tags in JS, and generally avoid anything that might make it hard to answer the question: "Where is this functionality coming from?" If it's an event listener, it should be in a .js file; if it's a style, it should be in a .css file. Easy.

React changed all that with its heavy reliance on JSX and the free mixing of HTML/CSS/JS within the same file while maintaining an easy way to answer the question: "Where is this functionality coming from?" Thinking in a component-first way lets us reliably track down and preserve pieces of our programs in an isolated way. If the component's broken, fix that component and leave the rest alone. 

This isolation of components is baked into React's state-render cycle. When a variable in state gets updated, only the components that rely on that state need to re-render, and the rest of the page stays unaffected.

The component-first mindset gives developers the same benefits as any modularization project. Collaboration is more manageable when team members stay in their component, and incremental updates are easier when the changes are limited to as small a piece of the overall project as possible. You can more easily re-use standard components across multiple projects, like sign-in and sign-up pages or navbars.

Developing a React app with many components can often mean constantly changing your mind about how many components a given feature should use, how those components should be arranged, which components should have state, and so on. Don't be discouraged if you've made the wrong decision on splitting up components. Get comfortable re-factoring your component architecture as you go. There's rarely one "right" answer to exactly how a site should be split up into React components, but paying attention to the most common and productive patterns will pay off.

In this lesson, we'll start splitting our applications into separate components stored in separate files. We'll pass data from parent to child components, paying particular attention to using components inside of .map statements to create a list displaying data from an array.
