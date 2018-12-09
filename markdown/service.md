### service

* In this module I encapsulate the context into the constructor, if you extends this service, you can using ctx to throw err and so on.

```javascript
const BaseService = require('../common/base_service')

class UserService extends BaseService {
  async index (params) {
    this.ctx.throw(400, 'Hello World')
    return 'Hello'
  }
}

module.exports = new UserService()
```
