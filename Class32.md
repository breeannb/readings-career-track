# [react custom hooks](https://reactjs.org/docs/hooks-custom.html)
- A custom Hook is a JavaScript function whose name starts with ”use” and that may call other Hooks
- There’s nothing new inside of it — the logic is copied from the components above. Just like in a component, make sure to only call other Hooks unconditionally at the top level of your custom Hook.
- Custom Hooks are a convention that naturally follows from the design of Hooks, rather than a React feature.
- Tip: Pass Information Between Hooks

# [hook rules](https://reactjs.org/docs/hooks-rules.html)
- Only Call Hooks at the Top Level
    - Don’t call Hooks inside loops, conditions, or nested functions.
- Only Call Hooks from React Functions
    - Call Hooks from React function components.
    - Call Hooks from custom Hooks (we’ll learn about them on the next page).

# [custom hooks - all you need to know](https://www.telerik.com/kendo-react-ui/react-hooks-guide/#toc-custom-react-hooks)

# [10 essential react hooks](https://blog.bitsrc.io/10-react-custom-hooks-you-should-have-in-your-toolbox-aa27d3f5564d)
- useArray hook
    - Usage: Building a todo list was never this simple. We provide the array in the hook and get access to these methods and array in the todos object below.
- react-use-form-state hook
    - react-use-form-state is a small React Hook that attempts to simplify managing form state, using the native form input elements you are familiar with.
- react-fetch-hook
    - Making ajax calls is like the most basic and most performed task for a frontend developer. And the React community is quick enough to create a hook for this purpose too.
- useMedia hook
    - useMedia is a React sensor hook that tracks the state of a CSS media query. We all know the importance of the media queries and how much important is responsiveness for any site.
- react-useportal hook
    - React Portals provide a first-class way to render children into a DOM node that exists outside the DOM hierarchy of the parent component. And this hook helps us do that.
-  react-firebase-hooks
    - We all appreciate the greatness of firebase and use it a lot in our projects, whether its for authentication or storage. And this hook is the one we really need.
- use-onClickOutside hook
    - An outside click is a way to know if the user clicks everything but a specific component. You may have seen this behavior when opening a dropdown menu or a modal or a dropdown list.
- useIntersectionObserver hook
    - The Intersection Observer API provides a way to asynchronously observe changes in the intersection of a target element with an ancestor element or with a top-level document’s viewport.
- use-location hook
    - The name says it all, this hook is used for getting the location of the browser.
- use-redux hook
    - This one is for my redux readers. This hook returns the store and dispatch property.
