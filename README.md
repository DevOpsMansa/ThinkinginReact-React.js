# React + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh


# Thinking in React
Learning Objectives
By the end of this lesson, learners will be able to:

Describe the "Thinking in React" philosophy.
Use the five-step process provided by the React team to build a React application from scratch.
Explain what type of data should be used as "state" and what shouldn't.

Thinking In React
When building websites with different frameworks, you should approach how you build them differently. With pure HTML and JavaScript, building a webpage is a much different process than it is with React. Likewise, other front-end frameworks require their own unique approaches in order to most efficiently build applications.

For this purpose, the React team provides us with "Thinking in React" as a guideline.

Thinking in React is a concept developed by the React team to help web developers build user interfaces (UI) more efficiently. It is a component-based approach that focuses on breaking down UI elements into small, reusable components. This allows developers to break down complex tasks into individual, simple parts that can be reused as needed. The main idea behind Thinking in React is to think of the UI as a set of components, or small pieces, that can be moved around, modified, and reused.

Thinking in React requires developers to break down an application into smaller components, each of which has its own state. State is data that is stored within a component, such as a user’s name or what items are in their shopping cart. By breaking down an app into smaller components, developers can more easily manage application state and make sure that updates only affect the component that needs updating.

The Thinking in React approach also encourages developers to use one-way data flow. This means that data flows from parent components to child components, rather than from child components to parent components. This helps keep components independent and makes it easier to debug and maintain an application.

Here are the steps to take when building a React application, according to the "Thinking in React" principles:

Break your user interface into components.
Build a static version of the application using React.
Find the simplest complete representation of the UI state.
Identify where the state should "live" - which component should "own" it.
Add inverse data flow, where necessary.
We will walk through each of these steps with examples adapted from the React documentation, so you can see how an application starts and evolves throughout development.


Step 0: Start with a Mockup
More often than not, you will start your applications with a mockup that you have either made yourself or received from a designer. You will likely also be given a dataset from an API that you are instructed to work with.

For the purposes of our examples, here are the data and mockup starting points:

[
  { category: "Fruits", price: "$1", stocked: true, name: "Apple" },
  { category: "Fruits", price: "$1", stocked: true, name: "Dragonfruit" },
  { category: "Fruits", price: "$2", stocked: false, name: "Passionfruit" },
  { category: "Vegetables", price: "$2", stocked: true, name: "Spinach" },
  { category: "Vegetables", price: "$4", stocked: false, name: "Pumpkin" },
  { category: "Vegetables", price: "$1", stocked: true, name: "Peas" }
]
mockup
Now that we know where to start, we can begin breaking this mockup down into individual components.


Step 1: Establish a Component Heirarchy
The simplest way to determine what components your application needs is to draw boxes to group components on the mockup itself, and give them names! Sometimes, mockups will already come with this information available, saving us a bit of time.

When determining what each component contains, think about the following:

Each component should (ideally) only do one thing. If a component has multiple functions, consider breaking it down into smaller subcomponents.
Components often align with CSS class selectors; if you have many elements you would style with a list-item class, perhaps you need a ListItem component.
Consider how you would organize design layers in HTML; anything that gets repeated is likely a component.
Likewise, well-structured data from an API will often map directly to the structure of your components, because UI and data models often share the same information architecture. In general, each component should match one piece of your data model (at most, with some exceptions).

Here's how the example mockup breaks down:

mockup
FilterableProductTable (grey) contains the entire app.
SearchBar (blue) receives the user input.
ProductTable (lavender) displays and filters the list according to the user input.
ProductCategoryRow (green) displays a heading for each category.
ProductRow (yellow) displays a row for each product.
In this case, we have not defined a separate component for the ProductTable header containing "Name" and "Price" because it is very simple. If the header were to expand in complexity and incorporate additional functionality such as searching or filtering, it would likely need to become its own component.

The component heirarchy is built simply by listing which components are nested inside of one another in a simple nested list:

FilterableProductTable

SearchBar
ProductTable

ProductCategoryRow
ProductRow

Step 2: Build a Static Layout in React
As a general rule of thumb, building static layouts requires a lot of typing and not much thinking, and adding interactivity requires a lot of thinking but not much typing. Starting with a static layout allows you to make sure your components are what they need to be, where they need to be, and how they need to be before you start complicating them with the wiring that enables interactivity.

How you approach building the static layout depends on the scale of the project and your personal preferences. In small-scale projects, it's typically easiest to work top-down, starting with the "parent" components and working your way down to the children. In larger projects, it becomes easier to do the reverse.

In this example, we'll build out our products all at once so that you can decide how you would have approached it after seeing the final result. When learning a new concept or a new way to approach a problem, it is often useful to start with the solution and work your way backwards to see how it was done. This makes it easier to do it yourself the next time you encounter something similar!

This learning technique is called "retrograde analysis," and can be helpful in many aspects of life, not just programming!# ThinkinginReact-React.js
