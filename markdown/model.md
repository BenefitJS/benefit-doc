### model

* So we using yeoman to generate development structure, then how to write model.

### first step

* You should define the schema by Joi.

  * create props
  
  ```javascript
  const props = {
    id: Joi.number().integer().description('id'),
    phone: Joi.string().description('phone'),
    password: Joi.string().description('password')
  }
  ```
  
  * define schema
  ```javascript
  const schema = Joi.object().keys(props).description('user info')
  ```
  
* write swagger document

 * Parameter Description
 
  * path --> swagger path
  * method --> swagger path
  * tags --> swagger tags
  * summary --> swagger summary
  * query --> swagger query
  * requestBody --> swagger requestBody
  * params --> swagger params
  * output --> swagger output

 * list
 
 ```javascript
 index: {
   path: '/users',
   method: 'get',
   tags: ['users'],
   summary: 'get user list',
   query: _.pick(props, ['phone']),
   output: {
     200: Joi.object().keys({
       result: Joi.array().items(props).description('result')
     })
   }
 }
 ```
 
 * create
 
 ```javascript
 create: {
   path: '/users',
   method: 'post',
   tags: ['users'],
   summary: 'create user',
   requestBody: {
     body: _.pick(props, ['phone', 'password']),
     required: ['phone', 'password']
   },
   output: {
     200: Joi.object().keys(props).description('result')
   }
 }
 ```
 
 * show
 
 ```javascript
 show: {
   path: '/users/:id',
   method: 'get',
   tags: ['users'],
   summary: 'get user info',
   params: _.pick(props, ['id']),
   output: {
     200: Joi.object().keys(props).description('result')
   }
 }
 ```
 
 * update
 
 ```javascript
 update: {
   path: '/users/{id}',
   method: 'put',
   tags: ['users'],
   summary: 'update user',
   params: _.pick(props, ['id']),
   requestBody: {
     body: _.pick(props, ['phone'])
   },
   output: {
     200: Joi.array().items(Joi.number()).description('result')
   }
 }
 ```
