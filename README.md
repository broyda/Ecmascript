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
#### Reducer composition (reducer calling another reducer)
```
Root Reducer
  |
  |
  |
  SubtreeReducer1
  |
  |
  |
  SubtreeReducer2
        |
        |
        |
        SubSubtreeReducer3
               |
               |
               |
               SubSubSubtreeReducer4
```

#### Recipe 7
#### Chrome debugging
Features:
 - Source map based debugging of JSX/ES7
 - XHR breakpoints - conditional when url contains "weather"
 - Event Listener breakpoints
 - DOM breakpoint - subtree modifications

Outputs the ES5 code

#### Recipe 8
#### Reducers are called post createStore(...)

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

### You want to fire a function when setState() has been called.
Add an optional callback as second parameter
```
this.setState({done: true},
() => {
    console.log('do something below');
    // functionality
}
)
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

### ES6 notes
let {something} = this.state

is the same as explicitly declaring:

let something = this.state.something

Similarly:
var {x, y} = this.props;
is the same as:
var x = this.props.x;
var y = this.props.y;


```

### Redux notes
Create separate root keys within the store


### getDefaultProps
Object returned by getDefaultProps(...) shared across instances

### Context

In the parent where the context 'reside'
-----------------------------------------
childContextTypes()
getChildContext() - (called everytime state or prop change) - similar to getInitialState() 

In the child that 'consumes' the context
---------------------------------------
contextType: { // Define}
this.state.foo
this.props.foo
this.context.foo

###Common operations (using ES7 and lodash counterpart)
1. Add to the end of the list
```
a = [1,2,3] -> b = 4
a.concat(b)
```

2. Delete from the list
```
a = [1, 2, 3, 4, 5, 6]    X 4
x : [...a.slice(0, 2),
     ...a.slice(3, 5)
]
```

3. Find (list holds objects) - find(...) and findIndex(...)
```
persons.findIndex(
   (person) => person.empid === passinempid
);

persons.find(
   (person) => person.empid === passinempid
);
```
