# cacher

[![NPM Version][npm-image]][npm-url]
[![NPM Downloads][downloads-image]][downloads-url]

Middleware for intelligence cache system using memory, filesystem, redis or mongoDB with NodeJS Frameworks
- [express](http://expressjs.com/)

* [How to install](#how-to-install)
* [How to use](#how-to-use)
  * [Express Routes](#express-routes)
  * [Using secure server](#using-secure-server)
* [Configuration Options](#configuration-options)
* [License](#license)
* [Authors](#authors)

## How to install
using `npm`
```bash
npm i cacher
```
or using `yarn`
```bash
yarn add cacher
```

## How to use

Assuming that exists a *express route function* defined (example below)
### Express Routes

```js
//routes.js
//const usersRoutes = require('./users.routes');
export (app)=>{
    app.get('/test', (req, res)=>{
        res.json('test route is working!')
    })
    // app.use('/users/', usersRoutes)
}
```

Now you can use this *function* to handle your routes with `http2` protocol

### Using secure server
You need to pass the [secure options](https://nodejs.org/api/http2.html#http2_http2_createsecureserver_options_onrequesthandler)

```js
const http2 = require('express-h2')
const expressRoutes = require('./routes')
const fs = require('fs');

const secureOptions = {
  key: fs.readFileSync('server-key.pem'),
  cert: fs.readFileSync('server-cert.pem')
};

const server = http2.createSecureServer(secureOptions, expressRoutes)
server.listen(3443)
```
For more informations and `issues` you can see in the [oficial repository](https://github.com/ksoliddev/express-h2) or [read this article with example project](https://medium.com/@kissema1/the-easy-way-to-use-http2-protocol-with-express-framework-dfae4f8e9689?source=friends_link&sk=b6986b8dac15016b684b08b618567249)

## Configuration Options
```js
const options = {}
http2.createSecureServer(secureOptions, expressRoutes, options)
```

 - `cors` - by default allow all access using credentials, but you can set `cors` [configuration options](https://expressjs.com/en/resources/middleware/cors.html#configuration-options)

## License

[MIT License](http://www.opensource.org/licenses/mit-license.php)

## Authors

[Kissema Eduardo Rafael](https://github.com/kissema) ([kissema1@gmail.com](mailto:kissema1@gmail.com))

[downloads-image]: https://img.shields.io/npm/dm/express-h2.svg
[downloads-url]: https://npmjs.org/package/express-h2
[npm-image]: https://img.shields.io/npm/v/express-h2.svg
[npm-url]: https://npmjs.org/package/express-h2