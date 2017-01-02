# Ecmascript

#### Recipe 1

#### You want to create a slice of an object which has unique keys but also arrays linked to those unique keys

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
    
#### Recipe 2

#### You want to abstract out object manipulation (merge, delete, join, slice, select) so in future you can plug in any new framework and replace the current one

See if you can create a helper and have object operations such as merge, delete, join, slice, select contained within there
  
