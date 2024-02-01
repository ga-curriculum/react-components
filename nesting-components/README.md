# ![React Components - Nesting Components](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to tktk

In this microlesson, demonstrate splitting off a small piece of an app into its own seprate file. This is where you should cover import/export, the export default syntax, and so on.

The exporting pattern we want to use is:

const Component = () => {

}

export default Component;

There should be no props yet, so this will be a boring presentational component swap. The component being refactored is up to you, but shouldn't include presenting any data from state, as that would lead to needing a prop sent down into the component. You could deliberately make a hard-coded list of three unique components that follow the same pattern, so that students are naturally led to the question: "shouldnt we make one component that accepts input instead of three hard-coded parallel components?" 

Then you could refactor it to use an array that lives in state in the NEXT microlesson, but in this microlesson, props can only be used as a conceptual cliffhanger that leads into the next microlesson specifically about props.