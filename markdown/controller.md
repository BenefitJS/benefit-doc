### controller

* For a simple write controller, I packaged the validate function in this BaseController. You should extends BaseController to use it.
  
  ```javascript
  class UserController extends BaseController {
    async index (ctx) {
      const { service } = ctx
      const params = ctx.query
      ctx.body = await service.user.index(params)
    }
    async create (ctx) {
      const { service, model } = ctx
      const params = ctx.request.body
      await super.validate(model.user.create, params)
      ctx.body = await service.user.create(params)
    }
    async show (ctx) {
      const { service } = ctx
      const params = ctx.params
      ctx.body = await service.user.show(params)
    }
    async update (ctx) {
      const { service } = ctx
      const params = Object.assign(ctx.params, ctx.request.body)
      ctx.body = await service.user.update(params)
    }
    async destroy (ctx) {
      const { service } = ctx
      const params = ctx.params
      ctx.body = await service.user.destroy(params)
    }
  }
  ```

* Encapsulate the service module and the model module into the context.

  ```javascript
  const { service, model } = ctx
  ```
