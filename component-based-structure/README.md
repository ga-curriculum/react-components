## Introduction to component-based structure

One of the key concepts in React is the use of components. Components are independent and reusable bits of code that serve as the building blocks of your application. Let's explore how to identify and structure components in a basic website.

### Identifying components in a web page

A website's layout often contains various sections that can be efficiently managed as components. Here's how to identify potential components:

1. Reusability: Components are ideal for sections of code that appear multiple times. Components are meant to be reusable, so if you notice repeated patterns, consider creating a component.

2. Dynamic Content: Sections that frequently receive changing data are perfect candidates for components. This includes dynamic sections where content might be swapped on a schedule or depending on the user.

3. Like Functionality: Groups of elements that function together, are dependant on each other, or might be styled the same way could be grouped into a single component.

4. Same Purpose: If a set of elements serves a collective purpose or feature, it makes sense to encapsulate them in a component.

Consider this list a guide, the component structure for your applications will ultimately be determined by you and the unique needs of your users.

## Analyzing a web page

Let's examine the markup for a web page and determine what component based structure makes the most sense.

### Hyperbo.ly

This is the landing page for Hyperbo.ly, a super-hot tech start-up making unbelievable progress in every field you can name: AI, VR, Crypto, NFTs...if it's confusing and exciting, it's Hyperbo.ly!

```html
<nav id="top-navbar">
  <a href="/">Home</a>
  <a href="/about-us">About Us</a>
  <a href="/money-pit">Investment Opportunities</a>
  <a href="/the-fine-print">Terms of Service</a>
</nav>
<main>
  <h1>Welcome to Hyperbo.ly</h1>
  <h2>The future is firmly in front of us!</h2>
  <p>If you can't explain it to a fifth-grader, then our product does it.</p>
</main>
<h2>Our Founders</h2>
<ul>
  <li>
    <h3>Elizabeth Holmes: CEO</h3>
    <p>MBA from SuperLegit University</p>
  </li>
  <li>
    <h3>Sam Bankman-Fried: CFO</h3>
    <p>CPA from TotallyReal State</p>
  </li>
  <li>
    <h3>Matt Damon: CMO</h3>
    <p>Was in that Movie You saw</p>
  </li>
</ul>
```

## Modularizing into components

When you're deciding how to divide your application into different components, imagine you’re looking at a wireframe sketch of your site. Where would you naturally draw the lines to separate different sections? This approach helps identify distinct areas that can function independently. Also, consider the reusability of these sections across various pages.

### Breaking a page into components

Based on the markup, there are three clear divisions of this page.

```html
<nav>...</nav>
<main>...</main>
<ul>...</ul>
```

Component structure wont always follow markup structure exactly, but can give give us clues about which items are grouped by purpose or functionality. If we consider the elements on this page, two stand out as great candidates for components:

Nav bar `<nav>`:

- This section, containing links, has a distinct purpose and will likely be reused on multiple pages, making it an ideal component. It is a cohesive unit that will probably also share a set of styles.

Founders list items`<li>`'s:

- The repeated pattern of individual entries in this list indicates a strong use case for components. Each list item shares a similar UI structure but with different content.

## Creating a component hierarchy

Lets look at this same site markup organized as a component hierarchy.

![tktk Hunter need a component outline wireframe here something like this... ](./assets/Screenshot%202024-03-26%20at%203.02.16 PM.png)

The `App` component serves as the parent or **_root_** of our component hierarchy. It contains 2 distinct child components: `Nav`, and `ListItem`. Each of these child components should be represented by its own dedicated file.

```text
App:
  |- Nav
  |- ListItem
  |- ListItem
  |- ListItem
```

This separation allows for more organized code management, with each component having its individual JSX and CSS files.
