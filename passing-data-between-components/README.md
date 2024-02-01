# ![React Components - Passing Data Between Components](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to tktk

NOW you can add props to the child components. Huzzah! An array of objects makes a ton of sense for this, as it enables you to show how an object with multiple properties could be sent in as a single prop that then gets "unpacked" in the child component. You could refactor the previous "bad" pattern of three unique components into the dynamic, prop-accepting single component that gets looped over.

Note that props are immutable! Dont get too deep into this, since there's no logical reason for them to want to change it, but at SOME point we need to say they're immutable, so here it is.

You could also demo passing props down through multiple generations, as this is a pain point in React. So three layers of components passing down something from level 1's state into level 2's props and level 3's props.