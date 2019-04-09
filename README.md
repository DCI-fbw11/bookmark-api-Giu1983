# Bookmark Api

## Objectives

```js
//GET api/bookmarks
[
  {
    id: "<uuid>",
    url: 'https://twitter.com/iamdevloper/status/1112428799222788099',
    tag: ['humor', 'sad reality'],
    createdAt: "<Date>"
  },
  {
    ...
  }
]
```

- use lowDB
  - set some defaults
- implement as mentioned above api/bookmarks where `/api` is controlled by a middleware
- create directories for:
  - routes
  - controller
  - database (lowDB)

### Endpoints

> Read about [Route parameters](https://expressjs.com/en/guide/routing.html#route-parameters)

- GET
  - api/bookmarks
  - api/bookmarks/:id
- POST
  - api/bookmarks
- PUT
  - api/bookmarks/:id
- DELETE
  - api/bookmarks/:id


###Notes *Giuseppa: 
  
  How to do the exercise:
  
  Preamble: I'm not sure if this is the right procedure, but I was not present at the course for a few days because of the     landing festival and I'm trying to reconstruct the various topics. 
  
  The goal is to build a REST Api, so I think this is the model I have to consider to do the exercise: 
  
  
  const User = use('App/Models/User')
  const { validate } = use('Validator')

  async signup({request, response, auth}) {

  const validation = await validate(request.all(), {
  email: 'required |email:unique:users',
  username: 'required|unique:users',
      password: 'required'
    })
    if(validation.fails()) {
    return response.send(validation.messages())
    }

  const user = new User()
   user.email = request.input('email')
   user.username = request.input('username')
   user.password = request.input('password')

  await user.save()

  const token = await auth.generate(user)

  return response.json({
   message: 'Successfully', 
   data: token
   })
   }
   
  async signin({request, response, auth}) {
   try {
        const parameter = request.only(['enail', 'password'])
        
        if(!parameter) {
           return response.status(404).json({data: 'Resource non found'})
           }
        const token = await.auth.attempt(parameter.email, parameter.password)
        return response.json({
               token: token
           })
       } catch(err) {
       return response.status(400).json({
              status: 'error', 
              message: 'Problem occurred...'
        })
     })
     
     
     Contact Routes: 
     
     Route.group(() => {
       Route.get('contacts',  'ContactController.index')
       Route.get('contact/:id', 'ContactController.show')
       Route.post('contact', 'ContactController.store')
       Route.put('contacts/:id','ContactController.update')
       Route.delete('contacts/:id', 'ContactController.destroy')
       Route.patch('contacts/:id/star', 'ContactController.startContact')
       Route.get('starred/contacts', 'ContactController.starredContacts')
       }).prefix('api/v1'). middleware(['auth'])
     
     
     
     It's this the right model? 
     
  
  
