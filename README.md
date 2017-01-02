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
