# [Model View Controller MVC](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller)
- Model–view–controller (usually known as MVC) is a software design pattern[1] commonly used for developing user interfaces that divides the related program logic into three interconnected elements.
- This is done to separate internal representations of information from the ways information is presented to and accepted from the user.[2][3] This kind of pattern is used for designing the layout of the page.
- Components 
    - Model
        - The central component of the pattern. It is the application's dynamic data structure, independent of the user interface.[5] It directly manages the data, logic and rules of the application.
    - View
        - Any representation of information such as a chart, diagram or table. Multiple views of the same information are possible, such as a bar chart for management and a tabular view for accountants.
    - Controller
        - Accepts input and converts it to commands for the model or view.
        - In addition to dividing the application into these components, the model–view–controller design defines the interactions between them.[7]
            - The model is responsible for managing the data of the application. It receives user input from the controller.
            - The view means presentation of the model in a particular format.
            - The controller responds to the user input and performs interactions on the data model objects. The controller receives the input, optionally validates it and then passes the input to the model.
    - Service
        - Between the controller and the model sometimes goes a layer which is called a service[citation needed]. It fetches data from the model and lets the controller use the fetched data. This layer allows to separate data storage (model), data fetching (service) and data manipulation (controller). Since this layer is not part of the original MVC concept, it is optional in most cases but can be useful for code management and reusability purposes in some cases.

# [Architecting Single Page Applications](https://hackernoon.com/architecting-single-page-applications-b842ea633c2e)
- 4 Layers 
    - View
        - Presentational Componenets
            - receive state through props 
            - emit new tate through events 
        - Container Components 
            - receive state from the store 
            - supply state to presentational components 
            - send new state to the store 
        - Application Services 
            - project interpret state 
            - orchestarate external operations 
        - Store 
            - holds the state 
            - state is immutable 
            - acts as a publisher 
            - notifies Subscribers about state changes 
        - Domain 
            - represents the state 
        - Domain Services 
            - encapsulate business logic 
            - side-effect free 
    - Application Services
    - Store
    - Domain 

# [React MVC](https://blog.testdouble.com/posts/2019-11-04-react-mvc/)
- The guiding light of Model View Controller (MVC) is separating presentation from domain.
- Our application’s “domain” is where we model our perception of the problem and its solution. 
- Implementing MVC Patterns in React
    - A Presentation Layer of Controller and View React Components
    - A UI-Agnostic Data Mode
- Pillar 1: Presentation Layer of Controller and View React Components
    - Controller Components
    - View Components
