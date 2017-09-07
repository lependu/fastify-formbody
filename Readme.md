# fastify-formbody

A simple plugin for [Fastify][fastify] that adds a content type parser for
the content type `application/x-www-form-urlencoded`.

[fastify]: http://www.fastify.io/

## Example

Given the following code:

```
const fastify = require('fastify')()

fastify.register(require('fastify-formbody'), {}, (err) => {
  if (err) throw err
})

fastify.post('/', (req, reply) => {
  reply.send(req.body)
})

fastify.listen(8000, (err) => {
  if (err) throw err
})
```

And a `POST` body of:

```
foo=foo&bar=bar&answer=42
```

The sent reply would be the object:

```
{
  foo: 'foo',
  bar: 'bar',
  answer: 42
}
```

## License

[MIT License](http://jsumners.mit-license.org/)