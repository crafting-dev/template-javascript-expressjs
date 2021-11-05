# Javascript/Express with MySQL template for Crafting Sandbox

This is a Javascript/[Express](https://expressjs.com/) with MySQL template, configured for quick development setup in [Crafting Sandbox](https://crafting.readme.io/docs).

## Specifications

This template defines a single `/ping` route:
```ts
app.get('/ping', (req, res) => {
  const pong = {
    ping: req.query.ping || 'To ping, or not to ping; that is the question.',
    received_at: new Date(),
  }

  res.json(pong)
})
```

This route receives a query string, and responds with the param string and the current time. For example:
```bash
$ curl --request GET 'localhost:3000/ping?ping=hello'
{"ping":"hello","received_at":"XXXX-XX-XXXXX:XX:XX.XXXX"}
```

Template is configured with MySQL, with the connection config available in [db.js](src/db.js):
```ts
const db = mysql.createConnection({
  host: process.env.MYSQL_SERVICE_HOST,
  user: 'brucewayne',
  password: 'batman',
  database: 'superhero',
})
```

PORT is set to `3000`:
```ts
const PORT = 3000
```

which is the same port value defined in App configuration below.

## App Configuration

The following [App configuration](https://crafting.readme.io/docs/app-spec) was used to create this template:

```yaml
endpoints:
- http:
  routes:
  - backend:
      port: http
      target: js-express
    path_prefix: /
name: app
services:
- description: Javascript/Express template
name: js-express
workspace:
  checkouts:
  - path: src/template-javascript-express
    repo:
      git: https://github.com/crafting-dev/template-javascript-expressjs.git
  packages:
  - name: nodejs
    version: ~16
  ports:
  - name: http
    port: 3000
    protocol: HTTP/TCP
- managed_service:
  properties:
    database: superhero
    password: batman
    username: brucewayne
  service_type: mysql
  version: "8"
name: mysql
```
