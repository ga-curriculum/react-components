# ![React Components - Passing Data Between Components](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to use props in React to pass data between different components.

So far, our Navbar component takes advantage of the **modularization** of React components. The other major impact of React components is their **reusability**, so let's take a look at re-using a single component to represent all the items in a list.

Think about the standard, dashboard-page, indexed list of things present on most web applications. Each individual item in the list could be its own React component, but that definitely shouldn't mean creating a new, unique file for everything in the list. This wouldn't even be possible if the list was dynamically created based on user data!

So, we'd like to have a single re-usable React component that takes care of displaying one individual item in the list. Given an array of objects that we want to display, what we need is some way of passing a single object to each individual instance of the re-usable list item component.

Enter `props`.

Every React component is an just a JavaScript function that returns HTML. When we write JS functions, however, we almost always have some kind of parameter being passed into the function, and so far, none of our React components have been designed to accept any kind of input. The parentheses in our arrow functions have always been empty. Until now!

React components are able to pass data down to child components through use of the `props` keyword. One of React's core features is the way data only flows downwards from a parent component to a child component. This design pattern is technically referred to as **unidirectional data flow**. In React, child component cannot define or change the props of its parent, and the child is not even allowed to change the props it is given from its parent. In other words, `props` are **immutable**. They only go one way, and once they've been passed down, the children are left to deal with them the way they are.

There are two pieces of the puzzle to cover: setting up a component to accept props from its parent, and setting up the parent to send props down to its children.

## Creating the Child Component

To convince investors to fund our incredible, mind-blowing AI crypto VR/AR startup, let's have the home page display a list of the awesome founding team putting this thing together. Each founder in the list will have their own component, and the App.jsx component will loop over an array of objects to generate this list.

First, let's set up our child component by creating a separate file named `FounderListItem.jsx` and setting it up with the smallest, testable filler code we can think of. No need to worry about props yet, let's just get the multiple components flowing and go from there.

```jsx
const FounderListItem = () => {
    return <li> 
    <h3>Hello, I'm a super impressive Founder too!</h3>
    </li>
}
```

Delightful. Don't forget to export it!

```jsx
export default FounderListItem
```

Perfection. Now that we have the child component stubbed out, let's add an array of data to our App component and map through it, returning an instance of `<FounderListItem>` for each object in the array.

In `App.jsx`:

```jsx

const extremelyImpressiveFounders = [
    {
        name: "Elizabeth Holmes",
        title: "CEO",
        credential: "MBA from SuperLegit U"
    },
    {
        name: "Sam Bankman-Fried",
        title: "CFO",
        credential: "CPA from TotallyReal State"
    },
    {
        name: "Matt Damon",
        title: "CMO",
        credential: "Was in that Movie You Saw"
    },
];
```

## You Do: Map Over the Founders, Without Props

Given this array in `App.jsx`, write a .map statement inside of a `<ul>` that loops over each one and adds the `<FounderListeItem>` to the list.

## Solution
```jsx
        <ul>
            { extremelyImpressiveFounders.map((founder)=> (
            <FounderListItem></FounderListItem>
            ))
            }
        </ul>
```

## Sending Data to the Child

To send data from the parent component to the child, we can add `props` using the exact same syntax as HTML attributes. Simply define your key-value pairs in the element, like so:

```jsx
<FounderListItem founder={founder}/>
```

Note the brackets around the right-hand, value side of the attribute. This ensures the value of the JS variable `founder`, which comes to us from the callback function in the `map` statement, will be assigned to a property named `founder` in the child.

## Using Props in the Child

Now that data is being sent into the `FounderListItem` component, we can refactor that function to accept a new parameter named `props`:

```jsx
const FounderListItem = (props) => {
    // Component content remains unchanged
}
```

Now, whenever we want to access a property passed down from the parent, we can use the `props` object. In our app, `props` will have a `founder` property, since that's what we named the attribute inside of `App.jsx`. We can update our `FounderListItem` component to display the data given to it:

```jsx
const FounderListItem = (props) => {
    return <li>
        <h3>{props.founder.name}: {props.founder.title}</h3>
        <p>{props.founder.credential}</p>
    </li>
}
```

## Destructuring Props

A common pattern you'll encounter is React developers **destructuring** the props object in their components. Depending on how nested the data gets, it can get tedious to keep typing and reading the word `props` in front of everything, such as `props.founder.name` and `props.founder.credential`. Instead, the component can use object destructuring syntax when defining its parameters, like so:

```jsx
const FounderListItem = ({founder}) => {
    return <li>
        <h3>{founder.name}: {founder.title}</h3>
        <p>{founder.credential}</p>
    </li>
}
```

This doesn't require changing the parent component's syntax, so it's purely a matter of style in the child component.

## You Do: Refactor the Navbar List

While the items in the navbar are unlikely to change, and are typically fine to hard-code, let's use the opportunity to practice this pattern of refactoring lists into separate components. Our goal is to refactor the list of links in the Navbar to use the same mapping pattern as our list of founders.

Add the following array to `Navbar.jsx` and use it to map over a second, child component for each item in the list. This will involve creating a new component named `NavbarListItem.jsx` to accept and display props from the `Navbar.jsx` parent component.

```js
const pagesInTheApp = [
    {
        name: 'Home',
        href: '/'
    },
    {
        name: 'About Us',
        href: '/about-us'
    },
    {
        name: 'Investment Opportunities',
        href: '/money-pit'
    },
    {
        name: 'Legal Disclosures',
        href: '/the-fine-print'
    },
]
```

## Solution

In ```Navbar.jsx```:

```jsx
import NavbarListItem from './NavbarListItem';
// ...
return <nav id="top-navbar">
    <ul>
      {pagesInTheApp.map((pageInfo)=>(
        <NavbarListItem pageInfo={pageInfo}/>
      ))}
    </ul>
  </nav>
```

In `NavbarListItem.jsx`:

```jsx
const NavbarListItem = (props) => {
    return <li>
        <a href={props.pageInfo.href}>{props.pageInfo.name}</a>
    </li>
}

export default NavbarListItem;
```

## When Do Components Go Too Far?

Was it too much to refactor the static navbar list items into their own components? Probably! Just because you can make something into its own component doesn't mean you should. If repeated elements are based on dynamic, user-generated data, then they should probably be separate components that accept props. If those elements are just static links, as in the Navbar example, it doesn't need to be a separate component. 

However, you'll find professional developer teams creating component libraries that do exactly this sort of thing: every button in the app is a separate component that carries its own props, styling, and functionality with it. This keeps things consistent no matter how large the app becomes. If every developer uses the team's custom `<ResponsiveButton>` component instead of generic `<button>` elements, the team can gain the maximum benefits of modularized React components. Joining a React dev team, you should expect to inhert a custom component library of some kind that the team uses throughout the application.