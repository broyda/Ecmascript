# Ecmascript

## Recipe 1

## You want to create a slice of an object which has unique keys but also arrays linked to those unique keys

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
    ids: [ 'Monday', 'Tuesday' ]    
  }),
  
  const getMeetings = (state) => {
    state.ids.map((id) => state.byId[id]);
  }
