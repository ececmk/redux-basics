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

## Methods:

### createStore(reducer, [preloadedState], [enhancer]): 
This method is used to create a new Redux store. It takes in a reducer function as its first argument, which is responsible for updating the state based on actions dispatched to the store. The preloadedState parameter is optional and allows you to initialize the state of the store. The enhancer parameter is also optional and is used to enhance the store with third-party capabilities, such as middleware.

### getState():
"getState()" is a method available on the store created with "createStore()". It retrieves the latest snapshot of the state after it has been updated.

### subscribe():
This method is used to subscribe a listener function to the Redux store. Whenever the state of the store changes, the listener function will be called. This is typically used to update the UI in response to state changes.

### dispatch(action): 
This method is used to dispatch an action to the Redux store. The action parameter is an object that describes the action to be performed, such as adding an item to a list or updating a user's profile. When an action is dispatched, it is passed to the reducer function, which updates the state of the store accordingly. Once the state is updated, the subscribed listeners are notified and the UI is updated accordingly.

## Hooks:

### useSelector(): 
The useSelector hook is a hook provided by the React-Redux library. It allows you to extract data from the Redux store state, without needing to subscribe to the store. It takes a single argument, a selector function, which is called with the entire Redux store state and returns the specific data you want from the state.

### useDispatch(): 
The useDispatch hook is another hook provided by the React-Redux library. It allows you to dispatch actions to the Redux store from within a React component. It returns a reference to the dispatch function provided by the Redux store.
