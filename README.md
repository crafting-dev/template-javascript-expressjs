# Javascript/Express with MySQL template for Crafting Sandbox

This is a Javascript/[Express](https://expressjs.com/) with MySQL template, configured for quick development setup in [Crafting Sandbox](https://docs.sandboxes.cloud/docs).

## Specifications

This template defines a single `/ping` route:

```ts
app.get('/ping', (req, res) => {
  const pong = {
    ping: req.query.ping || 'To ping, or not to ping; that is the question.',
    received_at: new Date(),
  };

  res.json(pong);
});
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
});
```

PORT is set to `3000`:

```ts
const PORT = 3000;
```

which is the same port value defined in App configuration below.

## App Definition

The following [App Definition](https://docs.sandboxes.cloud/docs/app-definition) was used to create this template:

```yaml
endpoints:
- name: api
  http:
    routes:
    - pathPrefix: "/"
      backend:
        target: js-express
        port: api
    authProxy:
      disabled: true
workspaces:
- name: js-express
  description: Template backend using Js/Express
  ports:
  - name: api
    port: 3000
    protocol: HTTP/TCP
  checkouts:
  - path: backend
    repo:
      git: https://github.com/crafting-dev/template-javascript-expressjs
  packages:
  - name: nodejs
    version: 16.12.0
dependencies:
- name: mysql
  serviceType: mysql
  version: '8'
  properties:
    database: superhero
    password: batman
    username: brucewayne
```
