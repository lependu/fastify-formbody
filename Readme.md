# fastify-formbody

A simple plugin for [Fastify][fastify] that adds a content type parser for
the content type `application/x-www-form-urlencoded`.

[fastify]: https://www.fastify.io/

## Example

Given the following code:

```js
const fastify = require('fastify')()

fastify.register(require('fastify-formbody'))

fastify.post('/', (req, reply) => {
  reply.send(req.body)
})

fastify.listen(8000, (err) => {
  if (err) throw err
})
```

And a `POST` body of:

```html
foo=foo&bar=bar&answer=42
```

The sent reply would be the object:

```js
{
  foo: 'foo',
  bar: 'bar',
  answer: 42
}
```

## Options

The plugin accepts an options object with the following properties:

+ `bodyLimit` (Default: `1048576`): the maximum amount of bytes to process
before returning an error. If the limit is exceeded, a `500` error will be
returned immediately.

## License

[MIT License](http://jsumners.mit-license.org/)
