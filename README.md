# Ecmascript

#### Recipe 1

#### You want to create a slice of an object which has unique keys but also arrays linked to those unique keys
```
data: () => ({
    content: {
      'Monday': {       
        content: 'Hello world',
        timestamp: 1,
      },
      'Tuesday': {     
        content: 'Hi globe',
        timestamp: 2,
      },
    },
    days: [ 'Monday', 'Tuesday' ]    
  }),
  
  const getMeetings = (state) => 
    state.days.map((day) => state.content[day]);
```

#### Recipe 2

#### You want to abstract out object manipulation (merge, delete, join, slice, select) so in future you can plug in any new framework and replace the current one

See if you can create a helper and have object operations such as merge, delete, join, slice, select contained within there

#### Recipe 3
#### Integrate Redux Devtools and redux-logger (with diff set to true and perf timings enabled) in your workflow.

```
import { createStore, applyMiddleware, compose } from 'redux'
import createLogger from 'redux-logger';
const logger = createLogger({diff : true,
                            duration : true});
                            
// Add redux-logger to the end of middleware's list  
const middlewares = [Other middlewares here, logger];

const enhancers = [applyMiddleware(...middlewares)];

const composeEnhancers = process.env.NODE_ENV !== 'production' && typeof window === 'object' && window.__REDUX_DEVTOOLS_EXTENSION_COMPOSE__
    ? window.__REDUX_DEVTOOLS_EXTENSION_COMPOSE__
    : compose;

// or (skip the initialState)
const store = createStore(reducer, composeEnhancers(...enhancers));

const initialState = {
    count: 0
};
// Store with initialState
const store = createStore(reducer, initialState, composeEnhancers(...enhancers));
```
#### Recipe 4
#### Mock redux store

#### Recipe 5
#### View transpiled code (ES6 -> ES5)

If you have babel-cli installed, then:
```
babel test_es6.js --out-file test_es5.js
```

#### Recipe 6
#### Chrome debugging
Features:
 - Source map based debugging of JSX/ES7
 - XHR breakpoints - conditional when url contains "weather"
 - Event Listener breakpoints
 - DOM breakpoint - subtree modifications

Outputs the ES5 code

#### Note 1
Add type='text/javascript' when importing javascript files

#### Note 2
One way of exporting code
```
function test() {
    // Do stuff
}
const Client = {test}
export default Client;
```



### React methods
```
getInitialState()
this.setState(attribute (can be an array) : some value (can come from a service))
 can then access using this.state.[attribute which can be an array as well]
render()
props can pass in functions too for example, onRowClick={(rowId) => // some code}
```
### Patterns

If components B and C updates a shared state, then A (which contains the shared state) is composed of B and C
```
A [shared state - pass state updater functions to the childs]
|\
B C
```


### Jest/Enzyme
API
```
wrapper.find
wrapper.containsAnyMatchingElements
    someinput = wrapper.find('input').first()
    input.simulate(eventname say 'click', )
access shallow wrapper's state 
    wrapper.state()
    wrapper.update() - invokes render() of the shallow component (in Jest/Enzyme setup setState does NOT rerender - that has to be forcefully invoked (note: input.simulate() internally invokes update()
html() as a debugging aid
afterEach() mockClear() to start with a new slate

```

