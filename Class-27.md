## Just taking some general notes, as I feel I would refere back to these docs for specific examples 

# [setState explained](https://css-tricks.com/understanding-react-setstate/)
- setState() is the only legitimate way to update state after the initial state setup. 

# [Reconciliation](https://reactjs.org/docs/reconciliation.html)
-  React implements a heuristic O(n) algorithm based on two assumptions:
    - Two elements of different types will produce different trees.
    - The developer can hint at which child elements may be stable across different renders with a key prop.

# [Typechecking Props](https://reactjs.org/docs/typechecking-with-proptypes.html)
- To run typechecking on the props for a component, you can assign the special propTypes property:
    - ```import PropTypes from 'prop-types';```
    - ```Greeting.propTypes = {```
        ```name: PropTypes.string```
        ```};```

# [snapshot testing](https://jestjs.io/docs/en/snapshot-testing)

# [static rendering - enzyme](https://airbnb.io/enzyme/docs/api/shallow.html)
- Shallow rendering is useful to constrain yourself to testing a component as a unit, and to ensure that your tests aren't indirectly asserting on behavior of child components.

# [shallow mounting - enzyme](https://airbnb.io/enzyme/docs/api/render.html)
- render returns a wrapper very similar to the other renderers in enzyme, mount and shallow; however, render uses a third party HTML parsing and traversal library Cheerio. We believe that Cheerio handles parsing and traversing HTML extremely well, and duplicating this functionality ourselves would be a disservice.

# [full mounting - enzyme](https://airbnb.io/enzyme/docs/api/mount.html)
- Full DOM rendering is ideal for use cases where you have components that may interact with DOM APIs or need to test components that are wrapped in higher order components.'
- Full DOM rendering requires that a full DOM API be available at the global scope. This means that it must be run in an environment that at least “looks like” a browser environment. If you do not want to run your tests inside of a browser, the recommended approach to using mount is to depend on a library called jsdom which is essentially a headless browser implemented completely in JS.
