# Redux Basics

Redux is a state management system for cross-component or app-wide state. It helps us manage such data across multiple components or even the entire app.

We can split the definition of state into three main kinds:

### Local State: 
State that belongs to a single component (e.g. listening to user input in an input field, toggling a "show more" details field) should be managed internally by the component using useState() or useReducer().

### Cross-Component State: 
State that affects multiple components (e.g. the open/close state of a modal overlay) requires "prop chains."

### App-wide State: 
State that affects the entire app (most or all components) (e.g. user authentication status) requires "prop chains."

## Why do we need Redux if we already have React Context for managing state that effects multiple components?

React Context has a couple of potential disadvantages, such as complex setup/management, performance issues, and deeply nested JSX code, and/or huge "Context Provider" components in complex apps because React Context is not optimized for high-frequency state changes.

## How Redux Works?

Redux is all about having one central data (state) store in your application. This is super important: never have more than one store. We can use the data stored in that store inside our components. If some data there changes, we want to know about it in a component so we can react accordingly and update the UI. Set up central store subscriptions for these components. They subscribe to the store, and whenever the data changes, the store notifies the components. The components can then get the data they need and use it.

## How do we change stored "data"?

Here is one very important rule: Components never directly manipulate the data stored in the store. Instead, we use a concept called reducers. We have to set up a reducer function, which is responsible for mutating the stored data.

!!! "Reducer functions" are a general concept and not a useReducer() hook. Reducer functions are functions that take some input, transform that input, and output a new result.

## How do we connect components and reducer function?

We have a third concept here: Actions. Components dispatch actions, meaning that they trigger certain actions. An action is simply a JavaScript object that describes the type of operation that the reducer should perform. Redux forwards the action to the reducer, reads the description of the desired operation, and performs the operation specified by the reducer.

So, components dispatch actions which describe what should be done but don't perform the operation directly. These actions are forwarded to the reducer, which carries out the desired operation and produces a new state that effectively replaces the existing state in the Central Data Store. When the state in that data store is updated, subscribing components are notified so that they can update their UI.

## The Reducer Function:

A reducer function is a standard JavaScript function, but it will be called by the Redux Library and will always receive two parameters: the existing state and the dispatched action.

The reducer function must return a certain output, meaning that it must return a new state object. Therefore, a reducer function should be a pure function, which basically means that the same values for inputs should always produce exactly the same output. Additionally, there should be no side effects inside that function.

!!! A reducer should really just be a function that takes the given input which provided by Redux and then produces the expected output; a new state object.
