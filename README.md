# Redux Basics

Redux is a state management system for cross componant ors app-wide state. It helps us manage such data across multiple components or even the complete app. 

We can split definition of state into three main kind of state:

### Local State: 
State that belongs to a single component. (E.g. listening to user input in an input field, toggling a "show more" details field) --> Should be managed component internal with useState() / useReducer()

### Cross-Component State: 
State that affects multiple components. (E. g. open/close state of a modal ovarlay) --> Requires "props chains".

### App-wide State: 
State that affects the entire app (most/all components) (E.g. user authentication status) --> Requires "props chains".

## Why do we need Redux if we already have React Context for managing state that effects multiple components?

React Context has a couple of potential disadvantages like complex setup/management, performance, deeply nested JSX code and/or huge "Context Provider" components in complex apps because React Context is not optimized for high-frequency state changes.

## How Redux Works?



