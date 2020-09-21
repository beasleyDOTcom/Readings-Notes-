## Why do we not need more .html pages in a multi-page React app?
because we can update the state to reflect what we want displayed 
## If we wanted a component to show up on every page, where would we put it and why?



Outside the <BrowserRouter/>
 -[x] Inside the <BrowserRouter />, outside a <Route />
 We'd put it in the app.js where we are displaying all of our compenents or in a component we import to app.js
Inside a <Route />
## What does props.children contain?
 props.children is used to display whatever you include between the opening and closing tags when invoking a component.
 resource: https://codeburst.io/a-quick-intro-to-reacts-props-children-cb3d2fce4891
Document the following Vocabulary Terms
Term
## Composition:
In React, composition is a natural pattern of the component model. It's how we build components from other components, of varying complexity and specialization through props. Depending on how generalized these components are, they can be used in building many other components.
resource: https://dev.to/bouhm/thinking-in-react-component-composition-fp5#:~:text=What%20is%20Composition%3F,in%20building%20many%20other%20components.
Children / Child Components
 props.children is used to display whatever you include between the opening and closing tags when invoking a component.
 resource: https://codeburst.io/a-quick-intro-to-reacts-props-children-cb3d2fce4891
## Hash Routing
A <Router> that uses the hash portion of the URL (i.e. window.location.hash) to keep your UI in sync with the URL.
resource: https://reactrouter.com/web/api/HashRouter
## Link Routing
allows you to use links to access different components
resource: https://reactrouter.com/web/api/Link