# [Architectural Styles and Architectural Patterns](https://medium.com/@mlbors/architectural-styles-and-architectural-patterns-c240f7df88a0#:~:text=Architectural%20Patterns%20VS%20Design%20Patterns&text=In%20a%20few%20words%2C%20while,and%20mechanisms%20of%20a%20system.)
- Architectural Patterns are similar to Design Patterns, but they have a different scope. In a few words, while Design Patterns impact a specific section of the code base, Architectural Patterns are high-level strategies that concern large-scale components, the global properties and mechanisms of a system.
- Sytles and Patterns - A single architecture can contain several Architectural Styles, and each Architectural Style can make use of several Architectural Patterns. An Architecture Patterns can be a subset of an Architectural Styles targeting a specific scope.
- Some major Architectural Patterns and Architectural Patterns Styles
    - Layered
    - Event-Driven
    - Domain Driven Design
    - Pipes and Filters
    - Microservices

# [Container and Presentation Pattern](https://alchemycodelab.github.io/fsjs-notes/05_react/patterns/container_presentation/)
- Container and Presentation Pattern
    - split into two distinct places: 
        - containers : are stateful components that contain your business login
        - presentations : are stateless components that present your data 
- Containers 
    - Container components “[a]re concerned with how things work”1. In this role they manage state, fetch data from APIs, setup event handlers, and pass information to other components via props.
- Presentations 
    - Presentation components “[a]re concerned with how things look”1. In this role they receive props and use those props to render and style DOM.
- Directory Structure 

# [Container Details](https://alchemycodelab.github.io/fsjs-notes/05_react/patterns/container_presentation/container-details)
- Container Component Details
    - Container components are responsible for specifying how a section of our application works. They manage state, fetch data from apis, and setup event handlers.
- Class Containers
- Initializing State
    - To initialize state use the useState hook. When using useState each piece of state should be a JavaScript primitive (string, number, boolean, null, undefined) or a simple array. You can use multiple useState hooks in a single component.
- Fetching Data
    - Fetching data and setting the fetched data in state is considered a side effect. This is because by fetching data we are changing the state of our application.
- Containers as Hooks
    - Containers can also be written as custom hooks, rather than as components (container hooks vs container components).

# [Presentation Details](https://alchemycodelab.github.io/fsjs-notes/05_react/patterns/container_presentation/presentation-details)
- Presentation components are responsible for specifying how a section of our page looks. They create DOM and styles.
- Creating A Presentational Component
    - Presentational components are written as functional components. They return the markup that is going to get rendered to the DOM.
- Ofter, we’ll need to pass props into our presentational components in order to make them reusable.
- When we pass props into our component we should use the prop-types package to specify the props our component receives. This gives us convenient warning messages if we forget to pass a prop or pass a prop with the wrong type.

# [functional vs class components](https://medium.com/@Zwenza/functional-vs-class-components-in-react-231e3fbd7108)
- Differences between functional and class-Components   
    - syntax 
    - state
    - lifecycle hooks 
    -  
- Why use functional components? 
    - Functional component are much easier to read and test because they are plain JavaScript functions without state or lifecycle-hooks
    - You end up with less code
    - They help you to use best practices. It will get easier to separate container and presentational components because you need to think more about your component’s state if you don’t have access to setState() in your component
    - The React team mentioned that there may be a performance boost for functional component in future React versions
