# [context api](https://reactjs.org/docs/context.html)
- Context provides a way to pass data through the component tree without having to pass props down manually at every level.
- Context provides a way to share values like these between components without having to explicitly pass a prop through every level of the tree.
    - If you only want to avoid passing some props through many levels, component composition is often a simpler solution than context.
- API 
    - React.createContext
    - Context.Provider
    - Class.contextType
    - Context.Consumer
    - Context.displayName
- Caveats: 
    - Because context uses reference identity to determine when to re-render, there are some gotchas that could trigger unintentional renders in consumers when a provider’s parent re-renders.
    
# [react context links](https://github.com/diegohaz/awesome-react-context)
- keeping this on deck for later :) 
