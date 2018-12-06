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
