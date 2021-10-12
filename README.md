# Javascript Express template for Cloud Sandbox

This is a Javascript [Express](https://expressjs.com/) template, configured for quick development setup in Cloud Sandbox.

## Specifications

The following `App configuration` was used to create this template:

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

To run and hot-reload for development:
```bash
npm start
```

To lint and fix files:
```bash
npm run lint
```