# Express Javascript template for Cloud Sandbox

This is an [Express](https://expressjs.com/) javascript template, for quick development setup in Cloud Sandbox.

This template was bootstrapped using the [express generator](https://github.com/expressjs/generator).

## Specifications

The following `App configuration` was used to create this template:

```yaml
spec:
  endpoints:
  - http:
      routes:
      - backend:
          port: http
          target: js-express
        path_prefix: /
    name: app
  services:
  - description: A Javascript/Express template
    name: js-express
    workspace:
      checkouts:
      - path: template-javascript-expressjs
        repo:
          git: https://github.com/crafting-dev/template-javascript-expressjs.git
      packages:
      - name: nodejs
        version: ~16
      ports:
      - name: http
        port: 3000
        protocol: HTTP/TCP
```

The template was created with [pug](https://github.com/pugjs/pug) as its view template engine:

```bash
npx express --view=pug .
```

To install dependencies:

```
npm install
```

To start the server:

```
npm start
```