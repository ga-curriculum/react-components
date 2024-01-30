# ![React Components - Passing Data Between Components](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to tktk

NOW you can add props to the child components. Huzzah! An array of objects that lives in state makes a ton of sense for this, as it enables you to show how an object with multiple properties could be sent in as a single prop that then gets "unpacked" in the child component. You could refactor the previous "bad" pattern of three unique components into the dynamic, prop-accepting single component that gets looped over.

Note that props are immutable! Dont get too deep into this, as the lifting state pattern will be coming in a future module, but not quite yet. You could include a button in the child component that attempts to change the prop, and reveals that it does not work.

You could also demo passing props down through multiple generations, as this is a pain point in React. So three layers of components passing down something from level 1's state into level 2's props and level 3's props.